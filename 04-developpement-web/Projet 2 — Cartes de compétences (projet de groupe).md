# Cartes de compétences — Documentation de réalisation

**Classe :** E1A
**Groupe :** Drilon Nuhija, Deaa Rrudhani, Sofia Negreche, Art Tolaj, Lilou Seve
**Projet de groupe :** site de cartes de compétences, avec classement, mini-jeux et recrutement d'équipe.
**Site en ligne :** https://cartes-competences.vercel.app
**Dépôt Git :** https://github.com/dnhj-06/cartes-competences (privé, accès sur invitation)


> **Plan de la documentation**
> - **Démarche HERMES** : mandat, phases, planification prévue et réalisée.
> - **Documentation d'installation** : parties 0 à 10 (tout refaire depuis zéro).
> - **Incidents** : partie 11.
> - **Choix techniques** : partie 12.
> - **Documentation d'exploitation** : partie 13 (faire vivre le site au quotidien).
> - **Guide d'utilisation** : partie 14 (élève et admin).
> - **Journal de bord** : partie 15.
> - **Bilan** : partie 16.

> **But du site :** chaque élève volontaire crée sa carte avec 6 stats (Réseau, Systèmes, Matériel, Web, Programmation, Logique). Il gagne des points en jouant à des mini-jeux liés aux cours, puis dépense ces points pour monter ses stats. Les cartes sont classées par note globale, et on peut chercher des coéquipiers selon un profil d'équipe.
>
> **Contraintes :**
> - HTML, CSS et JavaScript uniquement (modules ES, sans framework, sans étape de build) ;
> - tout gratuit : Firebase (plan Spark), Vercel (plan Hobby), GitHub ;
> - toujours `textContent`, jamais `innerHTML` (protection contre l'injection de code) ;
> - aucun nom ni donnée personnelle dans le code publié.

---

## Équipe

| Membre | GitHub | Rôle |
|---|---|---|
| Drilon Nuhija | `dnhj-06` | Chef de projet : organisation GitHub (relectures, fusions), format des données, pages du site (classement, fiche joueur, Ma carte, Créer ma carte, recrutement, menu), branchement des pages sur Firebase |
| Deaa Rrudhani | `drrdh23` | Firebase : création du projet, Authentication, Firestore, règles de sécurité, clé API ; pages d'inscription et de connexion ; calculs et photos |
| Sofia Negreche | `sofianegreche` | Page Mon équipe, mentions légales, page admin, relecture et tests des Pull Requests |
| Art Tolaj | `at-stm` | Design : couleurs, typographie, carte et ses niveaux, logo |
| Lilou Seve | `lilouseve` | Mini-jeux : moteur, format et fichiers de questions ; plan de test |

> **Captures :** les 50 captures sont numérotées dans l'ordre (01 à 50), avec le nom de la personne qui les a faites. Les adresses e-mail sont floutées.

---

## Démarche HERMES

Le projet suit les quatre phases de **HERMES 2022** (approche traditionnelle). En haut de chaque partie de cette documentation, on indique la phase concernée.

### Mandat d'initialisation

| | |
|---|---|
| **Mandant** | Enseignant du PPE (classe E1A) |
| **Chef de projet** | Drilon Nuhija |
| **Situation de départ** | Les élèves révisent chacun de leur côté, sans lien entre les cours et sans moyen simple de trouver des coéquipiers selon leurs points forts. |
| **Objectif** | Un site où chaque élève volontaire a une carte de compétences (6 stats) qui progresse grâce à des mini-jeux liés aux cours, avec un classement et un outil de recrutement d'équipe. |
| **Périmètre V1** | Comptes de l'école, création de carte, classement, fiche joueur, Ma carte, mini-jeux, recrutement, Mon équipe, page admin (photos), mentions légales. |
| **Contraintes** | HTML, CSS et JavaScript uniquement ; tout gratuit ; seulement les adresses @git.swiss ; aucune donnée personnelle dans le code. |
| **Risques identifiés** | Limites des offres gratuites (Firebase Spark, Vercel Hobby), triche sur les points, photos des élèves (données personnelles). |

### Les quatre phases

| Phase | Ce qu'on a fait | Livrables | Parties | Jalon |
|---|---|---|---|---|
| **1. Initialisation** | Idée du projet, cahier des charges, répartition des rôles, choix des outils | Cahier des charges, répartition des rôles | 0, 1 | Cahier des charges partagé avec le groupe (11.11) |
| **2. Conception** | Choix de la technique (13.11), format des données, maquette de la carte, règles de travail Git, règles de sécurité | `docs/format-donnees.md`, maquette, `firestore.rules` | 1.2, 2, 4, 9 | Format des données validé par le groupe |
| **3. Réalisation** | Firebase, pages, design, photos, mini-jeux, tests de chaque Pull Request | Code sur `main` (PR n° 1 à 36), plan de test | 3, 5, 6, 7, 8 | Toutes les PR de la V1 fusionnées |
| **4. Déploiement** | Mise en ligne sur Vercel, adresse ajoutée dans Firebase et sur la clé API, documentation | Site en ligne, cette documentation | 10, 11 | Site accessible sur cartes-competences.vercel.app |

### Planification : prévu et réalisé

Semaine 1 = du lundi 9.11 au vendredi 13.11 · Semaine 2 = du lundi 16.11 au vendredi 20.11.

| Phase | Prévu | Réalisé | Écart et explication |
|---|---|---|---|
| **Initialisation** | Semaine 1 | 9.11 → 12.11 (cahier des charges partagé le 11.11) | Seulement 3 membres sur 5 au démarrage : la répartition a été finalisée le 12.11, avec Drilon comme chef de projet. |
| **Conception** | Semaine 1 | 12.11 → 13.11 (choix de la technique le 13.11), puis mises à jour | Le format des données a été modifié pendant la réalisation (photo facultative, coût des points) : relu et validé à chaque fois par Pull Request. |
| **Réalisation** | Semaine 1 et semaine 2 | 15.11 → 19.11 (Firebase le 15.11, mini-jeux les 16.11 et 18.11, photos le 18.11) | Les points gagnés avec les mini-jeux et l'enregistrement des équipes ne sont pas terminés : reportés en V2 pour livrer une V1 stable. |
| **Déploiement** | Fin de semaine 2 | Semaine 2 (site en ligne, documentation le 19.11) | Vercel Hobby ne publie que les commits du propriétaire : redéploiement à la main après chaque fusion. Page Mon équipe vide en ligne, corrigée (PR n° 36). |

### Livrables : prévu et réalisé

| Prévu dans la V1 | Réalisé | Remarque |
|---|---|---|
| Comptes de l'école et connexion | ✅ | Adresse @git.swiss vérifiée obligatoire |
| Carte, classement, fiche joueur, Ma carte | ✅ | |
| Mini-jeux jouables | ✅ | 3 jeux |
| Points gagnés avec les mini-jeux | ❌ | Reporté en V2 (collection `gains`) |
| Recrutement et Mon équipe | ✅ | Équipes encore en données de test |
| Équipes enregistrées dans Firestore | ❌ | Reporté en V2 |
| Page admin (validation des photos) | ✅ | Design de la page reporté en V2 |
| Limite des gains par jour côté serveur | ❌ | Reporté en V2 (fonction serveur) |
| Mise en ligne gratuite | ✅ | Vercel Hobby, redéploiement à la main pour les PR des autres membres |

---

## 0. Outils à préparer

**Phase HERMES :** Initialisation

1. Installer **VS Code** et l'extension **Live Server** (pour tester en local sur `http://127.0.0.1:5500`).
2. Installer **Git** (Git Bash sur Windows).
3. Créer un compte **GitHub**, un compte **Firebase** (avec un compte Google) et un compte **Vercel** (connexion avec GitHub).
4. Se mettre d'accord sur la répartition : design, pages (front), base de données et règles (back), mini-jeux, tests.

#### 📸 Captures


📸 **Capture 01 — Git installé** *(Deaa)*
![01-git-installation](https://hackmd.io/_uploads/r1vRfL2AMx.png)


---

## 1. Organisation GitHub

**Phase HERMES :** Initialisation

**Réalisé par :** Drilon (dépôt, invitations, relectures et fusions), avec tout le groupe

### 1.1 Créer le dépôt

1. Sur GitHub : **New repository** → nom `cartes-competences` → **Private** → cocher *Add a README*.
2. **Settings → Collaborators** : inviter chaque membre du groupe.
3. **Settings → General → Pull Requests** : garder seulement **Allow squash merging** (un commit propre par sujet sur `main`).
4. **Settings → Branches** : protéger `main` (passage obligatoire par une Pull Request).

### 1.2 Règles de travail

| Règle | Pourquoi |
|---|---|
| Une branche par sujet (`prenom/sujet`, ex. `prenom/page-classement`) | On sait ce que contient chaque branche |
| Jamais de commit direct sur `main` | `main` = ce qui est en ligne |
| Une Pull Request par branche, relue et testée par un autre membre | On évite les bugs et les oublis |
| Fusion en **Squash and merge**, puis suppression de la branche | Historique lisible |
| Messages de commit en français, clairs | Ex. « Classement : filtre par niveau » |

### 1.3 Commandes de base

```bash
# Récupérer le projet la première fois
git clone https://github.com/<compte>/cartes-competences.git
cd cartes-competences

# Commencer un sujet
git checkout main
git pull
git checkout -b prenom/mon-sujet

# Enregistrer et envoyer
git add .
git commit -m "Page X : ce qui a été fait"
git push -u origin prenom/mon-sujet
```

Puis sur GitHub : **Compare & pull request** → décrire *ce que fait la PR* et *comment tester*.

> Comme on fusionne en *Squash*, ne pas faire `git merge origin/main` sur une vieille branche locale (conflits sur tous les fichiers). Pour se remettre à jour :
> ```bash
> git fetch --all --prune
> git reset --hard origin/main
> ```

#### 📸 Captures

📸 **Capture 02 — Dépôt cartes-competences créé en privé** *(Drilon)*
![02-github-depot-cree](https://hackmd.io/_uploads/r1KCfLnRMl.jpg)

📸 **Capture 03 — Vérification de Git, configuration et clonage du dépôt** *(Deaa)*
![03-git-config-clone](https://hackmd.io/_uploads/HyqCz83RMx.png)

📸 **Capture 04 — Création d'une branche par sujet** *(Deaa)*
![04-git-nouvelle-branche](https://hackmd.io/_uploads/SJiCzLh0Me.png)

📸 **Capture 05 — Ouverture d'une Pull Request** *(Drilon)*
![05-github-pull-request](https://hackmd.io/_uploads/ryxZkQLnCfe.jpg)

📸 **Capture 06 — Relecture d'une Pull Request par un autre membre** *(Drilon)*
![06-github-relecture](https://hackmd.io/_uploads/By41XI3Aze.jpg)

📸 **Capture 07 — Pull Request fusionnée en Squash and merge** *(Drilon)*
![07-github-squash-merge](https://hackmd.io/_uploads/BkBkmInRMx.jpg)

### 1.4 Structure des fichiers

```
index.html            → classement (page d'accueil)
joueur.html           → fiche d'un joueur
ma-carte.html         → dépenser ses points, accord photo, envoi de photo
creer-carte.html      → création de la carte (première visite)
recrutement.html      → chercher des joueurs pour une équipe
equipe.html           → mes équipes
mini-jeux.html, jeu.html
admin.html            → validation des photos
connexion.html, inscription.html, mentions-legales.html
css/   commun.css (design général), carte.css (la carte), pages.css (mise en page), provisoire.css
js/    firebase.js, auth.js, donnees.js, calculs.js, photos.js, carte.js, menu.js, profils.js, compatibilite.js
js/pages/   un script par page
js/jeux/    moteur des mini-jeux
questions/  questions de chaque mini-jeu
docs/       format des données, format des questions, plan de test, charte, accord photo
firestore.rules, .vercelignore
```

---

## 2. Format des données

**Phase HERMES :** Conception

**Réalisé par :** Drilon (format), Deaa (calculs et relecture côté règles)

À faire **avant** de coder les pages, pour que le front et le back utilisent les mêmes noms.

1. Écrire `docs/format-donnees.md` avec une section par collection Firestore.
2. Règle de nommage : champs en français, sans accent, en camelCase (`pointsDispo`, `photoStatut`).
3. Collections :

| Collection | Un document = | Identifiant |
|---|---|---|
| `joueurs` | une carte | uid Firebase du joueur |
| `photos` | la photo (grande + miniature) | uid du joueur |
| `gains` | une partie récompensée | automatique |
| `miniJeux` | un mini-jeu | court, ex. `subnetting-chrono` |
| `equipes` | une équipe | automatique |
| `admins` | un admin | uid de l'admin |

4. Champs d'une carte (`joueurs/{uid}`) : `pseudo`, `stats` (6 nombres), `noteDepart` (50), `pointsDispo`, `pointsGagnesTotal`, `visibleRecrutement`, `photoStatut` (`aucune`, `en_attente`, `validee`, `refusee`), `miniature`, `accordPhoto`, `creeLe`, `noteAtteinteLe`.
5. **Ne pas enregistrer** la note globale, le niveau ni la spécialité : on les calcule à l'affichage (jamais faux ni décalés).

### 2.1 Règles de calcul (`js/calculs.js`)

| Calcul | Règle |
|---|---|
| Note globale | moyenne des 6 stats, arrondie |
| Niveau | 50–64 bronze, 65–74 argent, 75–84 or, 85+ élite |
| Coût du prochain point | stat 40–74 → 1, 75–84 → 2, 85–98 → 3, 99 = maximum |
| Création de carte | 40 partout + 60 points à répartir, 60 max par stat (total 300, note 50) |

#### 📸 Captures

📸 **Capture 08 — Format d'une carte (collection joueurs)** *(Deaa)*
![08-format-donnees-joueurs](https://hackmd.io/_uploads/B1gwyX8nAMl.png)

📸 **Capture 09 — calculs.js testé dans la console : note, niveau et coût d'un point** *(Deaa)*
![09-calculs-test-console](https://hackmd.io/_uploads/Skt17IhCGl.png)


---

## 3. Firebase (base de données et comptes)

**Phase HERMES :** Réalisation

**Réalisé par :** Deaa

### 3.1 Créer le projet

1. [console.firebase.google.com](https://console.firebase.google.com) → **Ajouter un projet** → nom `cartes-competences` → désactiver Google Analytics.
2. Rester sur le plan **Spark** (gratuit).
3. **Paramètres du projet → Vos applications → Web (`</>`)** → enregistrer l'application → copier l'objet `firebaseConfig`.

#### 📸 Captures

📸 **Capture 10 — Création du projet Firebase** *(Deaa)*
![10-firebase-nom-projet](https://hackmd.io/_uploads/r1syQL2CGl.png)

📸 **Capture 11 — Plan Spark (gratuit)** *(Deaa)*
![11-firebase-plan-spark](https://hackmd.io/_uploads/SJCyXIhRfe.png)

📸 **Capture 12 — Objet firebaseConfig à copier** *(Deaa)*
![12-firebase-config-cdn](https://hackmd.io/_uploads/rkxgXL3AGl.png)

📸 **Capture 13 — Membres du groupe invités sur le projet Firebase** *(Deaa)*
![13-firebase-membres-invites](https://hackmd.io/_uploads/HJWxmL20zl.png)


### 3.2 Authentification

1. **Authentication → Commencer → Adresse e-mail/Mot de passe** → activer.
2. **Authentication → Paramètres → Domaines autorisés** : vérifier `localhost`, ajouter `127.0.0.1` et plus tard l'adresse Vercel.
3. Dans le code (`js/auth.js`) :
   - n'accepter que les adresses qui finissent par `@git.swiss` ;
   - envoyer l'e-mail de vérification après l'inscription ;
   - refuser la connexion tant que l'adresse n'est pas vérifiée ;
   - traduire les codes d'erreur Firebase en phrases françaises.

#### 📸 Captures

📸 **Capture 14 — Activation de la méthode Adresse e-mail/Mot de passe** *(Deaa)*
![14-auth-email-activation](https://hackmd.io/_uploads/rJmgX83Cfl.png)

📸 **Capture 15 — Domaines autorisés** *(Deaa)*
![15-auth-domaines-autorises](https://hackmd.io/_uploads/SJEeQ82CMx.png)


### 3.3 Firestore

1. **Firestore Database → Créer une base de données** → mode **production** → région **europe-west6 (Zurich)**.
2. Créer à la main la collection `admins` : un document dont l'identifiant est l'**uid** de l'admin (visible dans *Authentication → Users*).

#### 📸 Captures

📸 **Capture 16 — Région europe-west6 (Zurich)** *(Deaa)*
![16-firestore-region-zurich](https://hackmd.io/_uploads/rySgQ82Azl.png)

📸 **Capture 17 — Facturation refusée : on reste sur Spark** *(Deaa)*
![17-firestore-facturation-refusee](https://hackmd.io/_uploads/H1veXL30zg.png)

📸 **Capture 18 — Collections admins, joueurs et photos** *(Deaa)*
![18-firestore-collections](https://hackmd.io/_uploads/H1YeQI2AMx.png)


### 3.4 Configuration dans le code

1. Créer `js/firebase.js` qui importe le SDK depuis `https://www.gstatic.com/firebasejs/<version>/...` et exporte `db` et `auth`.
2. Coller la configuration **dans ce fichier** (pas de fichier séparé : le site n'a pas d'étape de build et Vercel publie les fichiers tels quels).

> La clé API web de Firebase **n'est pas un secret** : elle est visible dans tout site Firebase. La sécurité vient des **règles Firestore** et de la **restriction de la clé** (étape 3.6).

#### 📸 Captures

📸 **Capture 19 — js/firebase.js : connexion à Firebase** *(Deaa)*
![19-firebase-js-code](https://hackmd.io/_uploads/B1nemLn0Gl.png)

📸 **Capture 20 — Test : Firebase répond (auth et db dans la console)** *(Deaa)*
![20-firebase-test-console](https://hackmd.io/_uploads/BJ0lXI2RMe.png)


### 3.5 Règles de sécurité (`firestore.rules`)

Principe : **tout est interdit sauf ce qui est écrit**. Fonctions utiles : `estEleveVerifie()` (connecté + e-mail vérifié + `@git.swiss`) et `estAdmin()` (document dans `admins`).

| Collection | Lire | Écrire |
|---|---|---|
| `joueurs` | tout élève vérifié | création de SA carte une fois (valeurs de départ imposées) ; ensuite seulement : profil, achat d'**un** point au bon coût, envoi de photo (`en_attente`), retrait de l'accord photo ; l'admin passe `photoStatut` à `validee`/`refusee` |
| `photos` | le joueur, les admins, tout le monde si validée | le joueur pour la sienne, avec son accord ; suppression seulement avec le retrait de l'accord |
| `gains` | le joueur et les admins | création limitée (0 à 3 points, score 0 à 100) |
| `miniJeux` | tout élève vérifié | admins |
| `equipes` | propriétaire et membres | propriétaire |
| `admins` | soi-même (pour savoir si on est admin) | personne (ajout à la main) |

1. Écrire les règles dans `firestore.rules`.
2. Les tester dans **Firestore → Règles → Terrain de jeu des règles** (cas autorisés **et** cas refusés).
3. Cliquer sur **Publier**.

> **Limite V1 :** les règles seules ne peuvent pas limiter le nombre de gains par jour. Prévu en V2 avec une fonction serveur.

#### 📸 Captures

📸 **Capture 21 — Simulateur de règles** *(Deaa)*
![21-regles-simulateur](https://hackmd.io/_uploads/ByZZmI2Cfl.png)

📸 **Capture 22 — Lecture refusée pour une adresse hors école** *(Deaa)*
![22-regles-lecture-refusee-gmail](https://hackmd.io/_uploads/ByQ-QL2Czx.png)

📸 **Capture 23 — Test : triche sur les stats, refusé** *(Deaa)*
![23-regles-test-triche](https://hackmd.io/_uploads/HJPbQL3Afg.jpg)

📸 **Capture 24 — Récapitulatif des 12 tests des règles** *(Deaa)*
![24-regles-tableau-tests](https://hackmd.io/_uploads/BJ9-QI20Mg.png)


### 3.6 Restreindre la clé API

1. [console.cloud.google.com](https://console.cloud.google.com) → projet → **API et services → Identifiants** → *Browser key*.
2. **Restrictions d'application → Sites web** : ajouter `http://127.0.0.1:5500/*`, `http://localhost:5500/*` et `https://<adresse>.vercel.app/*`.

#### 📸 Captures

📸 **Capture 25 — Restrictions de la clé API** *(Deaa)*
![25-cle-restrictions](https://hackmd.io/_uploads/BynWXU2Czg.png)

📸 **Capture 26 — Sites autorisés à utiliser la clé** *(Deaa)*
![26-cle-sites-autorises](https://hackmd.io/_uploads/SykfXUn0fg.png)


### 3.7 Fonctions d'accès aux données (`js/donnees.js`)

Chaque fonction fait **exactement** l'écriture que les règles acceptent :

| Fonction | Ce qu'elle fait |
|---|---|
| `lireJoueurs()`, `lireJoueur(uid)`, `lirePhoto(uid)` | lecture |
| `estAdmin(uid)` | vrai si `admins/{uid}` existe |
| `creerCarte(...)` | carte sans photo, 0 point, note de départ 50 |
| `modifierProfil(...)` | pseudo et visibilité au recrutement |
| `donnerAccordPhoto(uid)` / `retirerAccordPhoto(uid)` | le retrait efface la miniature et `photos/{uid}` dans un seul *batch* |
| `acheterPoint(joueur, cle)` | **un point = une écriture**, coût selon `coutPoint()` |
| `validerPhoto(uid)` / `refuserPhoto(uid)` | réservé aux admins |

---

## 4. Design

**Phase HERMES :** Conception et réalisation

**Réalisé par :** Art

1. Choisir une identité : thème sombre, une couleur d'accent, une police lisible, un logo en SVG (`assets/logo.svg`).
2. `css/commun.css` : variables de couleurs et d'espacements, barre du haut (`.entete`), menu, boutons (`.bouton`, `.bouton--secondaire`), titres.
3. `css/carte.css` : la carte et ses variantes par niveau (`.carte--bronze`, `--argent`, `--or`, `--elite`, `--unranked`), version mini (`--mini`).
4. `js/carte.js` : une fonction `afficherCarte(joueur, { mini })` qui construit la carte en DOM (note, niveau, spécialité, photo ou silhouette, pseudo, 6 stats).
5. `css/pages.css` : mise en page de chaque page (colonnes, tableaux, formulaires, messages).

### 4.1 Ce qu'a fait Art

Art n'a pas fait de captures : son travail se voit sur les captures des pages (parties 5 et 7).

1. **Identité visuelle** : thème sombre, une couleur d'accent cyan, titres en majuscules, logo en SVG (`assets/logo.svg`).
2. **`css/commun.css`** : variables (couleurs, rayons, espacements), barre du haut avec le logo et le menu (onglet actif souligné), boutons principal et secondaire, sur-titres et chapeaux de page.
3. **`css/carte.css`** : la carte façon carte de foot, une couleur par niveau (sans niveau, bronze, argent, or, élite), version mini pour les listes et dos de carte.
4. **`js/carte.js`** : la fonction `afficherCarte(joueur, { mini, dos })` qui construit la carte (note, niveau, spécialité, photo ou silhouette, pseudo, 6 stats dans l'ordre RES, SYS, MAT, WEB, PRG, LOG), uniquement avec `textContent`.
5. **Intégration** : design fusionné en deux PR (n° 23 et n° 24), puis appliqué à toutes les pages (PR n° 27). Les dernières corrections ont été envoyées en zip et reprises dans le dépôt.

> **Accessibilité à vérifier :** contraste suffisant, contour visible au clavier (`:focus-visible`), `label` pour chaque champ, zone de message en `role="status"`, images avec `alt`.

#### 📸 Captures

📸 **Capture 27 — Design de la carte et de la barre du haut** *(Art)*
![27-design-carte](https://hackmd.io/_uploads/SJ8MQU2AMg.png)


---

## 5. Pages du site

**Phase HERMES :** Réalisation

**Réalisé par :** Drilon (classement, fiche, Ma carte, Créer ma carte, recrutement, menu, branchement Firebase), Deaa (inscription et connexion), Sofia (Mon équipe, admin, mentions légales)

Chaque page a son HTML et son script dans `js/pages/`. Toutes chargent `js/menu.js` (barre du haut + bouton *Se connecter / Se déconnecter*).

#### 📸 Captures

📸 **Capture 28 — Menu commun en haut de chaque page** *(Drilon)*
![28-menu](https://hackmd.io/_uploads/BJ_MQI2Azl.png)


### 5.1 Connexion et inscription

1. Formulaires avec `label`, `autocomplete` et une zone de message.
2. Inscription → e-mail de vérification → message « clique sur le lien ».
3. Connexion → si l'adresse n'est pas vérifiée : déconnexion + message.
4. Bouton « Mot de passe oublié ».

#### 📸 Captures

📸 **Capture 29 — js/auth.js : connexion, mot de passe oublié, exigerConnexion** *(Deaa)*
![29-auth-js-2](https://hackmd.io/_uploads/r1tG78nAMl.png)

📸 **Capture 30 — Page d'inscription** *(Deaa)*
![30-inscription-page](https://hackmd.io/_uploads/HJjz7I2Rzl.png)

📸 **Capture 31 — Test 1 : adresse hors école refusée** *(Deaa)*
![31-test-adresse-hors-ecole](https://hackmd.io/_uploads/r12zQI3AMl.png)

📸 **Capture 32 — Test 3 : compte créé** *(Deaa)*
![32-test-compte-cree](https://hackmd.io/_uploads/ryCM7Un0zl.png)

📸 **Capture 33 — Page de connexion** *(Deaa)*
![33-connexion-page](https://hackmd.io/_uploads/BJ1XmU30Me.png)

📸 **Capture 34 — Description de la PR avec le tableau des tests** *(Deaa)*
![34-connexion-description-pr](https://hackmd.io/_uploads/HyG7QU20Gg.png)


### 5.2 Protection des pages

En haut de chaque script de page :
```javascript
import { exigerConnexion } from "../auth.js";
const utilisateur = await exigerConnexion(); // sinon → connexion.html
```
Puis lire les données dans un `try / catch` et afficher un message clair si Firestore ne répond pas.

### 5.3 Créer ma carte

1. Champ pseudo (3 à 20 caractères).
2. 6 champs numériques (40 à 60) + compteur « points à répartir ».
3. Aperçu de la carte mis à jour en direct.
4. Cases *visible au recrutement* et *accord photo*.
5. Bouton actif seulement si exactement 60 points sont répartis → `creerCarte()` → redirection vers *Ma carte*.

### 5.4 Classement (page d'accueil)

1. Lire tous les joueurs, calculer la note, trier (note décroissante, puis pseudo).
2. Rang « sportif » : deux ex æquo ont le même rang.
3. Filtre par niveau, compteur de joueurs.
4. Chaque ligne : rang, mini-carte, pseudo cliquable vers la fiche.

#### 📸 Captures

📸 **Capture 35 — Classement avec le design** *(Drilon)*
![35-classement-design](https://hackmd.io/_uploads/BJNmXLn0fl.png)


### 5.5 Fiche joueur

1. Lire l'`uid` dans l'adresse (`joueur.html?uid=...`).
2. Grande carte (grande photo si validée), note, niveau, rang, tableau des stats avec `<meter>`.

#### 📸 Captures

📸 **Capture 36 — Fiche joueur avec le design** *(Drilon)*
![36-fiche-joueur-design](https://hackmd.io/_uploads/H1ImQ8hRfx.png)


### 5.6 Ma carte

1. Si le joueur n'a pas de carte → `creer-carte.html`.
2. Boutons +1 / −1 par stat avec le coût du prochain point ; rien n'est enregistré avant **Valider**.
3. **Valider** : acheter les points un par un (`acheterPoint`).
4. Case *visible au recrutement*, case *accord photo*, envoi de photo (visible seulement avec l'accord).

#### 📸 Captures

📸 **Capture 37 — Coût du point selon la valeur de la stat** *(Drilon)*
![37-ma-carte-paliers](https://hackmd.io/_uploads/Byw7XIh0Gx.png)

📸 **Capture 38 — Ma carte avec le design** *(Drilon)*
![38-ma-carte-design](https://hackmd.io/_uploads/rJ_m78n0fe.png)

📸 **Capture 39 — Accord photo dans Ma carte** *(Drilon)*
![39-ma-carte-accord-photo](https://hackmd.io/_uploads/S1cX78nCMl.png)


### 5.7 Recrutement et Mon équipe

1. Choisir un profil d'équipe (stats attendues + poids) dans `js/profils.js`.
2. `js/compatibilite.js` calcule un pourcentage de compatibilité pour chaque joueur visible.
3. Ajouter des joueurs à l'équipe (nombre de places limité).
4. *Mon équipe* : liste des équipes dont on est propriétaire ou membre.

#### 📸 Captures

📸 **Capture 40 — Recrutement avec le design** *(Drilon)*
![40-recrutement-design](https://hackmd.io/_uploads/BJjXQUnCzg.png)

📸 **Capture 41 — equipe.js : affichage et bouton Retirer** *(Sofia)*
![41-equipe-js-affichage](https://hackmd.io/_uploads/BJ1VmI2CMl.png)

📸 **Capture 42 — PR n° 26 : page Mon équipe** *(Sofia)*
![42-equipe-pr](https://hackmd.io/_uploads/Hk-EX83Cze.png)


### 5.8 Admin

1. Vérifier `estAdmin()` ; sinon message « réservée aux admins ».
2. Liste des photos en attente avec la vraie photo, boutons **Valider** / **Refuser**.
3. Tableau des joueurs (pseudo, note, statut photo, visibilité).

#### 📸 Captures

📸 **Capture 43 — Page admin : connexion administrateur réussie** *(Deaa)*
![43-admin-page](https://hackmd.io/_uploads/H1mNXI3Afg.png)

📸 **Capture 44 — PR n° 28 : statut « Pas de photo »** *(Sofia)*
![44-admin-pr](https://hackmd.io/_uploads/ByV4XU2Rfg.png)


### 5.9 Mentions légales

1. Qui gère le site, quelles données sont enregistrées et pourquoi.
2. Photo facultative, accord et retrait de l'accord.
3. Adresse de contact pour les demandes sur les données.

#### 📸 Captures

📸 **Capture 45 — PR n° 25 : photo facultative et retrait de l'accord** *(Sofia)*
![45-mentions-pr](https://hackmd.io/_uploads/Bk84XU2Rzx.png)


---

## 6. Photos

**Phase HERMES :** Réalisation

**Réalisé par :** Deaa

1. `js/photos.js` → `preparerPhotos(fichier)` :
   - refuser ce qui n'est pas une image ou dépasse 15 Mo ;
   - recadrer au centre au format 2:3 ;
   - exporter en **WebP** : 300×450 (40 Ko max) et 100×150 (5 Ko max), en baissant la qualité jusqu'à la bonne taille.
2. `envoyerPhoto(uid, photos)` : vérifier l'accord, puis écrire `photos/{uid}` **et** passer `photoStatut` à `en_attente` dans un seul *batch*.
3. L'admin valide → la miniature est copiée dans la carte (le classement n'a besoin de rien d'autre).
4. On n'affiche la photo que si `photoStatut` vaut `validee`, sinon une silhouette.

#### 📸 Captures

📸 **Capture 46 — Compression : carte 300×450 et miniature 100×150 sous les limites** *(Deaa)*
![46-photos-compression](https://hackmd.io/_uploads/SJgOV78hCfg.png)

*La photo de l'écran Proxmox est une image prise au hasard : elle sert juste à montrer que la compression marche.*

📸 **Capture 47 — Test de triche sur la photo : refusé** *(Deaa)*
![47-photos-test-triche](https://hackmd.io/_uploads/Bk9VXLn0Mg.png)

📸 **Capture 48 — PR n° 22 : compression et envoi des photos** *(Deaa)*
![48-photos-pr22](https://hackmd.io/_uploads/ryoVmI3Afe.png)


---

## 7. Mini-jeux

**Phase HERMES :** Réalisation

**Réalisé par :** Lilou (format des questions, moteur, les trois jeux, page Mini-jeux, plan de test)

### 7.1 Préparer le poste

1. Installer Git et l'extension Live Server, cloner le dépôt.
2. Toujours ouvrir les pages avec **Live Server** : les modules JavaScript ne marchent pas en double-cliquant sur le fichier.

### 7.2 Format des questions (PR n° 8)

1. Écrire `docs/format-questions.md` : format commun à tous les jeux (énoncé, choix, bonne réponse, explication).
2. Règles fixées après la relecture : 10 questions par partie, masque de sous-réseau écrit sous les deux formes (`/24` et `255.255.255.0`), limites de la V1 notées.

### 7.3 Moteur commun (`js/jeux/moteur.js`, PR n° 11)

1. **Tirage au hasard sans doublon** avec le mélange de Fisher-Yates. Vérification : sur 60 000 mélanges, chaque ordre sort environ 10 000 fois.
2. **Chrono** : le temps restant est annoncé une fois par minute, puis à 10 secondes (lecteurs d'écran).
3. **Score sur 100** et résultat de fin de partie : `{ miniJeu, stat, score }`.
4. Page `jeu.html` en trois écrans : départ, partie, résultat (score, points gagnés, explications des questions ratées).

### 7.4 Les trois mini-jeux

`jeu.html?id=...` choisit le jeu. Un fichier de questions par jeu dans `questions/` :

| Mini-jeu | Stat | PR | Contenu |
|---|---|---|---|
| Subnetting chrono | RES | n° 12 | 20 questions, masques de /8 à /30, réponses recalculées en JavaScript (opérations sur les bits) |
| Trouve l'erreur | WEB | n° 13 | 15 extraits HTML/CSS, on choisit la ligne fautive ; les balises s'affichent en texte (`textContent`) |
| Quelle sortie ? | PRG | n° 14 | 16 programmes C#, tous vérifiés avec `dotnet run` (16 / 16 conformes) |

### 7.5 Page Mini-jeux et finitions

1. `mini-jeux.html` : liste des jeux avec des valeurs de test en attendant Firebase (PR n° 15).
2. Bouton « Passer » et accord au singulier « 1 bonne réponse » (PR n° 19).

#### 📸 Captures

📸 **Capture 49 — Liste des mini-jeux** *(Lilou)*
![49-minijeux-liste](https://hackmd.io/_uploads/HJ6VmU3CGl.png)

📸 **Capture 50 — Une partie de mini-jeu** *(Lilou)*
![50-minijeux-partie](https://hackmd.io/_uploads/S1AVXI20Gl.png)


---

## 8. Tests

**Phase HERMES :** Réalisation

**Réalisé par :** Lilou (plan de test), Deaa (tests des règles et de la connexion), Sofia (tests des Pull Requests)

1. Écrire `docs/plan-de-test.md` : un tableau par page (action, résultat attendu, résultat obtenu, ✅/❌) (PR n° 16), puis le compléter après la relecture (PR n° 17). Il sert pour la semaine de test avec la classe.
2. Tester chaque PR en local avec Live Server avant de l'approuver.
3. Cas importants à vérifier :
   - page ouverte sans être connecté → redirection vers la connexion ;
   - achat de points : 74 → 75 coûte 1, 75 → 76 coûte 2, 99 bloqué ;
   - retrait de l'accord photo → la photo disparaît ;
   - un non-admin ne peut pas ouvrir la page admin ;
   - **tests de triche** dans la console du navigateur (écrire des valeurs interdites) → refusés par les règles.

---

## 9. Données personnelles et sécurité

**Phase HERMES :** Conception

1. Dépôt GitHub en **privé**.
2. Aucun prénom, nom ou adresse dans le **code** et les commentaires publiés (parler de rôles : « front », « règles Firestore »). Les noms des membres restent dans cette documentation.
3. Données de test avec des identifiants neutres (`test01`, `test02`...).
4. Fichier `.vercelignore` pour **ne pas publier** sur le site ce qui est interne :
```
docs/
README.md
firestore.rules
```
5. Vérifier qu'un fichier ignoré n'est pas importé par une page (sinon la page ne charge plus).
6. Toujours `textContent` pour afficher du texte venant d'un utilisateur.
7. Chaque membre peut activer *Keep my email addresses private* dans ses réglages GitHub.

---

## 10. Mise en ligne sur Vercel

**Phase HERMES :** Déploiement

**Réalisé par :** Drilon et Deaa

1. [vercel.com](https://vercel.com) → **Sign Up** avec le compte GitHub **propriétaire du dépôt** → plan **Hobby**.
2. **Add New… → Project** → autoriser l'accès au dépôt `cartes-competences` → **Import**.
3. Réglages : *Framework Preset* **Other**, *Root Directory* `./`, pas de commande de build.
4. **Deploy** → récupérer l'adresse `https://<nom>.vercel.app`.
5. Ajouter cette adresse dans Firebase (*Domaines autorisés*) et dans la restriction de la clé API (étape 3.6).

> **Plan Hobby :** Vercel ne déploie automatiquement que les commits du propriétaire du compte. Après la fusion d'une PR d'un autre membre : **Deployments → … → Redeploy**, ou **Create New → Deployment** sur `main`.

---

## 11. Incidents rencontrés

**Phase HERMES :** toutes les phases

> **Incident 1 — Sauvegardes Firestore payantes**
> **Cause :** à la création de la base, l'option des sauvegardes planifiées demande le plan Blaze (avec une carte bancaire).
> **Résolution :** facturation refusée, on reste sur le plan Spark gratuit (capture 17).

> **Incident 2 — « Cannot GET /connexion.html »**
> **Cause :** la page de connexion n'était pas encore dans le dossier ouvert par Live Server.
> **Résolution :** page créée au bon endroit, puis rechargée (capture 33).

> **Incident 3 — Redirection vers une page qui n'existe pas encore**
> **Cause :** après la connexion, le site envoie vers `index.html`, mais la page classement n'était pas encore fusionnée sur cette branche.
> **Résolution :** comportement attendu, noté dans la Pull Request ; réglé une fois le classement fusionné.

> **Incident 4 — Envoi de photo refusé (`permission-denied`)**
> **Cause :** les règles Firestore refusent l'envoi d'une photo sans carte ou sans accord photo.
> **Résolution :** `photos.js` vérifie la carte et l'accord avant l'envoi et affiche un message clair.

> **Incident 5 — Conflits en mettant à jour une ancienne branche locale**
> **Cause :** avec le *Squash and merge*, les commits de `main` ne sont plus les mêmes que ceux de la branche locale : Git voit deux versions de chaque fichier.
> **Résolution :** `git merge --abort`, copie de sauvegarde de la branche, puis `git reset --hard origin/main`.

> **Incident 6 — Page « Mon équipe » vide sur le site en ligne**
> **Cause :** le fichier `.vercelignore` empêchait la publication de `js/equipes-test.js`, dont la page a besoin.
> **Résolution :** fichier retiré de `.vercelignore` (Pull Request n° 36).

> **Incident 7 — Git pas reconnu après l'installation**
> **Cause :** VS Code était ouvert pendant l'installation et ne connaissait pas encore le nouveau chemin (PATH) de Git.
> **Résolution :** redémarrer VS Code (capture 01 pour l'installation).

> **Incident 8 — Les pages ne marchent pas en double-cliquant dessus**
> **Cause :** les modules JavaScript (`import`) et `fetch` sont bloqués quand la page est ouverte comme fichier (`file://`).
> **Résolution :** toujours ouvrir le site avec Live Server (`http://127.0.0.1:5500`).

> **Incident 9 — Chrome bloque le collage dans la console**
> **Cause :** protection de Chrome contre le code collé sans savoir ce qu'il fait.
> **Résolution :** taper `allow pasting` dans la console avant de coller un test.

| N° | Incident | Résolution |
|---|---|---|
| 1 | Sauvegardes Firestore payantes (Blaze) | Refusées, plan Spark gardé |
| 2 | `connexion.html` introuvable | Page créée au bon endroit |
| 3 | Redirection vers `index.html` absent | Réglé après la fusion du classement |
| 4 | Envoi de photo refusé | Vérification de la carte et de l'accord avant l'envoi |
| 5 | Conflits sur une branche locale | `git reset --hard origin/main` |
| 6 | Page Mon équipe vide en ligne | Correction de `.vercelignore` |
| 7 | Git pas reconnu | Redémarrer VS Code |
| 8 | Pages ouvertes en `file://` | Live Server |
| 9 | Collage bloqué dans la console | `allow pasting` |

---

## 12. Choix techniques

**Phase HERMES :** Conception

| Choix | Pourquoi | Alternative écartée | Limite connue |
|---|---|---|---|
| HTML, CSS, JavaScript sans framework | Ce qu'on voit en cours, aucune étape de build, Vercel publie les fichiers tels quels | React : plus long à apprendre dans le temps du projet | Plus de code à écrire à la main (pas de composants) |
| Firebase, plan Spark | Gratuit, comptes et base de données inclus, règles de sécurité côté serveur | Notre propre serveur (Node.js + base de données) : à héberger, payer et sécuriser nous-mêmes | Pas de fonction serveur gratuite, pas de sauvegarde automatique |
| Firestore en europe-west6 (Zurich) | Données des élèves stockées en Suisse | Région par défaut aux États-Unis | La région ne peut plus être changée |
| Vercel, plan Hobby | Gratuit avec un dépôt privé, mise en ligne depuis `main` | GitHub Pages : payant pour un dépôt privé | Déploiement automatique seulement pour les commits du propriétaire |
| Squash and merge | Un commit par sujet sur `main`, historique lisible | Merge classique : tous les petits commits dans `main` | Une vieille branche locale ne se met plus à jour avec `git merge` (partie 1, encadré) |
| `textContent` partout | Le texte d'un joueur ne peut jamais devenir du code | `innerHTML` : risque d'injection de code | Il faut créer chaque élément HTML en JavaScript |
| Calculs à l'affichage (note, niveau) | Jamais faux ni décalés | Enregistrer la note dans la base | Le calcul est refait sur chaque page |

---

## 13. Documentation d'exploitation

**Phase HERMES :** Déploiement

Ce qu'il faut faire pour faire vivre le site, sans connaître tout le code.

| Tâche | Comment faire |
|---|---|
| Publier une modification | Fusionner la Pull Request sur `main`. Si l'auteur n'est pas le propriétaire du compte Vercel : **Deployments → … → Redeploy** (partie 10). |
| Valider ou refuser une photo | Se connecter avec un compte admin → page **Admin** → **Valider** ou **Refuser**. |
| Ajouter un admin | Firebase → **Authentication → Users** : copier l'uid → **Firestore → admins** → nouveau document avec cet uid comme identifiant. |
| Modifier les règles de sécurité | Modifier `firestore.rules` sur une branche → tester dans le **Terrain de jeu des règles** → coller dans **Firestore → Règles** → **Publier** → Pull Request. |
| Ajouter des questions à un mini-jeu | Ajouter la question dans le fichier du jeu dans `questions/`, en suivant `docs/format-questions.md`, puis Pull Request. |
| Ajouter une nouvelle adresse du site | Firebase → **Authentication → Domaines autorisés** **et** Google Cloud → restriction de la clé API (partie 3.6). |
| Supprimer un joueur | Pas encore possible depuis la page admin (V2) : dans la console Firebase, supprimer `joueurs/{uid}`, `photos/{uid}` et le compte dans **Authentication**. |
| Surveiller les limites gratuites | Firebase → **Firestore → Utilisation** (lectures et écritures par jour du plan Spark). |

> **Sauvegardes :** le plan Spark ne fait pas de sauvegarde automatique de Firestore. Le code, lui, est sauvegardé sur GitHub.

---

## 14. Guide d'utilisation

**Phase HERMES :** Déploiement

### 14.1 Pour un élève

1. Ouvrir https://cartes-competences.vercel.app → **Créer un compte** avec son adresse **@git.swiss**.
2. Cliquer sur le lien reçu par e-mail, puis se connecter.
3. **Créer ma carte** : choisir un pseudo et répartir **60 points** sur les 6 stats (60 maximum par stat).
4. **Mini-jeux** : jouer pour gagner des points (3 parties récompensées par jour et par jeu).
5. **Ma carte** : dépenser ses points avec +1 / −1, puis **Valider**. Plus la stat est haute, plus le point coûte cher (1, 2 ou 3 points).
6. Photo (facultative) : cocher l'accord photo, envoyer une photo. Elle apparaît après validation par un admin. Décocher l'accord supprime la photo.
7. **Classement** : voir son rang, filtrer par niveau, cliquer sur un pseudo pour voir sa fiche.
8. **Recrutement** : choisir un profil d'équipe, ajouter les joueurs les plus compatibles. **Mon équipe** : voir ses équipes.
9. **Se déconnecter** en haut à droite.

### 14.2 Pour un admin

1. Se connecter avec un compte présent dans la collection `admins`.
2. Page **Admin** : valider ou refuser les photos en attente, voir le tableau des joueurs.

---

## 15. Journal de bord

**Phase HERMES :** toutes les phases

| Semaine | Fait | Problèmes | Solutions |
|---|---|---|---|
| **Semaine 1** (9.11 → 13.11) | Idée du projet et cahier des charges (partagé le 11.11) ; répartition des rôles et dépôt GitHub privé (12.11) ; choix de la technique : HTML, CSS, JavaScript (13.11) ; premier format des données | Groupe incomplet au démarrage (3 membres sur 5) ; Git pas reconnu après l'installation sur un poste | Rôles répartis dès que tout le monde était là, Drilon chef de projet ; redémarrer VS Code après l'installation de Git |
| **Semaine 2** (16.11 → 20.11) | Firebase (projet, comptes, base, 12 tests des règles, clé restreinte) ; connexion et inscription ; toutes les pages ; design appliqué partout ; photos ; 3 mini-jeux et plan de test ; mise en ligne sur Vercel ; documentation | Sauvegardes Firestore payantes ; conflits Git après les *Squash* ; Vercel ne publie pas les PR des autres membres ; page Mon équipe vide en ligne ; envoi de photo refusé | Plan Spark gardé ; `git reset --hard origin/main` ; redéploiement à la main ; correction de `.vercelignore` (PR n° 36) ; vérification de la carte et de l'accord avant l'envoi |

---|---|
| **Fait** | Firebase : projet, comptes, base, règles testées (12 tests), clé restreinte ; connexion et inscription ; pages classement, fiche, Ma carte, Créer ma carte, recrutement, Mon équipe, admin, mentions légales ; design appliqué partout ; photos ; les 3 mini-jeux et le plan de test ; mise en ligne sur Vercel ; documentation. |
| **Problèmes** | Sauvegardes Firestore payantes ; conflits Git après les *Squash* ; Vercel ne publie pas les PR des autres membres ; page Mon équipe vide en ligne ; envoi de photo refusé. |
| **Solutions** | Rester sur le plan Spark ; `git reset --hard origin/main` ; redéploiement à la main ; correction de `.vercelignore` (PR n° 36) ; vérification de la carte et de l'accord avant l'envoi. |

---

## 16. Bilan

**Phase HERMES :** toutes les phases

### 16.1 Ce qu'on a appris

- Travailler à plusieurs sur un même dépôt : une branche par sujet, Pull Request, relecture, fusion.
- Sécuriser une base de données avec des règles, et tester aussi ce qui doit être **refusé**.
- Mettre un site en ligne gratuitement et comprendre les limites des offres gratuites.

### 16.2 Ce qu'on ferait autrement

- Brancher les pages sur Firebase plus tôt, au lieu de garder longtemps des données de test.
- Créer le compte Vercel au nom de l'équipe dès le début (déploiement automatique pour tout le monde).
- Prévoir les fonctions serveur (limite des gains) dès la conception.

### 16.3 Risques restants

| Risque | Conséquence | Solution prévue |
|---|---|---|
| Gains par jour non limités côté serveur | Un tricheur pourrait gagner trop de points | Fonction serveur Vercel (V2) |
| Pas de sauvegarde automatique | Perte des cartes en cas d'erreur | Prévoir une copie des données (V2) |
| Limites du plan Spark | Site bloqué si trop de lectures par jour | Surveiller l'onglet Utilisation |

### 16.4 Ce que le projet apporte pour un poste en informatique

- Relire et tester le travail d'un collègue avant qu'il parte en production.
- Documenter pour qu'un collègue puisse reprendre le travail sans poser de questions.
- Penser sécurité et données personnelles dès le début d'un projet.
