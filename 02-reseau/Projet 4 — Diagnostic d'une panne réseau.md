# Projet 4 — Diagnostic d'une panne réseau

1. Configuration du routeur 
![Capture d'écran 2026-10-16 084326](https://hackmd.io/_uploads/SkUnPBJhMx.png)
![Capture d'écran 2026-10-16 084334](https://hackmd.io/_uploads/Bksnvrk2zx.png)

2. Configuration des PC 
![Capture d'écran 2026-10-16 084517](https://hackmd.io/_uploads/rk67FSy3ze.png)
![Capture d'écran 2026-10-16 084719](https://hackmd.io/_uploads/SkMVtr12Ge.png)

3. Test de ping 
![Capture d'écran 2026-10-16 085117](https://hackmd.io/_uploads/rkUFFSJ2Ge.png)

4. Provocation de la Panne Routeur 
![Capture d'écran 2026-10-16 090150](https://hackmd.io/_uploads/Hy2v2Bynzx.png)
![Capture d'écran 2026-10-16 090348](https://hackmd.io/_uploads/Bk2vnrJhGe.png)

5. Diagnostique de la panne 
![Capture d'écran 2026-10-16 090410](https://hackmd.io/_uploads/r1xchBknfl.png)
![image](https://hackmd.io/_uploads/Hy723ry3zl.png)
5.1 Problème identifié 
![image](https://hackmd.io/_uploads/rJkmArk3Mx.png)

6. Résolution de la panne 
![image](https://hackmd.io/_uploads/HkcK0Hy3fx.png)
![image](https://hackmd.io/_uploads/rkjcRH1hfx.png)
![image](https://hackmd.io/_uploads/rJox1Ik3zg.png)

# Rapport d'intervention : panne réseau

###### tags: `E1A` `Networking Essentials` `Projet 4` `GNS3` `Diagnostic`

## 1. Identification de l'incident

### 1.1 Signalement

L'utilisateur du poste **PC1** signale qu'il n'accède plus au réseau.

### 1.2 Équipements concernés

PC1, PC2, switch, routeur R1.

### 1.3 Schéma du réseau

![image](https://hackmd.io/_uploads/rk0lbUkhMe.png)


> 📸 Capture : topologie GNS3 avec noms et interfaces visibles.

### 1.4 Plan d'adressage1

| Équipement | Interface | Adresse IP | Masque | Passerelle |
|---|---|---|---|---|
| R1 | g0/0 | 192.168.10.1 | 255.255.255.0 | n/a |
| PC1 | eth0 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC2 | eth0 | 192.168.10.20 | 255.255.255.0 | 192.168.10.1 |

---

## 2. Symptôme constaté

Depuis PC1, le ping vers la passerelle échoue.

---

## 3. Démarche de diagnostic (modèle OSI)

Le diagnostic est mené **de bas en haut** : on s'arrête à la première couche défaillante.

### 3.1 Couche 1 : Physique

Vérification de la topologie GNS3 : tous les liens sont actifs.


**Conclusion :** ✅ couche physique OK.

### 3.2 Couche 3 : Configuration IP du poste

```
PC1> show ip
```


Adresse, masque et passerelle de PC1 sont corrects.

**Conclusion :** ✅ configuration du poste OK.

### 3.3 Couche 3 : Tests de connectivité

```
PC1> ping 127.0.0.1
PC1> ping 192.168.10.20
PC1> ping 192.168.10.1
```


| Test | Résultat | Interprétation |
|---|---|---|
| `ping 127.0.0.1` | ✅ Réussi | Pile TCP/IP fonctionnelle |
| `ping 192.168.10.20` (PC2) | ✅ Réussi | Couches 1-2 saines, réseau local OK |
| `ping 192.168.10.1` (passerelle) | ❌ Échec | Problème côté routeur |

**Conclusion :** le réseau local fonctionne, seule la passerelle est injoignable. Le routeur est suspecté.

### 3.4 Inspection du routeur R1

```
R1# show ip interface brief
R1# show running-config interface g0/0
```




L'interface `g0/0` est `up/up` mais son adresse est **192.168.10.2** au lieu de **192.168.10.1**.

**Conclusion :** ❌ cause identifiée.

### 3.5 Synthèse du diagnostic

| Couche | Test | Résultat | Conclusion |
|---|---|---|---|
| 1 : Physique | Topologie GNS3 | Liens actifs | ✅ OK |
| 3 : IP (poste) | `show ip` PC1 | IP, masque, passerelle corrects | ✅ OK |
| 3 : IP (local) | `ping` PC2 | Réussi | ✅ OK |
| 3 : IP (passerelle) | `ping` 192.168.10.1 | Échec | ❌ Panne |
| 3 : IP (routeur) | `show ip interface brief` | g0/0 = 192.168.10.2 | ❌ **Cause** |

---

## 4. Cause racine

> ❗ L'interface `g0/0` de **R1** est configurée en `192.168.10.2` au lieu de `192.168.10.1`.

Les postes ont pour passerelle `192.168.10.1`, qui n'existe plus sur le réseau. Il s'agit d'une erreur de configuration en **couche 3**, sans défaut physique ni problème de liaison.

---

## 5. Résolution

Commandes appliquées sur R1 :

```
R1# configure terminal
R1(config)# interface g0/0
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# end
R1# write memory
```

---

## 6. Vérification après correction

```
R1# show ip interface brief
PC1> ping 192.168.10.1
PC1> ping 192.168.10.20
PC1> trace 192.168.10.1
```

| Test | Résultat |
|---|---|
| `show ip interface brief` (R1) | ✅ g0/0 = 192.168.10.1, up/up |
| `ping 192.168.10.1` depuis PC1 | ✅ Réussi |
| `ping 192.168.10.20` depuis PC1 | ✅ Réussi |
| `trace 192.168.10.1` depuis PC1 | ✅ Réussi |

> ✅ Le réseau est rétabli et fonctionnel.

---

## 7. Recommandations

- Documenter le plan d'adressage et le tenir à jour.
- Sauvegarder les configurations (`write memory`) et en conserver une copie.
- Ajouter une description sur chaque interface (`description LAN-Bureau`).
- Mettre en place une supervision pour détecter rapidement une passerelle injoignable.
- Tester la connectivité après toute modification de configuration.

---

## 8. Conclusion

La panne provenait d'une mauvaise adresse IP sur l'interface LAN du routeur. Grâce à un diagnostic en couches (modèle OSI), les couches 1 et 2 ont été écartées rapidement, puis la cause a été isolée en couche 3 et corrigée. Le réseau est de nouveau opérationnel.
