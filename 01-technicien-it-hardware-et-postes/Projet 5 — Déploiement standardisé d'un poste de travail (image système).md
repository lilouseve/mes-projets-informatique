# Projet 5 — Déploiement standardisé d'un poste de travail (image système)


## 1. Objectif

Préparer un poste de référence Windows 11 Pro, avec ses comptes utilisateurs, pour pouvoir ensuite le déployer de façon standardisée à partir d'une image système.

## 2. Cahier des charges du poste standard

## 3. Étape 1 : créer le poste de référence

### 3.1 Création de la VM

Pour commencer, j'ai créé une nouvelle VM sous Windows et sélectionné le fichier ISO de Windows 11.

![Capture d'écran 2026-09-09 210551](https://hackmd.io/_uploads/SJbO0Q1tzx.png)
![Capture d'écran 2026-09-14 090853](https://hackmd.io/_uploads/HkVZgQSKzg.png)
![Capture d'écran 2026-09-14 090906](https://hackmd.io/_uploads/S1FmxQHYGl.png)

J'enregistre ensuite ma VM sur mon bureau.

![Capture d'écran 2026-09-14 091033](https://hackmd.io/_uploads/rJ8UlXSFze.png)

Je choisis « Only the files needed to support a TPM are encrypted » pour ne pas avoir à entrer mon mot de passe partout. Je configure bien sûr un mot de passe.

![Capture d'écran 2026-09-14 091135](https://hackmd.io/_uploads/SJOnemrFMl.png)

Je choisis la capacité de stockage, je configure le hardware, puis je clique sur Finish pour créer la VM.

![Capture d'écran 2026-09-14 091145](https://hackmd.io/_uploads/S1vKWmBKze.png)
![Capture d'écran 2026-09-14 091217](https://hackmd.io/_uploads/S1jT-QBtGg.png)
![Capture d'écran 2026-09-14 091328](https://hackmd.io/_uploads/S11-4mrYfe.png)

### 3.2 Installation de Windows 11 Pro

Je choisis « EFI VMware virtual SATA CDROM Drive » pour installer la bonne version de Windows, puis je configure Windows.

![Capture d'écran 2026-09-14 093805](https://hackmd.io/_uploads/HyLcP7SYMx.png)
![Capture d'écran 2026-09-14 094307](https://hackmd.io/_uploads/Bkvz_7rFfe.png)
![Capture d'écran 2026-09-14 095420](https://hackmd.io/_uploads/B12Y_mSYGl.png)

Comme je ne dispose pas de clé de produit, je clique sur « Je n'ai pas de clé de produit », puis je choisis Windows Pro.

![Capture d'écran 2026-09-14 095431](https://hackmd.io/_uploads/BySc_XrKfl.png)
![Capture d'écran 2026-09-14 095520](https://hackmd.io/_uploads/S1tAumBYfg.png)

Pendant l'installation, Windows me demande de me connecter avec une adresse mail. Je clique donc sur « Options de connexion ». Je nomme ensuite l'appareil et je crée un mot de passe.

![image](https://hackmd.io/_uploads/HyzYaXSYfg.png)
![Capture d'écran 2026-09-14 102853](https://hackmd.io/_uploads/BJwpuEBtMg.png)
![Capture d'écran 2026-09-14 102903](https://hackmd.io/_uploads/BkilKEBtfg.png)

## 4. Étape 2 : créer les comptes utilisateurs

Une fois sur le bureau de Windows, je me rends dans les paramètres, onglet « Comptes », pour configurer les utilisateurs.

![image](https://hackmd.io/_uploads/HJfOdztFzg.png)

Je clique sur « Autres utilisateurs », puis « Ajouter un autre utilisateur ».

![Capture d'écran 2026-09-17 093638](https://hackmd.io/_uploads/BJZTdMYtGl.png)
![image](https://hackmd.io/_uploads/rJe7aufFYfx.png)

Je clique sur « Je ne dispose pas des informations de connexion de cette personne », puis sur « Ajouter un utilisateur sans compte Microsoft ».

![Capture d'écran 2026-09-17 093921](https://hackmd.io/_uploads/ByI-5ztFzx.png)
![Capture d'écran 2026-09-17 093949](https://hackmd.io/_uploads/SkmE3fYYfx.png)

Une fois mon compte admin créé, je vérifie qu'il a bien les droits administrateur.

![Capture d'écran 2026-09-17 094105](https://hackmd.io/_uploads/rkh_nzFYGl.png)

Je fais la même démarche pour les autres utilisateurs.

![image](https://hackmd.io/_uploads/B1T0YQYtfl.png)

## 5. Test et résultat

| Vérification | Résultat |
|---|---|
| Windows 11 Pro installé sur le poste de référence | ✅ |
| Compte administrateur avec droits administrateur | ✅ |
| Autres comptes utilisateurs créés | ✅ |
