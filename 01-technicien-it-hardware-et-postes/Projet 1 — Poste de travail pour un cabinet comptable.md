# Projet 1 — Poste de travail pour un cabinet comptable


## 1. Objectif

Préparer un poste de travail Windows 11 Pro pour un cabinet comptable, dans une machine virtuelle VMware Workstation : installation du système, compte utilisateur standard, réseau, Office 365, imprimante, mises à jour et sécurité.

## 2. Étape 1 : créer la machine virtuelle

### 2.1 Création de la VM et choix de l'ISO

Pour commencer, j'ai créé une nouvelle VM sous Windows.

![Capture d'écran 2026-09-09 210551](https://hackmd.io/_uploads/SJbO0Q1tzx.png)

Je sélectionne le fichier ISO de Windows 11.

![Capture d'écran 2026-09-14 090853](https://hackmd.io/_uploads/HkVZgQSKzg.png)
![Capture d'écran 2026-09-14 090906](https://hackmd.io/_uploads/S1FmxQHYGl.png)

J'enregistre ensuite ma VM sur mon bureau.

![Capture d'écran 2026-09-14 091033](https://hackmd.io/_uploads/rJ8UlXSFze.png)

### 2.2 Chiffrement et stockage

Je choisis « Only the files needed to support a TPM are encrypted » pour ne pas avoir à entrer mon mot de passe partout. Je configure bien sûr un mot de passe.

![Capture d'écran 2026-09-14 091135](https://hackmd.io/_uploads/SJOnemrFMl.png)

Je choisis la capacité de stockage.

![Capture d'écran 2026-09-14 091145](https://hackmd.io/_uploads/S1vKWmBKze.png)

### 2.3 Matériel de la VM

Je configure le hardware, puis je clique sur Finish pour créer la VM.

![Capture d'écran 2026-09-14 091217](https://hackmd.io/_uploads/S1jT-QBtGg.png)
![Capture d'écran 2026-09-14 091328](https://hackmd.io/_uploads/S11-4mrYfe.png)

## 3. Étape 2 : installer Windows 11 Pro

### 3.1 Démarrage sur l'ISO

Je choisis « EFI VMware virtual SATA CDROM Drive » pour installer la bonne version de Windows.

![Capture d'écran 2026-09-14 093805](https://hackmd.io/_uploads/HyLcP7SYMx.png)

Il suffit ensuite de configurer Windows.

![Capture d'écran 2026-09-14 094307](https://hackmd.io/_uploads/Bkvz_7rFfe.png)
![Capture d'écran 2026-09-14 095420](https://hackmd.io/_uploads/B12Y_mSYGl.png)

### 3.2 Clé de produit et édition

Comme je ne dispose pas de clé de produit, je clique sur « Je n'ai pas de clé de produit », puis je choisis Windows 11 Pro.

![Capture d'écran 2026-09-14 095431](https://hackmd.io/_uploads/BySc_XrKfl.png)
![Capture d'écran 2026-09-14 095520](https://hackmd.io/_uploads/S1tAumBYfg.png)

### 3.3 Compte local

Pendant l'installation, Windows me demande de me connecter avec une adresse mail. Je clique donc sur « Options de connexion ».

![image](https://hackmd.io/_uploads/HyzYaXSYfg.png)

Je nomme ensuite l'appareil et je crée un mot de passe.

![Capture d'écran 2026-09-14 102853](https://hackmd.io/_uploads/BJwpuEBtMg.png)
![Capture d'écran 2026-09-14 102903](https://hackmd.io/_uploads/BkilKEBtfg.png)

## 4. Étape 3 : créer un compte utilisateur standard

Windows a fini l'installation. Je crée maintenant un compte utilisateur sans droits administrateur.

Je me rends dans `Paramètres > Comptes > Autres utilisateurs`, puis j'ajoute un compte.

![image](https://hackmd.io/_uploads/Bk6o4IrFMe.png)
![image](https://hackmd.io/_uploads/S1XaN8SFGl.png)

Je clique sur « Je ne dispose pas des informations de connexion de cet utilisateur », puis sur « Ajouter un utilisateur sans compte Microsoft ».

![image](https://hackmd.io/_uploads/ByWZrIrKGg.png)
![image](https://hackmd.io/_uploads/Hy5EBIHtMx.png)

Je rentre un pseudo et un mot de passe.

![image](https://hackmd.io/_uploads/ByOKrLrKfl.png)

Une fois le deuxième compte créé, je vérifie qu'il est bien en « Utilisateur standard ».

![image](https://hackmd.io/_uploads/BJCX8ISFfg.png)

## 5. Étape 4 : réseau et nom du poste

Dans le terminal, je tape la commande `ipconfig` pour vérifier que mon système est bien connecté au réseau.

![image](https://hackmd.io/_uploads/S1ZSwLStMl.png)

Je tape ensuite la commande `sysdm.cpl`, qui affiche les propriétés du système et permet de renommer l'ordinateur.

![image](https://hackmd.io/_uploads/H1NLuLBKfe.png)

## 6. Étape 5 : installer Office 365

Je récupère le fichier d'installation d'Office 365 sur Internet, je le mets sur le bureau et je lance l'installation.

![Capture d'écran 2026-09-14 135836](https://hackmd.io/_uploads/rJ224PHYfl.png)
![Capture d'écran 2026-09-14 140031](https://hackmd.io/_uploads/Hy00NwBYMx.png)
![Capture d'écran 2026-09-14 140324](https://hackmd.io/_uploads/r1N1rwrtzx.png)

## 7. Étape 6 : configurer l'imprimante

Je me rends dans `Paramètres > Bluetooth et appareils > Imprimantes et scanners`.

![Capture d'écran 2026-09-14 141549](https://hackmd.io/_uploads/rJQOmurKGe.png)

Je sélectionne l'imprimante « Microsoft Print to PDF », puis je modifie ses propriétés pour la renommer.

![Capture d'écran 2026-09-14 142248](https://hackmd.io/_uploads/rJ2I7OStMe.png)

## 8. Étape 7 : mises à jour et sécurité

Je reste dans les paramètres pour mettre à jour Windows.

![Capture d'écran 2026-09-14 151738](https://hackmd.io/_uploads/ByAmSdrFzx.png)
![Capture d'écran 2026-09-14 152236](https://hackmd.io/_uploads/H17EH_SFze.png)

Ensuite, je vais dans « Confidentialité et sécurité » pour vérifier l'antivirus et le pare-feu.

![Capture d'écran 2026-09-14 152347](https://hackmd.io/_uploads/r11FSurtMl.png)

## 9. Explication des réglages

| Réglage | Effet |
|---|---|
| Chiffrement TPM partiel | Seuls les fichiers liés au TPM sont chiffrés, pas besoin de saisir le mot de passe à chaque fois |
| Compte local | Installation sans compte Microsoft |
| Utilisateur standard | L'utilisateur ne peut pas modifier les réglages du système |
| `ipconfig` | Affiche l'adresse IP et la connexion réseau du poste |
| `sysdm.cpl` | Ouvre les propriétés système (nom de l'ordinateur) |

## 10. Test et résultat

| Vérification | Résultat |
|---|---|
| Compte utilisateur | Créé en « Utilisateur standard » |
| Réseau | Poste connecté (`ipconfig`) |
| Imprimante | Renommée, test d'impression effectué |
| Antivirus et pare-feu | Tout est activé |

![Capture d'écran 2026-09-14 142531](https://hackmd.io/_uploads/rJp6m_BFMe.png)
![Capture d'écran 2026-09-14 152356](https://hackmd.io/_uploads/Bk8FrdHYGl.png)

## 11. Conclusion

Le poste est prêt pour le cabinet comptable : Windows 11 Pro est installé, un compte utilisateur standard est créé, le poste est connecté au réseau, Office 365 et l'imprimante sont installés, et le système est à jour avec l'antivirus et le pare-feu activés.
