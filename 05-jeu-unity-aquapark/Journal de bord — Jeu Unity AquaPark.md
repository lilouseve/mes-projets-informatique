# Journal de bord — Jeu Unity AquaPark

Projet : jeu de course sur toboggan aquatique (Unity / C#), réalisé en groupe.
Mon rôle (Personne 5) : caméra, règles du jeu (chute, victoire, défaite) et intégration du travail du groupe.
Date : 24/11/2026

## 1. Objectif

Je fais le lien entre tout le monde : j'ai créé le projet commun, je code la caméra et les règles de la course, je vérifie les Pull Requests des autres et j'assemble tout dans la scène Level01.

| Ce que j'ai fait | Avec quoi |
|---|---|
| Création du projet Unity commun | Unity 6 (6000.6.10f1), modèle Universal 3D (URP) |
| Mise en ligne du projet pour le groupe | Git + GitHub (dépôt `AquaPark-unity` créé par Deaa) |
| Caméra qui suit le joueur | Script C# `CameraFollow` |
| Chutes et réapparition au checkpoint | Script C# `RespawnManager` |
| Ligne d'arrivée, score, temps limite | Script C# `FinishLine` |
| Tests sans attendre les autres | Scènes `Test_Camera` et `Test_Rules` + faux joueur |
| Suivi du groupe | Tableau Excel `SUIVI_PROJET.xlsx` |
| Vérification et fusion des Pull Requests | GitHub + tests dans Unity |

## 2. Étape 1 : Mise en place du projet (Phase 1)

### 2.1 Création du projet

- Projet Unity créé avec le modèle Universal 3D (URP).
- Dossiers rangés comme dans le cahier des charges (`Assets/_Project/Scripts`, `Prefabs`, `Materials`…).
- Scènes créées : `MainMenu`, `Level01` et une scène de test par personne.

> Version de Unity : le projet est en 6000.6.10f1 (et pas 6.3 LTS comme prévu). Tout le groupe doit installer exactement cette version.

### 2.2 Réglages et packages

- Tags ajoutés : `Obstacle`, `Coin`, `Boost`, `SlowZone`, `JumpPad`, `Checkpoint`, `KillZone` (`Player` et `Finish` existent déjà).
- Packages installés : Splines, ProBuilder, Input System.
- Réglages Git : Force Text + Visible Meta Files.

### 2.3 Partage avec le groupe

- Fichiers de départ (« squelettes ») pour les autres, avec les méthodes communes du cahier des charges.
- `.gitignore` Unity + `CREDITS.txt`.
- Projet envoyé sur GitHub avec les branches `main`, `develop` et `feature/camera`.

## 3. Étape 2 : Mes scripts

### 3.1 CameraFollow : la caméra

- Placée derrière et au-dessus du joueur.
- Mouvement fluide (pas de saccades) et suit les virages.
- Regarde devant le joueur pour voir le parcours qui arrive.
- Bonus : la caméra recule pendant les sauts et le champ de vision s'élargit avec la vitesse.

### 3.2 RespawnManager : les chutes

- Retient le dernier checkpoint franchi.
- Quand le joueur tombe : +3 secondes de pénalité, puis réapparition au checkpoint.
- Au bout de 3 chutes : Game Over.

### 3.3 FinishLine : l'arrivée

- Détecte quand le joueur franchit la ligne d'arrivée.
- Arrête le chrono, calcule le score et déclenche la victoire.
- Si on dépasse le temps limite (180 s) : Game Over.

$$
\text{Score} = \text{pièces} \times 10 + \text{bonus de temps}
$$

### 3.4 Explication des règles

| Règle | Valeur |
|---|---|
| Pénalité par chute | +3 secondes |
| Nombre de chutes avant Game Over | 3 |
| Temps limite | 180 s |
| Score | pièces × 10 + bonus de temps |

## 4. Étape 3 : Intégration des Pull Requests

### 4.1 Méthode

Pour chaque PR : je regarde les fichiers modifiés, je relis le code, je vérifie qu'il n'y a pas de conflit, que le projet compile, puis je teste en jeu avant de fusionner dans `develop`.

### 4.2 Les PR du groupe

| PR | Personne | Contenu | Résultat |
|---|---|---|---|
| #1 | Lilou | Caméra, règles, Test_Rules, tableau de suivi | Fusionnée |
| #2 | Deaa | Obstacles, bonus, zones, tremplins | Fusionnée |
| #4 | Sofia | Circuit complet (~1 min), checkpoints, décor, piscine | Fusionnée |
| #3 | Drilon | Déplacement du joueur, chute, 6 personnages | Fusionnée (corrections demandées) |
| #5 | Art | Menu, HUD, chrono | Fusionnée |

### 4.3 Test d'intégration (tout le monde ensemble)

Joueur de Drilon + circuit de Sofia + ma caméra et mes règles :

- Le joueur avance seul, saute, prend les boosts et ralentit aux chocs.
- Les 12 checkpoints sont détectés.
- Chute → réapparition au checkpoint.
- Arrivée détectée → score → victoire.
- Une course dure environ 70 secondes.

> Phase 2 validée : on peut jouer une course complète du départ à l'arrivée.

## 5. Étape 4 : Finalisation

Tout le travail du groupe est terminé :

- [x] Monter la vraie scène Level01 (circuit + joueur + obstacles + caméra)
- [x] Ajouter l'interface d'Art (menu, HUD, chrono)
- [x] Remplacer la capsule par le personnage de Drilon (`P_Player`)
- [x] Tests à 5, corrections, puis build .exe

## Test et résultat

| Scène | Ce que j'ai testé | Résultat |
|---|---|---|
| `Test_Camera` | Suivi, virages, gauche/droite, saut | La caméra suit bien |
| `Test_Rules` | 3 chutes dans un trou | Réapparition ×2 puis Game Over |
| `Test_Rules` | Éviter le trou et finir | Arrivée, score, victoire |

Résultat : 0 erreur dans la Console Unity.

## Les mots techniques

| Mot | Définition |
|---|---|
| Unity | Logiciel pour créer le jeu (moteur de jeu) |
| C# | Langage de programmation utilisé dans Unity |
| Script | Fichier de code qui donne un comportement à un objet |
| Scène | Un niveau ou un écran du jeu |
| Prefab | Objet tout prêt, réutilisable dans plusieurs scènes |
| Tag | Étiquette sur un objet pour que les scripts le reconnaissent |
| Checkpoint | Point de passage où l'on réapparaît après une chute |
| Git / GitHub | Outil / site pour partager le projet et garder l'historique |
| Branche | Copie du projet où une personne travaille sans gêner les autres |
| Pull Request (PR) | Demande pour ajouter son travail dans la version commune |
| Fusionner (merge) | Ajouter le travail d'une branche dans une autre |

## Conclusion

Le projet est terminé : toutes les parties du groupe ont été fusionnées, la scène Level01 est complète avec l'interface, le vrai personnage et le build .exe. De mon côté, j'ai créé le projet commun, codé la caméra et les règles de la course, et assemblé le travail de chacun.
