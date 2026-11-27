# TP Final — Épreuve Technicien IT

## 1. Objectif

Épreuve finale du module technicien IT : un questionnaire de 100 questions sur le hardware, puis trois cahiers des charges en situation professionnelle (configurations hardware, déploiement de Windows 10 Pro et d'Ubuntu, interconnexion des machines).

## 2. Partie 1 : questionnaire hardware (100 questions)

### 2.1 Composants de base

**1. Quel est le rôle du processeur (CPU) dans un ordinateur ?**
Le rôle du processeur est d'exécuter des instructions et de coordonner toutes les actions du système.

**2. Quelle est la fonction de la carte mère ?**
La carte mère permet à tous les composants de communiquer entre eux.

**3. Qu'est-ce que la RAM et pourquoi est-elle qualifiée de mémoire « volatile » ?**
La RAM stocke temporairement les données de l'ordinateur et elle est qualifiée de mémoire volatile car, quand on éteint le PC, son contenu disparaît.

**4. Quelle est la différence fonctionnelle entre la RAM et le stockage (HDD/SSD) ?**
La différence entre la RAM et le stockage, c’est que la RAM est temporaire et rapide, tandis que le stockage est permanent mais plus lent.

**5. Quel est le rôle du chipset sur une carte mère ?**
Le chipset permet les échanges entre le CPU, la RAM, etc.

**6. À quoi sert une carte graphique (GPU) dédiée par rapport à un GPU intégré ?**
Une carte graphique dédiée est plus puissante et sert pour les jeux, le montage vidéo, la 3D et toutes les tâches graphiques lourdes

**7. Qu'est-ce que le BIOS/UEFI et à quel moment intervient-il dans le démarrage d'un PC ?**
Le BIOS/UEFI démarre en tout premier quand on allume l’ordinateur et il permet le lancement du système d’exploitation.

**8. Quel est le rôle de l'alimentation (PSU) dans un ordinateur ?**

**9. À quoi sert un ventirad (dissipateur + ventilateur) sur un CPU ?**
Le ventirad sert à refroidir le CPU.

**10. Qu'est-ce qu'un facteur de forme (form factor) ? Citez-en deux exemples.**
Le facteur de forme est le type ou le format d’un composant. Exemples : ATX, Micro-ATX.

**11. Quel est le rôle des ports d'entrée/sortie (I/O) situés à l'arrière d'une carte mère ?**
Les ports d’entrée et de sortie servent à connecter un casque, une manette, un clavier, etc.

**12. Qu'est-ce qu'un firmware et en quoi diffère-t-il d'un logiciel applicatif ?**

### 2.2 Compatibilité des composants

**13. Qu'est-ce qu'un socket processeur et pourquoi doit-il correspondre entre CPU et carte mère ?**
Le socket est l’endroit où se fixe le CPU. Ils doivent correspondre sinon le CPU ne peut pas fonctionner correctement.

**14. Citez deux sockets Intel et deux sockets AMD actuels.**
Intel :
AMD : AM4, AM5

**15. Quelles générations de RAM sont couramment utilisées aujourd'hui et en quoi sont-elles incompatibles entre elles ?**
Les RAM utilisées aujourd’hui sont DDR4, DDR5, etc. Elles sont incompatibles car elles sont fabriquées de manière différente.

**16. Qu'est-ce que le TDP d'un processeur et pourquoi faut-il en tenir compte lors du choix du ventirad ?**

**17. Comment vérifier qu'une alimentation (PSU) est suffisante pour une configuration donnée ?**

**18. Quels éléments faut-il vérifier avant d'installer une carte graphique dans un boîtier (taille, connectique) ?**
Il faut vérifier l’espace disponible.

**19. En quoi consiste la compatibilité entre un boîtier et le facteur de forme d'une carte mère (ATX, mATX, Mini-ITX) ?**
Le boîtier doit avoir le même format que la carte mère.

**20. Pourquoi certains SSD M.2 ne sont-ils pas compatibles avec tous les slots M.2 d'une carte mère (NVMe vs SATA) ?**

**21. Qu'est-ce qu'un connecteur 24 broches et un connecteur 8 broches (EPS) sur une alimentation, et à quoi servent-ils ?**
Les 24 broches alimentent la carte mère et les 8 broches alimentent le CPU.

**22. Pourquoi est-il important de vérifier la compatibilité entre la fréquence de RAM annoncée et celle réellement supportée par la carte mère/le CPU ?**
Il est important de vérifier la compatibilité car si la RAM est trop puissante mais que la carte mère ou le CPU ne supportent pas cette puissance, il va y avoir une baisse de performance.

### 2.3 Alimentation

**23. Que signifie la certification 80 PLUS (Bronze, Gold, Platinum) sur une alimentation ?**

**24. Quelle est la différence entre une alimentation modulaire et non modulaire ?**
La différence entre une alimentation modulaire et non modulaire, c’est qu’avec une alimentation modulaire on peut détacher les câbles, contrairement à une alimentation non modulaire où les câbles ne sont pas détachables.

**25. Comment calcule-t-on approximativement la puissance nécessaire pour une configuration donnée ?**

**26. Qu'est-ce qu'un rail 12V sur une alimentation et pourquoi est-il important pour le GPU/CPU ?**

**27. Quels sont les risques d'une alimentation sous-dimensionnée par rapport aux besoins réels ?**
Les risques d’une alimentation sous-dimensionnée sont d’endommager les composants.

**28. À quoi sert le connecteur SATA d'alimentation ?**
Le connecteur SATA alimente le SSD/HDD.

**29. Quelle est la différence entre les watts « annoncés » et la puissance réellement stable délivrée par une alimentation bas de gamme ?**

**30. Pourquoi est-il déconseillé de réutiliser une très vieille alimentation sur un PC neuf performant ?**
Une vieille alimentation peut être instable, perdre en efficacité et ne plus fournir une puissance stable, ce qui peut endommager les composants

### 2.4 Refroidissement

**31. Quelle est la différence entre un refroidissement par air et un refroidissement liquide (watercooling) ?**
Un ventirad refroidit grâce à un ventilateur, contrairement à un watercooling qui refroidit grâce à un liquide qui passe dans un tuyau et utilise un radiateur.

**32. À quoi sert la pâte thermique et où doit-elle être appliquée ?**
La pâte thermique se pose sur le CPU et son but est d’améliorer le transfert de chaleur entre le CPU et le ventirad.

**33. Qu'est-ce qu'un watercooling AIO (All-In-One) ?**
Un watercooling AIO est déjà assemblé.

**34. Pourquoi le flux d'air (airflow) dans un boîtier est-il important pour les performances ?**
Le flux d’air est important car s’il n’y a pas assez d’air pour refroidir, les composants chauffent, ce qui fait que les performances seront moins bonnes.

**35. Quels sont les signes indiquant qu'un CPU ou un GPU surchauffe ?**
Les signes que le CPU ou le GPU surchauffe, c’est déjà s’ils dépassent 90 degrés. Il peut aussi y avoir des lags et des performances moins bonnes.

**36. Qu'est-ce que le throttling thermique ?**
Le throttling thermique, c’est la baisse de performances pour éviter que le PC surchauffe.

**37. Pourquoi faut-il dépoussiérer régulièrement un PC ?**
Il est important de dépoussiérer régulièrement son PC car sinon la poussière peut créer une surchauffe des composants, réduire les performances et parfois faire crasher le PC.

**38. Quel est le rôle des ventilateurs de boîtier (intake / exhaust) ?**
Les ventilateurs intake font entrer l’air frais dans le boîtier.
Les ventilateurs exhaust expulsent l’air chaud vers l’extérieur.

### 2.5 Stockage

**39. Quelle est la différence technique entre un disque dur HDD et un SSD ?**
Un disque HDD est mécanique et lent, tandis qu’un disque SSD est électronique et plus rapide.

**40. Qu'est-ce qu'un SSD NVMe et en quoi diffère-t-il d'un SSD SATA en termes de performance ?**

**41. Qu'est-ce que le format M.2 et à quoi correspond-il physiquement ?**

**42. Qu'est-ce que le RAID  ? Donnez un exemple d'utilité en entreprise.**
Le RAID, c’est un système qui utilise plusieurs disques soit pour la sécurité, soit pour les performances, parfois les deux.
Exemple : le RAID 0 est utilisé pour les performances.

**43. Quelle est la différence entre RAID 0 et RAID 1 ?**
RAID 0 est utilisé pour les performances mais n’a pas vraiment de sécurité.
RAID 1 est utilisé pour la sécurité et pour avoir une copie des données.

**44. Pourquoi un SSD est-il globalement plus fiable mécaniquement qu'un HDD ?**
Un SSD est plus fiable qu’un HDD car le SSD ne contient aucune pièce mécanique, contrairement au HDD.

**45. Qu'est-ce que la partition GPT et en quoi diffère-t-elle du MBR ?**

**46. Combien de partitions primaires maximum peut-on créer avec un schéma MBR, contre un schéma GPT ?**

**47. Qu'est-ce que le « TRIM » sur un SSD et à quoi sert-il ?**

**48. Pourquoi ne faut-il pas défragmenter un SSD comme on le ferait avec un HDD ?**

### 2.6 Connectique et ports

**49. Quelle est la différence entre un port USB-A et un port USB-C ?**
Un port USB-A est plus ancien et plus lent, alors qu’un port USB-C est plus récent et plus rapide.

**50. Que signifie USB 3.2 Gen 2 en termes de débit par rapport à USB 2.0 ?**
L’USB 3.2 est beaucoup plus rapide en termes de débit que l’USB 2.0.

**51. Quelle est la différence entre un port HDMI et un port DisplayPort ?**
Le DisplayPort est utile pour une utilisation sur un écran avec un grand débit, alors que l’HDMI classique s’utilise plutôt sur une télé ou sur un écran normal.

**52. Qu'est-ce qu'un port PCIe et à quoi sert-il principalement sur une carte mère ?**
Le port PCIe est un port d’extension pour le GPU, etc.

**53. Combien de broches comporte un connecteur SATA de données, et un connecteur SATA d'alimentation ?**
Un connecteur SATA de données comporte 7 broches et un connecteur SATA d’alimentation en comporte 15.

**54. Qu'est-ce qu'un port RJ45 et à quoi sert-il ?**
Un port RJ45 sert pour un câble Ethernet.

**55. Qu'est-ce que le Thunderbolt et quel est son avantage principal ?**

**56. À quoi sert un port Jack audio 3,5 mm sur une carte mère ?**
Un port jack audio sert à connecter un casque ou un micro.

**57. Qu'est-ce qu'un hub USB et dans quel cas l'utilise-t-on ?**
Un hub USB est un objet qui ajoute plusieurs entrées ou sorties, par exemple pour connecter plusieurs écrans ou son clavier, sa souris.

**58. Pourquoi certains périphériques nécessitent-ils une alimentation externe même reliés en USB ?**

### 2.7 Montage

**59. Quelles précautions faut-il prendre contre les décharges électrostatiques (ESD) avant de manipuler des composants ?**
Il faut bien vérifier que le PC a été mis hors tension.

**60. Dans quel ordre logique recommande-t-on de monter les composants dans un boîtier PC ?**

**61. Comment fixe-t-on physiquement un processeur sur une carte mère (socket à broches CPU vs socket à broches carte mère) ?**
Pour Intel, les broches sont sur la carte mère.
Pour AMD, les broches sont sur le CPU.

**62. Que faut-il vérifier avant de refermer le boîtier une fois le montage terminé ?**
Il faut vérifier que tous les câbles sont bien branchés, que tous les composants sont correctement installés et ne bougent plus, donc bien vissés.

**63. Comment installe-t-on correctement les barrettes de RAM (sens, slots recommandés en dual-channel) ?**
On vérifie qu’elles sont dans le bon sens et dans les bons slots.

**64. Quelles étapes suivre pour installer une alimentation (PSU) dans un boîtier ?**

**65. Comment fixe-t-on un SSD M.2 sur une carte mère ?**

**66. Quelles sont les étapes pour installer un ventirad CPU, application de la pâte thermique comprise ?**
On applique d’abord la pâte thermique, on pose ensuite le ventirad puis on branche le câble du ventilateur CPU.

**67. Comment gère-t-on le câblage (cable management) pour optimiser l'airflow et l'esthétique ?**
On essaye d’accrocher les câbles tous ensemble et de les cacher pour qu’ils se voient le moins possible et qu’ils ne dérangent pas le passage de l’air.

**68. Qu'est-ce qu'un « POST » et comment sait-on qu'un premier démarrage s'est bien déroulé ?**
Un POST, c’est un test quand on démarre un PC pour contrôler si tout est correct. Si le BIOS s’affiche, c’est que tout est correct.

**69. Que faire si le PC ne démarre pas après le premier montage (démarche de diagnostic) ?**
On vérifie les câbles, on vérifie que tous les composants sont au bon endroit et correctement installés.

**70. Pourquoi faut-il visser la carte mère sur des entretoises (standoffs) et non directement sur le boîtier ?**

### 2.8 PC portable

**71. Quelles sont les principales différences entre le démontage d'un PC fixe et celui d'un PC portable ?**
Pour démonter un PC portable, c’est beaucoup plus compliqué car les composants sont souvent soudés et beaucoup plus fragiles.
Contrairement au PC fixe où les composants sont démontables, moins fragiles et beaucoup plus grands.

**72. Comment accède-t-on généralement à la RAM et au SSD d'un ordinateur portable ?**
On enlève le capot de l’ordinateur, ce qui donne accès aux composants du PC.

**73. Pourquoi la plupart des composants d'un PC portable (CPU, GPU) ne sont-ils pas remplaçables comme sur un PC fixe ?**
Car ils sont soudés et c’est presque impossible de les remplacer.

**74. Quelles précautions particulières faut-il prendre avec la batterie lors du démontage d'un PC portable ?**
Il faut vérifier que la batterie est hors tension, sinon cela peut être dangereux.

**75. Comment identifie-t-on le type de RAM (SO-DIMM) et le type de SSD (M.2 ou 2,5") utilisés sur un PC portable ?**

**76. Que faut-il vérifier avant de commander une pièce de remplacement pour un PC portable ?**
Il faut vérifier que c’est le bon modèle, ni trop petit ni trop grand, et que le composant soit compatible.

**77. Pourquoi le nettoyage du système de refroidissement est-il particulièrement important sur un PC portable ?**
Il est très important de nettoyer régulièrement le système de refroidissement car sur un PC portable les ventilateurs sont beaucoup plus petits, donc ils peuvent s’encrasser plus vite. Sachant qu’un PC portable chauffe davantage qu’un PC fixe, il peut chauffer encore plus et cela peut réduire les capacités des composants.

**78. Quels outils spécifiques sont généralement nécessaires pour ouvrir un PC portable, par rapport à un PC fixe ?**
Il faut utiliser des outils assez petits comme par exemple un tournevis ou une pince.

### 2.9 BIOS / UEFI

**79. Que signifie l'acronyme UEFI et en quoi diffère-t-il du BIOS « Legacy » ?**
L’UEFI signifie Unified Extensible Firmware Interface.
L’UEFI est plus récent et plus avancé que le BIOS. Il permet d’utiliser le partitionnement GPT et offre plus de réglages, alors que le BIOS est plus ancien et plus limité.

**80. Comment accède-t-on au BIOS/UEFI au démarrage d'un ordinateur ?**
Au démarrage d’un ordinateur, il suffit d’appuyer sur la touche F2 pour ma part, mais sur certains types d’ordinateurs la touche peut être F10, etc.

**81. À quoi sert le réglage de l'ordre de démarrage (boot order) dans le BIOS/UEFI ?**

**82. Qu'est-ce que le Secure Boot et pourquoi est-il requis par certains systèmes d'exploitation récents ?**
Le Secure Boot vérifie que Windows démarre avec des fichiers sûrs et non modifiés.
Il est requis par les systèmes comme Windows 11 pour empêcher les virus de se lancer au démarrage.

**83. Qu'est-ce que le TPM (Trusted Platform Module) et quel est son rôle ?**

**84. Que réinitialise une opération de Clear CMOS (reset BIOS) ?**
Le Clear CMOS réinitialise le BIOS et remet tous les paramètres comme ils étaient lorsque l’ordinateur a été acheté.

**85. À quoi sert un mot de passe superviseur (supervisor password) dans le BIOS/UEFI ?**
Un mot de passe sert à protéger l’accès au BIOS et à empêcher n’importe qui d’y entrer.

**86. Comment active-t-on le profil XMP/DOCP de la RAM dans le BIOS/UEFI, et à quoi sert-il ?**

### 2.10 Diagnostic de pannes

**87. Un PC ne s'allume plus du tout (aucun ventilateur, aucune LED) : quelles sont les premières vérifications à effectuer ?**
Il faut d’abord vérifier que les câbles sont bien branchés et qu’ils ne sont pas défectueux.

**88. Un PC démarre mais n'affiche rien à l'écran : quelles causes matérielles possibles faut-il envisager ?**
Il faut vérifier que les câbles reliés à l’écran sont correctement branchés et qu’ils ne sont pas défectueux. On peut ensuite regarder si ce n’est pas le GPU qui a un problème.

**89. Comment diagnostiquer une panne de RAM (symptômes, méthode de test) ?**

**90. Le PC redémarre seul de façon aléatoire : quelles pistes matérielles explorer (alimentation, température) ?**
Si un PC redémarre seul de façon aléatoire, il faut vérifier l’alimentation, la température, les branchements, et parfois la RAM ou le GPU.

**91. Comment vérifier si un problème provient de la carte graphique plutôt que d'un autre composant ?**

**92. Un disque n'est pas détecté par le BIOS/UEFI : quelles vérifications effectuer ?**
Il faut vérifier la compatibilité et les branchements.

**93. Que signifient généralement les bips émis par certaines cartes mères au démarrage (beep codes) ?**
Les bips indiquent qu’il y a un problème de montage dans le PC. Cela peut être lié aux RAM, aux câbles, au CPU ou au GPU.

**94. Comment procéder par élimination pour isoler un composant défectueux sur une configuration qui ne démarre pas ?**

### 2.11 Sécurité et bonnes pratiques

**95. Pourquoi faut-il débrancher l'alimentation électrique avant d'intervenir à l'intérieur d'un PC ?**
Il faut impérativement débrancher un PC avant de le démonter car on pourrait se prendre une décharge électrique.

**96. Quels outils de base doit posséder un technicien pour un montage/démontage PC ?**
Un technicien doit posséder des tournevis, des pinces et un bracelet antistatique.

**97. Pourquoi ne faut-il jamais forcer l'insertion d'un composant (RAM, carte, connecteur) ?**
Il ne faut jamais forcer l’insertion d’un composant dans un PC car on risquerait de le casser.

**98. Qu'est-ce qu'un bracelet antistatique et comment doit-il être utilisé correctement ?**
Un bracelet antistatique est fait pour éviter les décharges électrostatiques.

**99. Pourquoi est-il recommandé de manipuler les composants par les bords et d'éviter de toucher les contacts dorés/broches ?**
Car les composants peuvent s’abîmer si on touche directement les broches, car c’est un endroit extrêmement fragile.

**100. Pourquoi la documentation (photos, notes) est-elle une bonne pratique professionnelle lors d'une intervention matérielle ?**
Documenter tout ce qu’on fait permet d’avoir une trace de ce qui a été réalisé.

## 3. Partie 2 : cahiers des charges (mise en situation professionnelle)

### 3.1 Cahier des charges 1 : conception de configurations hardware

#### Profil 1 — PC Gamer

**1.1 Fiche de configuration**

| Categorie | Marque / Modele | Prix (CHF) |
|---|---|---|
| Processeur (CPU) | AMD Ryzen 5 7600 (AM5, 6c/12t, 3.8-5.1 GHz) | 269.- |
| Carte mere | Gigabyte B650 EAGLE AX (AM5, B650, ATX, DDR5) | 107.- |
| Memoire vive (RAM) | Corsair Vengeance 32 Go (2x16 Go) DDR5-6000 CL30 | 105.- |
| Carte graphique (GPU) | Sapphire PULSE AMD Radeon RX 9060 XT 16 Go | 540.- |
| Stockage (SSD) | Samsung 990 EVO Plus 1 To NVMe PCIe 4.0 | 80.- |
| Alimentation (PSU) | Corsair RM650e 650W - 80 PLUS Gold | 79.- |
| Boitier | Corsair 4000D Airflow (ATX, facade mesh, 2 ventilateurs inclus) | 100.- |
| Refroidissement CPU | be quiet! Pure Rock 2 (tour air 120mm) | 40.- |
| Ventilateurs additionnels | 2x be quiet! Pure Wings 3 120mm | 30.- |
| TOTAL | | 1350.- |

**1.2 Verification de compatibilite**

| Point de controle | Verification |
|---|---|
| Socket CPU / carte mere | Ryzen 5 7600 et Gigabyte B650 EAGLE AX sont tous deux au format AM5, donc compatibles |
| Type de RAM | La plateforme AM5 ne supporte que la DDR5. La carte mere B650 accepte la DDR5 jusqu'a 192 Go, donc Corsair Vengeance DDR5-6000 compatible |
| Format boitier / alimentation | Corsair 4000D Airflow est un boitier ATX, compatible avec la carte mere ATX et une alimentation ATX |
| TDP CPU vs puissance PSU | TDP CPU 65W + GPU ~160W + reste du systeme ~55-75W = environ 280-300W. L'alimentation de 650W offre une marge confortable |

**1.3 Respect du budget**

Budget indique : 1500.-
Tolerance : 1350.- a 1650.-
Total : 1350.-
Budget respecte.

#### Profil 2 — PC Administration

**2.1 Fiche de configuration**

| Categorie | Marque / Modele | Prix (CHF) |
|---|---|---|
| Processeur | AMD Ryzen 5 8500G | 132.- |
| Carte mere | ASUS Prime A620M-A-CSM | 70.- |
| RAM | Kingston Fury Beast 32 Go DDR5-5200 | 105.- |
| SSD | Crucial P3 Plus 1 To NVMe | 75.- |
| HDD | WD Blue 1 To 7200 rpm | 45.- |
| Boitier | Intertech H-606 mATX | 42.- |
| Alimentation | be quiet! System Power 10 450W | 49.- |
| Refroidissement CPU | be quiet! Pure Rock Slim 2 | 30.- |
| TOTAL | | 548.- |

**2.2 Verification de compatibilite**

| Point de controle | Verification |
|---|---|
| Socket CPU / carte mere | AM5 compatible |
| Type de RAM | DDR5 compatible |
| Format boitier | mATX compatible |
| TDP vs PSU | Consommation totale ~120W, PSU 450W largement suffisant |

**2.3 Respect du budget**

Budget : 600.-
Tolerance : 540.- a 660.-
Total : 548.-
Budget respecte.

#### Profil 3 — PC Étudiant

**3.1 Fiche de configuration**

| Categorie | Marque / Modele | Prix (CHF) |
|---|---|---|
| Processeur | AMD Ryzen 7 8700G | 299.- |
| Carte mere | Gigabyte B650 EAGLE AX | 107.- |
| RAM | G.Skill Flare X5 32 Go DDR5-6000 | 116.- |
| SSD | Crucial P3 Plus 2 To NVMe | 140.- |
| Alimentation | be quiet! System Power 10 550W | 55.- |
| Boitier | Deepcool CG530 | 68.- |
| Refroidissement CPU | be quiet! Pure Rock 2 | 40.- |
| TOTAL | | 825.- |

**3.2 Verification de compatibilite**

| Point de controle | Verification |
|---|---|
| Socket CPU / carte mere | AM5 compatible |
| Type de RAM | DDR5 compatible |
| Format boitier | ATX compatible |
| TDP vs PSU | Consommation ~120W, PSU 550W suffisant |

**3.3 Respect du budget**

Budget : 900.-
Tolerance : 810.- a 990.-
Total : 825.-
Budget respecte.

### 3.2 Cahier des charges 2 : déploiement des systèmes d'exploitation

#### Partie A — Windows 10 Pro

Pour la première étape, je me rends sur Internet pour télécharger le fichier ISO de Windows 10.
![Capture d'écran 2026-09-12 134852](https://hackmd.io/_uploads/S1ZpnnMtzx.png)
![Capture d'écran 2026-09-12 134908](https://hackmd.io/_uploads/ryey6hfFMe.png)

Je commence ensuite l'installation et choisis l’option "Créer un support d'installation", car je veux obtenir un fichier ISO pour créer ma VM.
![Capture d'écran 2026-09-12 134244](https://hackmd.io/_uploads/HkSxp2MKzg.png)

Je sélectionne "Fichier ISO" et l'installation débute.
![Capture d'écran 2026-09-12 134311](https://hackmd.io/_uploads/H1_8ahGFMe.png)
![Capture d'écran 2026-09-12 134353](https://hackmd.io/_uploads/rJa8phfFMl.png)

On peut voir que mon fichier a bien été créé.
![Capture d'écran 2026-09-12 135801](https://hackmd.io/_uploads/BJTU0hzKMe.png)

Je vais ensuite dans VMware pour créer une nouvelle VM avec Windows 10.
![image](https://hackmd.io/_uploads/HJp90nMtfx.png)
![Capture d'écran 2026-09-12 140000](https://hackmd.io/_uploads/rkV0A2fFMx.png)

Je choisis l’option "Installer disc image file (iso)" et je sélectionne mon fichier ISO Windows 10.
![image](https://hackmd.io/_uploads/BJokkazKGl.png)

Je renomme ma VM et l’enregistre sur mon bureau.
![image](https://hackmd.io/_uploads/Syh8Jpztze.png)

Je fais ensuite tous les réglages nécessaires.
![image](https://hackmd.io/_uploads/S1ka1TGKGe.png)

Une fois les modifications effectuées, je peux commencer l'installation de ma VM.
![image](https://hackmd.io/_uploads/HkV-gpGKfg.png)

Je configure ensuite Windows.
![Capture d'écran 2026-09-12 140945](https://hackmd.io/_uploads/rJZXWaftfe.png)

Je sélectionne Windows 10 Pro.
![image](https://hackmd.io/_uploads/ryoU-6MYfx.png)

Je choisis l'installation personnalisée pour éviter les applications inutiles.
![image](https://hackmd.io/_uploads/B1A5-TMtMe.png)
![image](https://hackmd.io/_uploads/SJ5jWaGKGx.png)

Windows est enfin installé.
![Capture d'écran 2026-09-12 143211](https://hackmd.io/_uploads/SkQbt6GFfe.png)

Je me rends ensuite dans les paramètres pour vérifier que le fuseau horaire est correct.
![image](https://hackmd.io/_uploads/r1Poj6MFGe.png)

Je fais la même chose pour le clavier.
![image](https://hackmd.io/_uploads/H1xZnTztMe.png)

Ensuite, je cherche l'adresse IP de ma VM.
![Capture d'écran 2026-09-12 145900](https://hackmd.io/_uploads/Hk41pTfFMx.png)

Puis je vérifie qu’elle est bien connectée.
![image](https://hackmd.io/_uploads/rybepaMYfe.png)

Je me dirige ensuite dans les paramètres pour effectuer les mises à jour nécessaires.
![image](https://hackmd.io/_uploads/Hk8qpTzFGl.png)
![Capture d'écran 2026-09-12 150421](https://hackmd.io/_uploads/H18WbyXKzx.png)

Windows 10 a atteint sa fin de support (14 octobre 2025), ce qui explique l’absence de nouvelles mises à jour.
![Capture d'écran 2026-09-12 162812](https://hackmd.io/_uploads/ryeTZkQYze.png)

Pour la prochaine étape, je me rends dans le gestionnaire des tâches, puis dans l’onglet "Démarrage", et je vérifie qu’il n’y a pas d’applications inutiles.
![image](https://hackmd.io/_uploads/HJGhMk7FGx.png)

Je vais ensuite dans le panneau de configuration et je clique sur "Matériel et audio".
![Capture d'écran 2026-09-12 163354](https://hackmd.io/_uploads/SJmvmJmYMg.png)

J’accède aux paramètres "Options d’alimentation".
![Capture d'écran 2026-09-12 163800](https://hackmd.io/_uploads/B1p071XKzx.png)

Puis je vérifie que le mode "Équilibré" est activé.
![Capture d'écran 2026-09-12 163559](https://hackmd.io/_uploads/H1RbEkmtGg.png)

Pour vérifier que les paramètres de sécurité sont activés, je me rends dans "Paramètres", puis "Mises à jour et sécurité".
![Capture d'écran 2026-09-12 164111](https://hackmd.io/_uploads/SJRfSkQKze.png)

Tout est en règle, aucune action supplémentaire n’est requise.
![Capture d'écran 2026-09-12 164130](https://hackmd.io/_uploads/HJEXBkXFMe.png)

La prochaine étape est de lancer cleanmgr.
Je fais Windows + R puis je tape cleanmgr.
![Capture d'écran 2026-09-12 164539](https://hackmd.io/_uploads/HkcO8yXtfl.png)

Je sélectionne ensuite les fichiers inutiles à supprimer.
![Capture d'écran 2026-09-12 164609](https://hackmd.io/_uploads/HyDEuJ7tzl.png)
![Capture d'écran 2026-09-12 164849](https://hackmd.io/_uploads/Hkp2O1Xtfl.png)
![Capture d'écran 2026-09-12 164859](https://hackmd.io/_uploads/S1Da_1XtMx.png)

Je fais la même manipulation pour vérifier que mon système est sécurisé.
![Capture d'écran 2026-09-12 170125](https://hackmd.io/_uploads/H1yOt1XYfx.png)

On peut voir qu’il n’est pas sécurisé, donc je vais le configurer.
![Capture d'écran 2026-09-12 170149](https://hackmd.io/_uploads/rJVcFymKfg.png)

Je coche l’option "Activer la protection du système".
![image](https://hackmd.io/_uploads/H1vy51XFfe.png)

On observe maintenant que mon système est bien sécurisé.
![image](https://hackmd.io/_uploads/Bye45k7Fzx.png)

J’en profite aussi pour renommer mon appareil.
![Capture d'écran 2026-09-12 171601](https://hackmd.io/_uploads/SkZf01QKfl.png)

Pour la suite, je fais Windows + R et je tape winver.
![Capture d'écran 2026-09-12 170637](https://hackmd.io/_uploads/HJ7aq17YMg.png)

Cela affiche la version de Windows installée.
![Capture d'écran 2026-09-12 170647](https://hackmd.io/_uploads/S13pcJXYfe.png)

Pour la dernière étape, je fais Windows + R et je tape sysdm.cpl.
![Capture d'écran 2026-09-12 172527](https://hackmd.io/_uploads/Byk8ygXtfx.png)

On peut voir dans la ligne "Mode BIOS" que le système est bien configuré en mode UEFI.
![Capture d'écran 2026-09-12 172510](https://hackmd.io/_uploads/Hkn81gmYze.png)

#### Partie B — Ubuntu

Pour la première étape, je commence par créer une nouvelle VM.
![Capture d'écran 2026-09-13 144532](https://hackmd.io/_uploads/BylmozNtGe.png)

![Capture d'écran 2026-09-12 140000](https://hackmd.io/_uploads/SJjc5z4tze.png)

Je choisis le fichier ISO Ubuntu à installer.
![Capture d'écran 2026-09-13 144559](https://hackmd.io/_uploads/ByBssMNKMe.png)

J’enregistre ma VM sur mon bureau et je la renomme.
![Capture d'écran 2026-09-13 144747](https://hackmd.io/_uploads/SJ4RozVKMx.png)

Je choisis le stockage.
![image](https://hackmd.io/_uploads/HJVe2fVtGl.png)

Je me rends ensuite dans les paramètres hardware et je fais les réglages nécessaires.
![image](https://hackmd.io/_uploads/rkzlTG4tfg.png)

Je clique sur Finish et ma VM est créée.
![image](https://hackmd.io/_uploads/ByENe74Ffl.png)

Je commence à paramétrer mon Ubuntu.
![Capture d'écran 2026-09-13 145800](https://hackmd.io/_uploads/SkA40MVKGg.png)

Je choisis pour l’instant Français car il n’y a pas Français (Suisse). J’irai ensuite dans les paramètres pour modifier la langue.
![image](https://hackmd.io/_uploads/SySICzNYfx.png)

![Capture d'écran 2026-09-13 150121](https://hackmd.io/_uploads/BJ00AMEYGx.png)
![Capture d'écran 2026-09-13 150135](https://hackmd.io/_uploads/SyJl1mEKGe.png)
![Capture d'écran 2026-09-13 150156](https://hackmd.io/_uploads/HkVxk7EFfe.png)

Je crée donc un compte utilisateur.
![image](https://hackmd.io/_uploads/BkS8km4tzx.png)

Je choisis le fuseau horaire.
![image](https://hackmd.io/_uploads/SJM-xXVFMe.png)

Je commence l’installation.
![image](https://hackmd.io/_uploads/ByENe74Ffl.png)

Après l’installation, je me rends dans les paramètres et je modifie le clavier pour le mettre en mode Français (Suisse).
![image](https://hackmd.io/_uploads/Hk0vUXEFzl.png)

On peut observer sur l’image que ma VM dispose d’une connexion réseau fonctionnelle avec accès à Internet.
![Capture d'écran 2026-09-13 153711](https://hackmd.io/_uploads/rJXLw74Kfg.png)

Pour la suite, je mets à jour le système.
![Capture d'écran 2026-09-13 154232](https://hackmd.io/_uploads/S1TT37NYfx.png)

On peut voir qu’il y a 127 paquets qui peuvent être mis à jour. Je vais donc effectuer la mise à jour.
![Capture d'écran 2026-09-13 154757](https://hackmd.io/_uploads/SJ11pX4KMx.png)

J’ai ensuite décidé de redémarrer le système avec la commande "sudo reboot", mais la commande n’a pas fonctionné. J’ai donc forcé le redémarrage avec "sudo systemctl reboot -i".
![Capture d'écran 2026-09-13 155011](https://hackmd.io/_uploads/HJFUpmEKfg.png)

![Capture d'écran 2026-09-13 155115](https://hackmd.io/_uploads/Hyg6TmVtze.png)

De retour sur le terminal, je décide de nettoyer le système avec la commande "sudo apt autoremove -y", ce qui a supprimé 7 paquets obsolètes.
![Capture d'écran 2026-09-13 155227](https://hackmd.io/_uploads/HkFRaQ4FMl.png)

Je vérifie ensuite quels services sont activés au démarrage du système avec la commande "systemctl list-unit-files --type=service --state=enabled".
![Capture d'écran 2026-09-13 155634](https://hackmd.io/_uploads/H1VS074Ffg.png)

Je peux apercevoir le pare-feu, donc je décide de le configurer directement depuis le terminal.
Je regarde en premier l’état du pare-feu et je vois qu’il est inactif. Je décide donc de l’activer avec "sudo ufw enable".
![Capture d'écran 2026-09-13 155755](https://hackmd.io/_uploads/ry1CCQNYzx.png)

Pour finir la manipulation, j’active la règle SSH avec "sudo ufw allow ssh", ce qui permet de se connecter à la VM à distance sans que le pare-feu bloque l’accès.
La commande "sudo ufw status verbose" confirme que le pare-feu est bien actif.
![Capture d'écran 2026-09-13 155844](https://hackmd.io/_uploads/HJHvy44Yfg.png)

La commande "lsb_release -a" affiche les informations de version de la distribution installée : Ubuntu 26.04.1 LTS.
![image](https://hackmd.io/_uploads/HkMogNNKGg.png)

### 3.3 Cahier des charges 3 : interconnexion des machines

Première étape : relever l’adresse IP des deux VM et vérifier qu’elles sont sur le même réseau.
![Capture d'écran 2026-09-13 171522](https://hackmd.io/_uploads/Sk6CRVEFGl.png)
![Capture d'écran 2026-09-13 171736](https://hackmd.io/_uploads/BJXJyBVFfx.png)

Ensuite, il suffit de pinger les deux machines entre elles.
![Capture d'écran 2026-09-13 171946](https://hackmd.io/_uploads/H1LLBHVtfl.png)

Je sais que Windows bloque le ping avec le pare-feu. Il faut donc se rendre dans les paramètres.
![Capture d'écran 2026-09-13 172109](https://hackmd.io/_uploads/S19qBHNtMe.png)

Se rendre sur Système et sécurité.
![Capture d'écran 2026-09-13 173113](https://hackmd.io/_uploads/rkLsBB4Fzl.png)

Cliquer sur Paramètres avancés.
![Capture d'écran 2026-09-13 173141](https://hackmd.io/_uploads/HyXTrBVtMl.png)

Ensuite Windows Defender Pare-feu.
![Capture d'écran 2026-09-13 173230](https://hackmd.io/_uploads/H12RrHVFfx.png)

Aller sur Règles du trafic entrant.
![Capture d'écran 2026-09-13 173313](https://hackmd.io/_uploads/SkuxUHVKfl.png)

Il faut activer la règle "Partage de fichiers et d’imprimantes".
![Capture d'écran 2026-09-13 173446](https://hackmd.io/_uploads/Bk6LUrVtzx.png)

Une fois que tout est bon, je peux re-pinguer l’adresse IP de Windows depuis le terminal Ubuntu.
On peut observer que zéro paquet est perdu et que tous sont reçus.
![Capture d'écran 2026-09-13 173800](https://hackmd.io/_uploads/S17q8rNFfe.png)

## 4. Conclusion

Ce TP final regroupe les 100 questions du questionnaire hardware et les trois cahiers des charges : trois configurations hardware qui respectent les budgets, le déploiement de Windows 10 Pro et d'Ubuntu en machines virtuelles, et l'interconnexion des deux machines, validée par un ping sans perte de paquets.
