# Projet 3 — Migration et sauvegarde d'un poste existant


## 1. Objectif

Un poste de travail vieillissant (système lent, obsolète) doit être réinstallé complètement, tout en récupérant les documents, les favoris et les paramètres essentiels de l'utilisateur. La migration est faite sans perte de données, avec une clé USB comme support de sauvegarde et une machine virtuelle (VMware Workstation, Windows 11) comme environnement de test.

## 2. Étape 1 : inventaire des données à conserver

Pour le test, je crée des documents factices et j'ajoute des pages en favoris dans le navigateur.

![image](https://hackmd.io/_uploads/rJ8ZXaPYGg.png)
![Capture d'écran 2026-09-16 092102](https://hackmd.io/_uploads/BkcxN6DKMl.png)
![Capture d'écran 2026-09-16 092146](https://hackmd.io/_uploads/BygbVpPYfe.png)

| Élément | Détail |
|---|---|
| Documents utilisateur | `doc test 1`, `doc test 2`, `doc test 3` dans le dossier `Documents` |
| Favoris du navigateur | Favoris de Microsoft Edge, exportés dans `favorites_navigateur.html` |
| Logiciels installés | Microsoft Edge (préinstallé) |
| Configuration réseau | DHCP standard, sans IP fixe ni paramètre particulier |

## 3. Étape 2 : sauvegarde sur la clé USB

Je connecte la clé USB à la VM avec `VM > Removable Devices > [clé USB] > Connect`.

J'exporte les favoris vers la clé USB.

![image](https://hackmd.io/_uploads/r1FoBTPYfg.png)

Pour les documents, je fais un copier-coller (`Ctrl + C` / `Ctrl + V`) vers la clé USB (lecteur `E:`).

![Capture d'écran 2026-09-16 093226](https://hackmd.io/_uploads/SkbHLaPFMe.png)
![image](https://hackmd.io/_uploads/HJmSLpwYMl.png)

## 4. Étape 3 : vérification de la sauvegarde

Je vérifie que tous les fichiers sont bien sur la clé.

![Capture d'écran 2026-09-16 093616](https://hackmd.io/_uploads/rk_VwTwFfg.png)
![Capture d'écran 2026-09-16 093606](https://hackmd.io/_uploads/rySIw6DFGl.png)

| Emplacement | Nombre de fichiers |
|---|---|
| `C:\Users\...\Documents` | 4 fichiers |
| Clé USB (`E:`) | 4 éléments (3 documents de test + 1 fichier de favoris) |

Les deux résultats correspondent : la sauvegarde est complète avant la réinstallation.

> Remarque : l'espace « utilisé » sur la clé USB (40 Ko) est plus grand que la taille réelle des fichiers (402 octets). C'est normal : le système de fichiers FAT32 réserve l'espace par blocs fixes (clusters), donc même un tout petit fichier occupe un bloc entier. Ce n'est pas une erreur de copie.

## 5. Étape 4 : réinstallation propre du système

### 5.1 Démarrage sur l'image d'installation

Par précaution, je déconnecte la clé USB de la VM avant le formatage (`VM > Removable Devices > [clé USB] > Disconnect`).

![Capture d'écran 2026-09-16 093920](https://hackmd.io/_uploads/SJkjNRwYMl.png)

Je clique sur « Restart Guest ».

![Capture d'écran 2026-09-16 094056](https://hackmd.io/_uploads/BkCZHADtGl.png)

Pendant le redémarrage, dans le Boot Manager, je choisis « EFI VMware Virtual SATA CDROM Drive (1.0) ».

![Capture d'écran 2026-09-16 094337](https://hackmd.io/_uploads/Hy2KQAwtfx.png)

L'installateur de Windows 11 se lance : je choisis la langue (français), puis « Personnalisée : installer uniquement Windows (avancé) ».

![Capture d'écran 2026-09-16 103922](https://hackmd.io/_uploads/BkxKOBuKMe.png)

### 5.2 Suppression des partitions

Je supprime les 4 partitions existantes (Système, MSR réservé, Principale, Récupération) pour ne garder qu'un espace non alloué de 64 Go sur le disque 0.

![Capture d'écran 2026-09-16 104114](https://hackmd.io/_uploads/rJl3uBdFfg.png)
![Capture d'écran 2026-09-16 104232](https://hackmd.io/_uploads/S1EyKBuYMe.png)

### 5.3 Installation de Windows

Je sélectionne l'espace non alloué et je lance l'installation. Windows recrée automatiquement les partitions nécessaires et copie les fichiers, avec plusieurs redémarrages. Je termine par la configuration initiale (région, clavier, compte utilisateur local).

![Capture d'écran 2026-09-16 104455](https://hackmd.io/_uploads/H1MzFHdFMg.png)

## 6. Étape 5 : réinstallation des logiciels

Le seul logiciel de l'inventaire, Microsoft Edge, est réinstallé par défaut avec le système. Aucune autre installation n'a été nécessaire pour ce test.

## 7. Étape 6 : restauration des données

### 7.1 Documents

Je reconnecte la clé USB à la VM, puis je copie les fichiers dans le dossier `Documents` du nouveau système.

![Capture d'écran 2026-09-16 132223](https://hackmd.io/_uploads/H1P7YB_Yfl.png)
![Capture d'écran 2026-09-16 132446](https://hackmd.io/_uploads/ByWdtBdKfl.png)
![Capture d'écran 2026-09-16 132454](https://hackmd.io/_uploads/ryiuKr_Yzl.png)

### 7.2 Favoris

Dans Edge, je vais dans `Menu > Favoris > Gestionnaire de favoris > Importer des favoris`.

![Capture d'écran 2026-09-16 132515](https://hackmd.io/_uploads/HJboYHdYMe.png)
![Capture d'écran 2026-09-16 132541](https://hackmd.io/_uploads/SJ4aYB_Kze.png)

Je sélectionne le fichier `favorites_navigateur.html`.

![Capture d'écran 2026-09-16 132615](https://hackmd.io/_uploads/S1NRKrdFfx.png)
![Capture d'écran 2026-09-16 132623](https://hackmd.io/_uploads/rJ5J5SOKGe.png)

## 8. Étape 7 : reconfiguration des paramètres essentiels

Le poste de test n'avait ni configuration réseau particulière (IP fixe, DNS personnalisé), ni imprimante partagée, ni plusieurs comptes utilisateurs. La configuration réseau par défaut (DHCP) fonctionnait donc sans intervention.

Sur un vrai poste de production, cette étape consisterait à :

- reconfigurer l'adresse IP, le masque, la passerelle et les DNS si une configuration statique était utilisée (`Paramètres > Réseau et Internet > Propriétés de la connexion > Modifier les paramètres IP`) ;
- réinstaller le pilote et reconnecter les imprimantes partagées ;
- recréer les comptes utilisateurs avec les bonnes permissions si le poste était partagé.

## 9. Test et résultat

Les favoris sont bien réapparus dans le nouveau navigateur.

![Capture d'écran 2026-09-16 132648](https://hackmd.io/_uploads/rkRb5Hdtfx.png)

| Vérification | Résultat |
|---|---|
| Sauvegarde complète avant formatage | ✅ 4 éléments sur la clé, comme sur le disque |
| Windows 11 réinstallé proprement | ✅ |
| Documents restaurés | ✅ Même nombre de fichiers qu'à l'origine |
| Favoris restaurés | ✅ Visibles dans Edge |

## 10. Difficultés rencontrées

- Lors du premier enregistrement, j'ai confondu le lecteur `D:` avec la clé USB. C'était en fait le lecteur DVD avec l'image d'installation de Windows (lecture seule). La clé n'était pas encore connectée à la VM : par défaut, elle reste rattachée à la machine hôte et doit être reliée avec le menu Removable Devices.

**Points de vigilance à retenir :**

- Bien identifier le support de sauvegarde avant d'y écrire.
- Connecter explicitement les périphériques USB à la VM avant de les utiliser.
- Ne jamais formater avant d'avoir vérifié la sauvegarde (nombre et taille des fichiers).
- Déconnecter le support de sauvegarde avant le formatage.
- Vérifier attentivement la partition à supprimer pour ne pas toucher au mauvais disque.

## 11. Conclusion

La migration du poste a été réalisée avec succès, sans perte de données, grâce à une double vérification (avant le formatage et après la restauration). Cette procédure, décrite étape par étape, est reproductible pour tout poste similaire qui doit être réinstallé complètement.
