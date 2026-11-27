# Projet 2 — Snapshots et plan de reprise d'une VM critique

1. Créer une VM de test avec une application simple installée.
![Capture d'écran 2026-10-07 083830](https://hackmd.io/_uploads/Hk9EZu7sMx.png)
![Capture d'écran 2026-10-07 084031](https://hackmd.io/_uploads/SJQIW_XjMx.png)
![Capture d'écran 2026-10-07 084145](https://hackmd.io/_uploads/Sk1P-_Xofx.png)
![Capture d'écran 2026-10-07 084506](https://hackmd.io/_uploads/Sy9v-_moMx.png)
![Capture d'écran 2026-10-07 085416](https://hackmd.io/_uploads/H1PAbumszx.png)
2. Prendre un snapshot avant une modification volontaire (ex. installation d'une mise à jour).
![Capture d'écran 2026-10-07 085606](https://hackmd.io/_uploads/BJYgfOmofl.png)
![Capture d'écran 2026-10-07 085658](https://hackmd.io/_uploads/HyfZG_QiGx.png)
![Capture d'écran 2026-10-07 085708](https://hackmd.io/_uploads/BJc-zdXsfl.png)
![Capture d'écran 2026-10-07 085821](https://hackmd.io/_uploads/H1bffdXiMl.png)
![Capture d'écran 2026-10-07 090136](https://hackmd.io/_uploads/By-1SO7oGg.png)

![Capture d'écran 2026-10-07 090014](https://hackmd.io/_uploads/Sy6Mz_7ofx.png)
3. Simuler un incident (suppression de fichier, panne applicative).
![Capture d'écran 2026-10-07 090504](https://hackmd.io/_uploads/SyIYfumozl.png)
![Capture d'écran 2026-10-07 090511](https://hackmd.io/_uploads/SyiJXu7ofg.png)
4. Restaurer la VM à partir du snapshot.
![Capture d'écran 2026-10-07 090558](https://hackmd.io/_uploads/SkYxQ_QiMg.png)
![Capture d'écran 2026-10-07 090602](https://hackmd.io/_uploads/SJzZQumizl.png)
![Capture d'écran 2026-10-07 090743](https://hackmd.io/_uploads/SyAW7d7jMl.png)
![Capture d'écran 2026-10-07 090809](https://hackmd.io/_uploads/r18MXdQiMx.png)


5. Mesure du temps de restauration

> ℹ️ Environnement : VM Windows 11 sous VMware Workstation, serveur web IIS.
> Snapshot utilisé : `Avant_MAJ_01`

### Méthode

1. Incident simulé : suppression de `index.html` et `donnees.txt`, arrêt du service `W3SVC`.
2. Lancement de la restauration : **VM → Snapshot → Snapshot Manager → Go To**.
3. Fin de la mesure : le site `http://127.0.0.1` affiche de nouveau « Application de test - version 1 ».

### Résultat

| Élément | Valeur |
|---|---|
| Snapshot restauré | `Avant_MAJ_01` |
| Temps de restauration estimé | environ 1 minute |
| Service W3SVC après restauration | `Running` |
| Fichiers `index.html` et `donnees.txt` | restaurés |


### Preuves

- Capture : Snapshot Manager avec `Avant_MAJ_01`
- Capture : site en « version 2 » avant l'incident
- Capture : site inaccessible après l'incident
- Capture : site en « version 1 » après restauration
- Capture : `Get-Service W3SVC` et `dir C:\inetpub\wwwroot`

6. Plan de reprise (RTO / RPO)

6.1 Objectif et périmètre

Restaurer rapidement un serveur web IIS virtualisé (VM Windows 11, VMware Workstation) après une mauvaise mise à jour, une suppression de fichiers ou une panne du service web.

### 6.2 Objectifs de reprise

| Indicateur | Valeur | Explication |
|---|---|---|
| **RPO** | 24 h (0 pour un changement planifié) | Snapshot quotidien + snapshot avant chaque modification |
| **RTO visé** | 15 minutes | Arrêt maximal acceptable |
| **RTO mesuré** | environ 1 minute (estimé) | Du lancement du « Go To » au site de nouveau accessible |

Le RTO mesuré est inférieur au RTO visé : l'objectif est atteint.

### 6.3 Politique de snapshots

| Moment | Fréquence | Rétention |
|---|---|---|
| Avant toute mise à jour ou modification | À chaque changement | 3 à 7 jours |
| Snapshot de routine | Quotidien | 3 derniers |

Nommage : `Avant_MAJ_01`, `Quotidien_AAAA-MM-JJ`.

### 6.4 Procédure de restauration

1. Constater l'incident (site inaccessible, fichiers manquants, service arrêté).
2. Ouvrir **VM → Snapshot → Snapshot Manager**.
3. Sélectionner le dernier snapshot sain et cliquer sur **Go To**.
4. Redémarrer la VM si nécessaire.
5. Effectuer les vérifications (6.5).
6. Consigner l'incident et la durée de la restauration.

### 6.5 Vérifications après restauration

- [ ] `Get-Service W3SVC` retourne `Running`
- [ ] `http://127.0.0.1` affiche « Application de test - version 1 »
- [ ] `index.html` et `donnees.txt` présents dans `C:\inetpub\wwwroot`

### 6.6 Limites et améliorations

- Un snapshot n'est **pas une sauvegarde** : il dépend du disque d'origine.
- Trop de snapshots ralentissent la VM et consomment de l'espace disque.
- La restauration annule les données créées après le snapshot (d'où le RPO).
- Amélioration : sauvegarde externe régulière de la VM ou des données.

### 6.7 Responsabilités

L'administrateur système prend les snapshots, gère la rétention et exécute la restauration en cas d'incident.





