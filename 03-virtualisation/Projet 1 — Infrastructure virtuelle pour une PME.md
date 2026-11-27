# Projet 1 — Infrastructure virtuelle pour une PME


## 1. Objectif

Mettre en place trois postes virtuels pour une PME avec VMware Workstation (réseau NAT VMnet8) : installation des systèmes, comptes administrateur et utilisateur, réseau en IP fixe, nom de machine, groupe de travail, imprimante, logiciel métier, mises à jour, antivirus et pare-feu.

## 2. Étape 1 : installer les machines virtuelles

### 2.1 VM Windows 11

![Capture d'écran 2026-09-09 210551](https://hackmd.io/_uploads/SJbO0Q1tzx.png)
![Capture d'écran 2026-09-09 210910](https://hackmd.io/_uploads/rJqWJE1KGg.png)
![Capture d'écran 2026-09-09 193330](https://hackmd.io/_uploads/HkzD1keKMg.png)
![Capture d'écran 2026-09-09 202403](https://hackmd.io/_uploads/BJ0CwE1tGe.png)
![Capture d'écran 2026-09-09 202606](https://hackmd.io/_uploads/H1TvKV1KMe.png)
![Capture d'écran 2026-09-10 094437](https://hackmd.io/_uploads/ry6gx1xYzg.png)

### 2.2 VM Ubuntu

![image](https://hackmd.io/_uploads/By1nbVyKGg.png)
![image](https://hackmd.io/_uploads/BJxUfVytfe.png)
![image](https://hackmd.io/_uploads/H1mqfVkFfg.png)
![Capture d'écran 2026-09-09 193622](https://hackmd.io/_uploads/H18aMVkKfe.png)
![Capture d'écran 2026-09-09 193901](https://hackmd.io/_uploads/r11eQEkKfl.png)

## 3. Étape 2 : créer les comptes administrateur et utilisateur

Sur chaque poste, je crée un compte `admin` (administrateur) et un compte `utilisateur` (standard).

![Capture d'écran 2026-10-06 143811](https://hackmd.io/_uploads/H1x6w5zoMx.png)
![Capture d'écran 2026-10-06 143826](https://hackmd.io/_uploads/ByipD9fszl.png)
![image](https://hackmd.io/_uploads/ByOSK5fifg.png)

## 4. Étape 3 : configurer le réseau

### 4.1 Adresse IP fixe et ping

![Capture d'écran 2026-10-06 172551](https://hackmd.io/_uploads/rkA5KczsMe.png)
![Capture d'écran 2026-10-06 174357](https://hackmd.io/_uploads/HkVoFcfifx.png)
![Capture d'écran 2026-10-06 175748](https://hackmd.io/_uploads/BkOqqqfjMx.png)

### 4.2 Nom de machine

![Capture d'écran 2026-10-06 180346](https://hackmd.io/_uploads/HyIUhqMoGx.png)
![Capture d'écran 2026-10-06 175918](https://hackmd.io/_uploads/Hy3In5zoGl.png)
![Capture d'écran 2026-10-06 180041](https://hackmd.io/_uploads/rJfw35MjMg.png)

### 4.3 Groupe de travail et test d'impression

![Capture d'écran 2026-10-06 181648](https://hackmd.io/_uploads/H1vsJhGsGx.png)
![Capture d'écran 2026-10-06 192656](https://hackmd.io/_uploads/SJWnknGoGl.png)

## 5. Étape 4 : installer le logiciel métier

![Capture d'écran 2026-10-06 193503](https://hackmd.io/_uploads/H1vPEnzizl.png)
![Capture d'écran 2026-10-06 194338](https://hackmd.io/_uploads/ry2DE2MsMx.png)
![Capture d'écran 2026-10-06 194658](https://hackmd.io/_uploads/SkIOE3foMe.png)

## 6. Étape 5 : mises à jour, antivirus et pare-feu

### 6.1 Mises à jour

![Capture d'écran 2026-10-06 205921](https://hackmd.io/_uploads/S1kAH6zsGl.png)
![Capture d'écran 2026-10-06 210202](https://hackmd.io/_uploads/H18RrafoGe.png)
![Capture d'écran 2026-10-06 211711](https://hackmd.io/_uploads/Bku_t6ziGg.png)

### 6.2 Antivirus et pare-feu

![Capture d'écran 2026-10-06 212021](https://hackmd.io/_uploads/rJ-Oq6Mjfl.png)
![Capture d'écran 2026-10-06 212116](https://hackmd.io/_uploads/SyYu9pMsMl.png)
![Capture d'écran 2026-10-06 212804](https://hackmd.io/_uploads/S1HzC6Gszl.png)

## 7. Fiche de mise en service

**Date :** 06/10/2026 | **Projet :** infrastructure virtuelle pour une PME (VM VMware Workstation, réseau NAT VMnet8)

| | **PcCompta01** | **PcCompta02** | **PcCompta03** |
|---|---|---|---|
| Système d'exploitation | Windows 11 | Ubuntu | Windows 11 |
| Groupe de travail | WORKSPACE | WORKSPACE | WORKSPACE |
| Adresse IP (fixe) | 192.168.150.50 | 192.168.150.51 | 192.168.150.52 |
| Masque | 255.255.255.0 | 255.255.255.0 | 255.255.255.0 |
| Passerelle | 192.168.150.2 | 192.168.150.2 | 192.168.150.2 |
| DNS | 192.168.150.2 et 8.8.8.8 | idem | idem |
| Compte administrateur | admin | admin | admin |
| Compte utilisateur standard | utilisateur | utilisateur | utilisateur |
| Logiciel métier | Mobi Office | Office365WebDesktop | Mobi Office |
| Imprimante réseau | Generic Text Only | Generic Text Only | Generic Text Only |
| Mises à jour | Vérifiées et activées | Vérifiées et activées | Vérifiées et activées |
| Antivirus | Actif | Actif | Actif |
| Pare-feu | Activé | Activé | Activé |

## 8. Test et résultat

Les 3 postes sont dans le même sous-réseau `192.168.150.0/24` et se joignent entre eux par ping.

| Vérification | Résultat |
|---|---|
| Ping entre les 3 postes | ✅ |
| Comptes admin et utilisateur | ✅ Créés sur les 3 postes |
| Logiciel métier et imprimante | ✅ Installés |
| Mises à jour, antivirus, pare-feu | ✅ Vérifiés et activés |

## 9. Difficultés rencontrées

| Problème | Solution |
|---|---|
| La passerelle ne répondait pas avec l'ancienne IP | J'ai relevé le vrai sous-réseau de VMnet8 et reconfiguré l'IP fixe |
| Carte réseau déconnectée | J'ai coché *Connected* dans VMware |
| Mode Bridged inutilisable sur le Wi-Fi de l'école | Passage en NAT |
| Ping bloqué entre les VM Windows | Règle ICMPv4 ajoutée au pare-feu |

## 10. Conclusion

Les postes sont opérationnels : système, comptes, réseau, logiciel métier, imprimante et sécurité de base sont en place.
