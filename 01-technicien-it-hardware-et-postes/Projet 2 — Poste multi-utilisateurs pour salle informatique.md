# Projet 2 — Poste multi-utilisateurs pour salle informatique


## 1. Objectif

Configurer un poste Windows 11 Pro partagé dans une salle informatique : un compte administrateur pour la maintenance, des comptes étudiants standards cloisonnés, une politique de mot de passe et de verrouillage, et un verrouillage automatique de la session.

## 2. Étape 1 : créer la VM et installer Windows 11 Pro

### 2.1 Création de la VM

Pour commencer, j'ai créé une nouvelle VM sous Windows et sélectionné le fichier ISO de Windows 11.

![](https://hackmd.io/_uploads/SJbO0Q1tzx.png)
![](https://hackmd.io/_uploads/HkVZgQSKzg.png)
![](https://hackmd.io/_uploads/S1FmxQHYGl.png)

J'enregistre ensuite ma VM sur mon bureau.

![](https://hackmd.io/_uploads/rJ8UlXSFze.png)

Je choisis « Only the files needed to support a TPM are encrypted » pour ne pas avoir à entrer mon mot de passe partout. Je configure bien sûr un mot de passe.

![](https://hackmd.io/_uploads/SJOnemrFMl.png)

Je choisis la capacité de stockage, je configure le hardware, puis je clique sur Finish pour créer la VM.

![](https://hackmd.io/_uploads/S1vKWmBKze.png)
![](https://hackmd.io/_uploads/S1jT-QBtGg.png)
![](https://hackmd.io/_uploads/S11-4mrYfe.png)

### 2.2 Installation de Windows

Je choisis « EFI VMware virtual SATA CDROM Drive » pour installer la bonne version de Windows, puis je configure Windows.

![](https://hackmd.io/_uploads/HyLcP7SYMx.png)
![](https://hackmd.io/_uploads/Bkvz_7rFfe.png)
![](https://hackmd.io/_uploads/B12Y_mSYGl.png)

Comme je ne dispose pas de clé de produit, je clique sur « Je n'ai pas de clé de produit », puis je choisis Windows Pro.

![](https://hackmd.io/_uploads/BySc_XrKfl.png)
![](https://hackmd.io/_uploads/S1tAumBYfg.png)

Pendant l'installation, Windows me demande de me connecter avec une adresse mail. Je clique donc sur « Options de connexion ». Je nomme ensuite l'appareil et je crée un mot de passe.

![](https://hackmd.io/_uploads/HyzYaXSYfg.png)
![](https://hackmd.io/_uploads/BJwpuEBtMg.png)
![](https://hackmd.io/_uploads/BkilKEBtfg.png)

## 3. Étape 2 : créer les comptes utilisateurs

Une fois sur Windows, je me rends dans le panneau de configuration, puis dans « Comptes d'utilisateurs ».

![](https://hackmd.io/_uploads/r1zR2vUFfl.png)
![](https://hackmd.io/_uploads/rymG6DLtMl.png)

Je clique sur « Gérer un autre compte », puis sur le lien en bas de la page pour ajouter des utilisateurs.

![](https://hackmd.io/_uploads/BylQCDIKfx.png)
![](https://hackmd.io/_uploads/BJDLH_ItMx.png)

J'arrive dans les paramètres, où je peux ajouter tous mes utilisateurs.

![](https://hackmd.io/_uploads/S1mxodLtfx.png)

Pour chaque utilisateur, je clique sur « Je ne dispose pas des informations de connexion de cette personne », puis sur « Ajouter un utilisateur sans compte Microsoft ».

![](https://hackmd.io/_uploads/BygXo_8KGg.png)
![](https://hackmd.io/_uploads/ryu8iOIYfl.png)

Je répète ce processus pour tous les utilisateurs. Voici le résultat :

![](https://hackmd.io/_uploads/BJHzbF8tGe.png)

## 4. Étape 3 : verrouillage automatique de la session

J'ouvre l'éditeur de stratégie de groupe avec `Windows + R`, puis la commande `gpedit.msc`.

![](https://hackmd.io/_uploads/H1esfYLtze.png)

Je vais dans `Configuration utilisateur > Modèles d'administration > Panneau de configuration > Personnalisation`.

![](https://hackmd.io/_uploads/H1urlTUYzx.png)
![](https://hackmd.io/_uploads/rkttlaLYfl.png)
![](https://hackmd.io/_uploads/HJaqx6LFfx.png)
![](https://hackmd.io/_uploads/B1SaxpUYGl.png)

J'active les options « Activer l'écran de veille » et « Protéger l'écran de veille avec un mot de passe ».

![](https://hackmd.io/_uploads/BkZt-W6UtGe.png)
![](https://hackmd.io/_uploads/H1rcZaItMx.png)

Dans l'option « Dépassement du délai d'expiration de l'écran de veille », je règle le délai sur 300 secondes.

![](https://hackmd.io/_uploads/SJPcVgvtzx.png)

## 5. Étape 4 : politique de mot de passe et de verrouillage du compte

Je vais dans `Configuration ordinateur > Paramètres Windows > Paramètres de sécurité > Stratégies de comptes`.

![](https://hackmd.io/_uploads/ry2Nz6IFfe.png)
![](https://hackmd.io/_uploads/BycIM6UKzg.png)
![](https://hackmd.io/_uploads/SJ8OM68YMl.png)

### 5.1 Stratégie de mot de passe

![](https://hackmd.io/_uploads/HyU9GaLYGe.png)

Voici les modifications que j'ai faites :

![](https://hackmd.io/_uploads/HkIjmaLYMg.png)

### 5.2 Stratégie de verrouillage du compte

Je retourne dans « Stratégies de comptes » et je clique sur « Stratégie de verrouillage du compte ». On peut observer les valeurs que j'ai modifiées.

![](https://hackmd.io/_uploads/SkHEEaIYzx.png)

## 6. Explication des réglages

| Réglage | Emplacement | Effet |
|---|---|---|
| Comptes sans compte Microsoft | Paramètres > Comptes | Comptes locaux pour chaque étudiant |
| Écran de veille protégé par mot de passe | `gpedit.msc` > Configuration utilisateur > Personnalisation | La session se verrouille quand l'écran de veille se lance |
| Délai de 300 secondes | Même emplacement | Verrouillage après 5 minutes d'inactivité |
| Stratégie de mot de passe | `gpedit.msc` > Configuration ordinateur > Stratégies de comptes | Impose des mots de passe qui respectent des critères |
| Stratégie de verrouillage du compte | Même emplacement | Bloque le compte après des tentatives de connexion ratées |

## 7. Test et résultat

### 7.1 Cloisonnement NTFS

Je me connecte sur le compte Étudiant 2.

![](https://hackmd.io/_uploads/By9dtTIKMx.png)

J'essaie d'accéder aux fichiers de l'Étudiant 1, mais cela ne fonctionne pas. C'est la preuve que le cloisonnement NTFS fonctionne bien entre les comptes étudiants.

![](https://hackmd.io/_uploads/HkMQKaIFMx.png)

### 7.2 Politique de mot de passe

J'appuie sur `Ctrl + Alt + Suppr`, puis je clique sur « Modifier un mot de passe ».

![](https://hackmd.io/_uploads/rJFqMlDKMg.png)

J'essaie de mettre un mot de passe très simple : il n'est pas accepté, car il ne répond pas aux critères.

![](https://hackmd.io/_uploads/Sy6nflvFMe.png)

| Test | Résultat attendu | Résultat obtenu |
|---|---|---|
| Étudiant 2 ouvre les fichiers de l'Étudiant 1 | Accès refusé | ✅ Accès refusé |
| Mot de passe trop simple | Refusé | ✅ Refusé |

## 8. Conclusion

Le poste a été configuré conformément aux objectifs du projet : un compte administrateur dédié à la maintenance, trois comptes étudiants standards cloisonnés via les permissions NTFS natives de Windows, une politique de mot de passe et de verrouillage de compte, ainsi qu'un verrouillage automatique de session après inactivité. Les tests de cloisonnement et de politique de mot de passe confirment le bon fonctionnement de la configuration.
