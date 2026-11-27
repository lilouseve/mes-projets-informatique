# Projet 4 — Migration d'un serveur physique vers une VM (P2V)


## 1. Objectif

Migrer un serveur physique (simulé : SRV-PHYS) qui héberge un site web IIS vers une machine virtuelle Windows 11, comparer le fonctionnement avant et après, puis rédiger un rapport de migration avec les risques identifiés.

## 2. Étape 1 : identifier le rôle et la configuration du serveur

![Capture d'écran 2026-10-08 123509](https://hackmd.io/_uploads/SkzPBxrjGe.png)
![Capture d'écran 2026-10-08 123613](https://hackmd.io/_uploads/ryuPrxHjGg.png)
![Capture d'écran 2026-10-08 123721](https://hackmd.io/_uploads/Byb_HgBjzl.png)

## 3. Étape 2 : reconstruire un équivalent en VM

![Capture d'écran 2026-10-08 125351](https://hackmd.io/_uploads/H1zevgSiGe.png)
![Capture d'écran 2026-10-08 125411](https://hackmd.io/_uploads/H1XgveSjMl.png)
![Capture d'écran 2026-10-08 125425](https://hackmd.io/_uploads/Hk7lPlHsGg.png)
![Capture d'écran 2026-10-08 125516](https://hackmd.io/_uploads/B1JbweHoMl.png)
![Capture d'écran 2026-10-08 125527](https://hackmd.io/_uploads/r1JZvxSsMe.png)
![Capture d'écran 2026-10-08 125559](https://hackmd.io/_uploads/r1x-wgSiMl.png)
![Capture d'écran 2026-10-08 125603](https://hackmd.io/_uploads/SyxWPxHiMe.png)
![Capture d'écran 2026-10-08 125610](https://hackmd.io/_uploads/rklZvlSozg.png)

## 4. Étape 3 : réaliser la migration

![Capture d'écran 2026-10-08 150427](https://hackmd.io/_uploads/BkDerMHiMx.png)
![Capture d'écran 2026-10-08 150631](https://hackmd.io/_uploads/SyjPHMHifl.png)
![Capture d'écran 2026-10-08 151317](https://hackmd.io/_uploads/HkTpNfUifl.png)
![Capture d'écran 2026-10-09 091113](https://hackmd.io/_uploads/Sy954MUjzg.png)
![Capture d'écran 2026-10-09 091504](https://hackmd.io/_uploads/SkMiNfUofe.png)

## 5. Comparaison avant / après migration

### 5.1 Avant migration (SRV-PHYS)

- Le serveur hébergeait un site web local.
- Le rôle IIS était installé et le service `W3SVC` était en cours d'exécution.
- Le fonctionnement dépendait du matériel du serveur (disque, réseau, pilotes).
- Le site était accessible uniquement depuis la machine locale.

### 5.2 Après migration (VM Windows 11)

- Le rôle IIS a été réinstallé proprement dans la VM.
- Le dossier `C:\inetpub\wwwroot` est fonctionnel.
- Le site a été déployé dans la VM et est accessible via `http://localhost`.
- Le comportement est identique : les pages HTML s'affichent correctement.

### 5.3 Tableau comparatif

| Critère | Avant (SRV-PHYS) | Après (VM) | Résultat |
|---|---|---|---|
| Rôle IIS / service `W3SVC` | Installé, `Running` | Installé, `Running` | Identique |
| Pages et fichiers de `wwwroot` | Présents | Présents | Identique |
| Fonctionnement du site | Page affichée | Page affichée | Identique |
| Accessibilité | `localhost` uniquement | `localhost` uniquement | Identique |
| Performances | Non mesurées | Non mesurées | Dépendent des ressources attribuées à la VM |
| Stabilité | Dépend du matériel | Environnement propre et contrôlé | Meilleure dans la VM |

## 6. Problèmes possibles

### 6.1 Pilotes, licences et performances

| Domaine | Constat | Impact |
|---|---|---|
| **Pilotes** | Aucun pilote matériel nécessaire pour IIS. La VM utilise des pilotes virtuels standards. | Aucun conflit |
| **Licences** | La VM utilise une licence Windows 11. IIS est inclus gratuitement dans Windows. | Pas de problème de licence |
| **Performances** | La VM peut être moins performante si la RAM, le CPU ou le stockage sont limités. Le site est statique (HTML/CSS). | Le site reste fonctionnel |

### 6.2 Autres problèmes potentiels

- Mauvaise copie des fichiers dans `wwwroot`.
- IIS non installé ou mal configuré.

### 6.3 Problèmes propres à une migration P2V

- **Nom et adresse IP identiques** : la VM migrée copie ceux du serveur d'origine. Si les deux tournent en même temps sur le même réseau, il y a un conflit.
- **Activation de Windows** : un changement de matériel (réel vers virtuel) peut demander de réactiver la licence.
- **TPM et Secure Boot (Windows 11)** : le TPM virtuel et le démarrage sécurisé doivent être configurés dans la VM.
- **Pilotes de l'ancien matériel** : ils peuvent rester dans le système copié sans être utilisés.
- **VMware Tools** : à installer dans la VM pour les pilotes virtuels et l'intégration.

## 7. Rapport de migration

### 7.1 Résumé

- Le serveur physique n'a pas été migré directement (pas de P2V avec un outil).
- Une reconstruction du serveur IIS a été réalisée dans une VM Windows 11.
- Le site web a été redéployé dans `C:\inetpub\wwwroot`.
- Le fonctionnement a été validé via `http://localhost`.

### 7.2 Risques identifiés

| Risque | Cause | Mesure de prévention |
|---|---|---|
| Perte de données | Fichiers du site mal copiés | Vérifier la liste des fichiers avant et après |
| Différences de configuration | Réglages du serveur d'origine non reproduits | Relever la configuration avant (`systeminfo`, `ipconfig /all`) |
| Performances réduites | RAM, CPU ou stockage insuffisants dans la VM | Dimensionner la VM selon le serveur d'origine |
| Erreurs IIS | Rôle non installé ou non démarré | Contrôler `Get-Service W3SVC` après la migration |
| Conflit de nom ou d'IP | Deux machines identiques sur le même réseau | Isoler ou renommer la VM avant de la démarrer |

## 8. Conclusion

La reconstruction du serveur IIS dans la VM est réussie : le site fonctionne de façon identique à l'original, les différences possibles de performances et de stabilité sont documentées, et les risques sont identifiés avec une mesure de prévention pour chacun.
