# Projet 1 — Site vitrine pour un artisan local


## 1. Présentation du projet

Ce projet consiste à créer un site vitrine d'une seule page pour un artisan local fictif : **Dupont Électricité**, électricien à Genève. Le site présente l'entreprise, ses services et ses coordonnées. Il doit être lisible sur ordinateur comme sur mobile.

**Fichiers livrés :**

| Fichier | Rôle |
|---|---|
| `index.html` | Structure et contenu de la page |
| `style.css` | Mise en forme et responsive |

![image](https://hackmd.io/_uploads/rkcDwl86fe.png)


---

## 2. Choix de structure (HTML)

La page est découpée en trois sections, comme demandé : **Accueil**, **Services** et **Contact**. Ce découpage correspond à ce que cherche un visiteur : savoir qui est l'artisan, ce qu'il propose, et comment le joindre.

J'ai utilisé des **balises sémantiques** plutôt que des `<div>` partout, car elles décrivent le rôle de chaque zone. C'est plus clair à lire et mieux compris par les navigateurs et les lecteurs d'écran.

| Balise | Utilisation | Pourquoi |
|---|---|---|
| `<header>` | Nom de l'entreprise et menu | Zone d'en-tête de la page |
| `<nav>` | Liste de liens du menu | Zone de navigation |
| `<main>` | Contenu principal | Un seul par page |
| `<section>` | Accueil, Services, Contact | Une section par thème |
| `<article>` | Chaque service | Bloc indépendant, réutilisable |
| `<footer>` | Copyright | Pied de page |

**Hiérarchie des titres :** un seul `<h1>` (titre de la page, dans l'accueil), des `<h2>` pour les titres de sections et des `<h3>` pour chaque service. Cette hiérarchie sans saut de niveau aide la lecture et l'accessibilité.

**Navigation :** les liens du menu (`href="#services"`, etc.) pointent vers l'`id` de chaque section, ce qui permet de se déplacer dans la page.

**Contact :** le téléphone utilise `tel:` (appel direct depuis un mobile) et l'email utilise `mailto:` (ouverture de la messagerie). Cela simplifie la prise de contact pour le visiteur.

**Éléments du `<head>` :** `lang="fr"`, `charset="UTF-8"`, la balise `viewport` (indispensable pour le mobile), un `<title>` explicite et le lien vers `style.css`.

![image](https://hackmd.io/_uploads/ByJ7_x8pGl.png)

---

## 3. Choix de mise en forme (CSS)

- **Couleurs :** j'ai choisi un **bleu foncé (`#1a3a5c`)** comme couleur principale, pour le header et les titres. Il évoque le sérieux et la confiance, ce qui convient à un artisan, et il rappelle l'univers de l'électricité. Le fond de la page est un gris très clair (`#f5f5f5`), ce qui fait ressortir les cartes blanches des services. Le texte est en gris foncé (`#333333`), plus doux que du noir pur mais bien lisible. Le texte blanc sur le bleu foncé du header offre un bon contraste.
- **Police :** Arial, choisie pour sa lisibilité à l'écran.
- **Menu :** la liste est en `display: flex` pour aligner les liens horizontalement, sans puces ni soulignement. Les liens sont blancs sur le fond coloré du header.
- **Sections :** `max-width: 900px` et `margin: 0 auto` pour centrer le contenu et garder des lignes de texte lisibles sur grand écran.
- **Services en cartes :** les trois `<article>` sont placés côte à côte avec **Flexbox** (`display: flex`, `gap`, `flex: 1`) et stylisés en cartes (fond blanc, coins arrondis, légère ombre), ce qui rend les services faciles à comparer d'un coup d'œil.
- **Unités :** `rem` pour les tailles de texte, afin qu'elles s'adaptent aux réglages du navigateur.

![Capture d'écran 2026-11-02 125351](https://hackmd.io/_uploads/rJzeqg8aMe.png)
![Capture d'écran 2026-11-02 125358](https://hackmd.io/_uploads/HJMecl8afx.png)


---

## 4. Responsive (mobile)

Une **media query** `@media (max-width: 600px)` adapte la page aux petits écrans :

- les cartes de services passent en colonne (`flex-direction: column`) ;
- le menu passe en colonne ;
- la taille des titres est réduite pour éviter les débordements.

La balise `<meta name="viewport">` permet au navigateur mobile d'utiliser la bonne largeur d'écran.

**Test :** vérifié avec les outils de développement de Chrome (F12, mode appareil)

![Capture d'écran 2026-11-02 125438](https://hackmd.io/_uploads/rk-EcxUpzx.png)
![Capture d'écran 2026-11-02 125448](https://hackmd.io/_uploads/BkzE9gUafg.png)
![Capture d'écran 2026-11-02 125504](https://hackmd.io/_uploads/B1M45xL6fe.png)


---

## 5. Tests et validation

### 5.1 Tests dans deux navigateurs

| Point vérifié | Chrome | Firefox |
|---|---|---|
| Affichage général (header, sections, footer) | OK | OK |
| Liens du menu (défilement vers les sections) | OK | OK |
| Cartes de services côte à côte (desktop) | OK | OK |
| Cartes en colonne (mobile) | OK | OK |
| Lien `tel:` | OK | OK |
| Lien `mailto:` | OK | OK |

**Conclusion des tests :** le rendu est identique dans les deux navigateurs 
![Capture d'écran 2026-11-02 125937](https://hackmd.io/_uploads/SyZvslU6fl.png)

![image](https://hackmd.io/_uploads/SyK8seUpGl.png)


### 5.2 Validation du code

Le code HTML a été vérifié avec le validateur W3C (validator.w3.org).

![image](https://hackmd.io/_uploads/SyVmal8Tzx.png)


---

## 6. Problèmes rencontrés et solutions

| Problème | Cause | Solution |
|---|---|---|
| Un lien du menu ne fonctionnait pas | Il manquait le `#` dans le `href` (`services` au lieu de `#services`) | Ajout du `#` pour cibler l'`id` de la section |
| Le lien « Contact » ne menait nulle part | `id="Contact"` (majuscule) ne correspondait pas à `href="#contact"` | Écriture de l'`id` en minuscule, identique au lien |
| Mise en page cassée après le titre | `<h1>` jamais refermé (`<h1>` au lieu de `</h1>`) | Correction en `</h1>` |
| Liens `tel:` et `mailto:` peu fiables | Espaces dans la valeur du `href` | Suppression des espaces |


## 7. Conclusion

Le site répond aux consignes : contenu structuré en trois sections, HTML sémantique, mise en forme CSS, affichage adapté au mobile et tests dans deux navigateurs.


## 8. Livrables

- [x] `index.html` et `style.css`
- [x] Capture d'écran desktop
- [x] Capture d'écran mobile
- [x] Captures des deux navigateurs
- [x] Capture de la validation W3C
- [x] Cette note de documentation
