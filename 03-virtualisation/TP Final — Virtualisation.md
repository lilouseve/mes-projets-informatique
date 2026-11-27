# TP Final — Virtualisation

# PARTIE 1 — Audit de connaissances (100 questions)

A. Histoire et bases (1 → 10)

1. Quelle entreprise a créé les premières machines virtuelles dans les années 1960, et sur quel type d'ordinateur ? Les premières machines virtuelles ont été créées par IBM sur des ordinateurs mainframes.

2. Pourquoi la virtualisation a-t-elle perdu de son intérêt entre 1980 et 2000 ? Car il n'y avait plus vraiment de besoin pour la virtualisation, chaque utilisateur avait sa machine dédiée.

3. Quel produit, sorti en 2001, a permis de virtualiser des processeurs x86 standards ? En 2001, VMware ESX est l'hyperviseur qui vient d'être créé et qui permet de virtualiser des processeurs x86.

4. Définissez la virtualisation en une phrase. La virtualisation, c'est le fait de faire tourner plusieurs systèmes d'exploitation, donc d'avoir plusieurs ordinateurs virtuels dans une seule machine.

5. Quelle est la différence entre un hôte (host) et un invité (guest) ? L'hôte, c'est la machine physique qui va héberger la VM, et l'invité, c'est la VM.

6. Qu'est-ce qu'un template de VM et à quoi sert-il ? Un template de VM sert à déployer plusieurs VM similaires avec les mêmes préconfigurations, cela permet de gagner du temps.

7. Un snapshot peut-il remplacer une sauvegarde ? Justifiez. Un snapshot peut remplacer une sauvegarde, mais temporairement, c'est-à-dire que si le disque de stockage a un problème, le snapshot n'existe plus.

8. Citez trois bénéfices concrets de la virtualisation pour une entreprise. Gain de temps, facilité d'utilisation.

9. Qu'est-ce que l'overhead en virtualisation ?

10. Pourquoi un serveur hôte isolé constitue-t-il un SPOF (point de défaillance unique) ?

B. Matériel et extensions de virtualisation (11 → 20)

11. Quel est le nom de l'extension de virtualisation matérielle chez Intel ? Chez AMD ? Le nom de l'extension chez Intel, c'est VT-x, et chez AMD, c'est AMD-V.

12. Quel est le rôle des technologies Intel EPT et AMD RVI ?

13. Quelle commande Linux permet de vérifier le support de la virtualisation ? Que signifient vmx et svm ? vmx, c'est le support de chez Intel, et svm, c'est le support de chez AMD.

14. Où vérifier sous Windows que la virtualisation est activée ?

15. Dans quel environnement faut-il activer VT-x / AMD-V s'il est désactivé ? Il faut aller vérifier dans les réglages du BIOS ou de l'UEFI.

16. Qu'est-ce que la contention d'E/S (I/O contention) ?

17. Pourquoi privilégie-t-on des disques NVMe plutôt que des HDD pour héberger des VMs ? Car les disques HDD sont plus anciens et moins performants.

18. À quoi sert le SR-IOV ?

19. Qu'est-ce que la virtualisation imbriquée (nested virtualization) et pourquoi est-elle utile dans un lab ? La virtualisation imbriquée sert à faire tourner un hyperviseur directement dans une VM ; avec ceci, on peut faire des clusters.

20. Pourquoi un hôte de virtualisation a-t-il besoin de plus de bande passante réseau qu'un serveur physique classique ?

C. Types de virtualisation (21 → 28)

21. Qu'est-ce que la VDI ? Citez une solution du marché. La VDI, c'est le fait d'avoir accès à des bureaux Windows à distance.

22. Qu'est-ce que le SDN ? Citez une solution du marché.

23. Qu'est-ce que la virtualisation de stockage ? Citez deux solutions.

24. Quel problème résout la virtualisation applicative ?

25. Quelle est la différence fondamentale entre une VM et un conteneur ? La VM utilise un OS, tandis que le conteneur utilise uniquement des applications.

26. Pourquoi un conteneur démarre-t-il beaucoup plus vite qu'une VM ? Car un conteneur n'a pas besoin de faire démarrer d'OS.

27. Une entreprise veut que 150 employés accèdent à leur bureau Windows depuis n'importe quel appareil. Quel type de virtualisation recommandez-vous ? Je recommanderais l'option de la VDI.

28. Dans Proxmox VE, que sont les LXC ?

D. Acteurs du marché (29 → 35)

29. Qui a racheté VMware, et en quelle année ? Broadcom a racheté VMware en 2023.

30. Quelle a été la conséquence principale de ce rachat pour les clients ? La conséquence principale, c'est que Broadcom, après le rachat de VMware, a rendu payantes certaines utilisations, ce qui a poussé les utilisateurs habituels à se diriger vers d'autres alternatives comme Proxmox.

31. Sur quelle technologie de virtualisation repose Proxmox VE ?

32. Quel est l'hyperviseur de Microsoft et dans quels produits est-il intégré ? L'hyperviseur de Microsoft, c'est Hyper-V ; il est intégré dans Windows 10/11 et Windows Server.

33. Citez deux fournisseurs cloud européens ou suisses répondant à un besoin de souveraineté des données. Infomaniak et OVHcloud.

34. Quel est le rôle de Kubernetes ?

35. Sur quel hyperviseur historique repose XCP-ng ?

E. Processeurs et dimensionnement (36 → 47)

36. Quelle est la différence entre l'architecture x86-64 et l'architecture ARM ?

37. Pourquoi une VM Windows Server x86 ne peut-elle pas être exécutée sur un hôte à processeur ARM (ex. Ampere Altra) ? Car ils sont incompatibles entre eux.

38. Différenciez cœur physique, thread et vCPU.

39. Quel gain de performance approximatif apporte l'Hyper-Threading / SMT ? L'Hyper-Threading apporte un gain de performance entre 15 et 30 %.

40. Qu'est-ce que l'overcommit (surallocation) CPU ?

41. Quel ratio d'overcommit CPU est raisonnable pour des charges générales ? Pour des charges critiques ?

42. Calcul : un hôte possède 2 processeurs de 16 cœurs / 32 threads. Overcommit 4:1, VMs à 4 vCPU. Combien de VMs peut-il héberger au maximum ? 2 × 16 × 32 = 1024 1024 ÷ 4 = 256 256 ÷ 4 = 64 VM maximum Le nombre de VM maximum est de 64.

43. Calcul : 60 VMs à 2 vCPU, ratio 3:1. Combien de threads physiques faut-il au minimum ? 60 × 2 = 120 vCPU 120 ÷ 3 = 40 threads Le nombre de threads minimum est de 40.

44. Pourquoi évite-t-on l'overcommit de la RAM en production ?

45. Que signifie TDP et pourquoi est-ce un critère business ?

46. Pour 40 petites VMs, privilégiez-vous la fréquence ou le nombre de cœurs ? Et pour une application monothread ?

47. Qu'est-ce que le dimensionnement N+1 dans un cluster, et pourquoi est-il indispensable ?

F. Hyperviseurs (48 → 55)

48. Définissez un hyperviseur. Un hyperviseur, c'est un logiciel qui permet de créer et de gérer des VM en utilisant les ressources physiques d'une machine.

49. Quelle est la différence entre un hyperviseur de Type 1 et de Type 2 ? Un hyperviseur de Type 1 s'installe directement sur le matériel physique et ne dispose pas d'OS, contrairement à l'hyperviseur de Type 2, qui utilise un OS et s'installe comme une application.

50. Citez trois hyperviseurs de Type 1. VMware ESXi, Microsoft Hyper-V, Proxmox.

51. Citez trois hyperviseurs de Type 2. VMware Workstation, VirtualBox, Parallels Desktop.

52. Pourquoi un hyperviseur de Type 1 est-il préféré en production ? Car il y a un accès direct au matériel et plus de performances.

53. Quelles deux technologies de virtualisation Proxmox VE combine-t-il ?

54. Dans un environnement 100 % Microsoft, quel hyperviseur est le plus cohérent ? Pourquoi ? Hyper-V est le plus cohérent, car on est sur du 100 % Microsoft, donc il y a l'intégration d'Active Directory et des licences Windows Server.

55. Quel hyperviseur recommandez-vous pour une PME au budget serré souhaitant une solution open source ? Pour un budget serré, je recommanderais Proxmox VE.

G. Proxmox VE (56 → 65)

56. Sur quel port est accessible l'interface web de Proxmox VE ? L'interface web de Proxmox VE est accessible sur le port 8006.

57. Quel est le nom du pont réseau (bridge) créé par défaut ? Le nom du pont réseau est vmbr0.

58. Quel est le rôle de ce pont réseau ? Il sert à relier la VM au réseau physique de l'hôte.

59. Quel outil en ligne de commande réalise les sauvegardes de VMs sous Proxmox ?

60. Quelle commande crée un cluster Proxmox ?

61. Quelle commande permet à un nœud de rejoindre un cluster existant ?

62. Quelle commande affiche l'état du cluster et du quorum ?

63. Qu'est-ce que le quorum et pourquoi recommande-t-on au minimum 3 nœuds ?

64. Quel service assure la communication entre les nœuds d'un cluster Proxmox ? Le service qui assure la communication entre les nœuds est Corosync.

65. Qu'est-ce que Ceph dans un contexte Proxmox ? C'est une solution de stockage intégrée nativement.

H. VMware ESXi, Hyper-V, RHV (66 → 77)

66. Quelle est l'URL d'accès au client web d'un hôte ESXi ? L'URL d'accès au client web d'un hôte ESXi est : https://ip-esxi.

67. Quel est le rôle de vCenter Server ? Le rôle de vCenter Server est de gérer les hôtes ESXi et leurs VM de façon centralisée.

68. Différenciez vSwitch et Port Group.

69. À quoi sert un port VMkernel ?

70. Qu'est-ce que VMFS ? VMFS est un système de fichiers qui appartient à VMware et qui permet d'accéder en même temps aux disques virtuels sur un datastore partagé.

71. Différenciez un disque Thin et un disque Thick.

72. Quel est le format de disque virtuel chez VMware ? Chez Hyper-V ? Chez RHV ? Le format de disque chez VMware est VMDK.

73. Citez les trois types de commutateurs virtuels Hyper-V et leur usage.

74. Différenciez une VM Hyper-V de Génération 1 et de Génération 2. La VM de Génération 1 utilise le BIOS, et la VM de Génération 2 utilise l'UEFI.

75. Différenciez un checkpoint standard et un checkpoint de production.

76. Comment s'appelle la migration à chaud chez VMware ? Chez Hyper-V ? Chez VMware, c'est vMotion, et chez Hyper-V, c'est Live Migration.

77. Quel est l'équivalent Hyper-V de vSphere HA ?

I. Réseau virtuel (78 → 85)

78. Qu'est-ce qu'un VLAN et quel est son intérêt en virtualisation ?

79. Quelle norme IEEE définit le marquage VLAN ?

80. À quoi sert l'agrégation de liens (LACP / bonding) sur un hôte ?

81. Pourquoi isoler le réseau de management sur un VLAN dédié ?

82. Pourquoi séparer les réseaux cluster, stockage et VMs ?

83. Deux VMs hébergées sur deux hyperviseurs différents doivent se pinguer. Citez trois conditions nécessaires. La première condition, c'est d'être sur le même sous-réseau ; la seconde, vérifier que le pare-feu ne bloque pas le ping ; et la troisième, qu'un switch soit bien configuré entre les deux hôtes.

84. Pourquoi un ping vers une VM Windows échoue-t-il souvent par défaut ? Comment le corriger proprement ? La plupart du temps, c'est le pare-feu Windows qui bloque ; il suffit de se rendre dans les paramètres du pare-feu Windows et d'activer la règle « Partage de fichiers et d'imprimantes » sur un réseau privé.

85. Dans un lab imbriqué, quelle option doit être activée sur la VM qui héberge l'hyperviseur, côté hyperviseur « parent » ?

J. Stockage, haute disponibilité, sauvegarde (86 → 95)

86. Différenciez SAN et NAS. Le SAN est un stockage bloc, et le NAS est un stockage de fichiers.

87. Citez un protocole de stockage bloc et un protocole de stockage fichier. Un protocole de stockage bloc : iSCSI. Un protocole de stockage fichier : NFS.

88. Pourquoi un stockage partagé est-il indispensable à la migration à chaud ? Car les deux hôtes doivent voir le même stockage, donc la VM doit garder accès à son disque pendant le transfert sans avoir à faire de copie de données.

89. Différenciez migration à chaud et basculement HA. La migration à chaud est une manipulation planifiée qui ne nécessite pas l'arrêt de la VM, tandis que le basculement HA intervient lors d'une panne, ce qui implique un redémarrage de la VM.

90. Qu'est-ce qu'un heartbeat dans un cluster ?

91. Énoncez la règle de sauvegarde 3-2-1.

92. Contre quoi protègent respectivement un snapshot, la HA et une sauvegarde ? Un snapshot protège contre une fausse manipulation, ce qui permet de revenir en arrière ; la HA protège d'une panne matérielle ; et la sauvegarde protège contre une perte de données.

93. Pourquoi ne faut-il pas laisser un snapshot actif trop longtemps ?

94. Qu'est-ce qu'un split-brain et comment le quorum l'empêche-t-il ?

95. Pourquoi un cluster de 2 nœuds sans stockage partagé ne fournit-il pas une vraie haute disponibilité ?

K. Sécurité et cloud (96 → 100)

96. Qu'est-ce qu'une VM Escape ?

97. Citez trois mesures de durcissement (hardening) d'un hyperviseur.

98. Pourquoi activer le MFA sur les consoles d'administration de virtualisation ?

99. Différenciez cloud hybride et multi-cloud.

100. Qu'est-ce que le vendor lock-in et comment la virtualisation multi-plateforme permet-elle de le limiter ?

PARTIE 2 — Cahiers des charges
CAHIER DES CHARGES 1 — Dimensionnement de la plateforme et choix du processeur

1. Calcul des besoins en vCPU

Total des vCPU critiques : 2 + 2 + 8 + 8 = 20

Calcul des threads critiques : 20 / 1 = 20 threads

Calcul des threads standards : 40 / 3 = 13,33 threads

Total : 20 + 13,33 = 33,33 threads

Application du pourcentage de 30 % : 33 × (1 + 30/100) = 42,9 threads

Besoin total ≈ 43 threads

2. Calcul du besoin en RAM

RAM critique : 112 Go RAM standard : 160 Go Total : 112 + 160 = 272 Go

Application du pourcentage de 30 % : 272 × (1 + 30/100) = 354 Go

Besoin total ≈ 354 Go de RAM

3. Calcul du besoin en stockage

Stockage critique : 1300 Go Stockage standard : 3420 Go Total : 1300 + 3420 = 4720 Go

Application du pourcentage de 30 % : 4720 × (1 + 30/100) = 6136 Go

Ajout d'une marge de 20 % : 6136 / (1 - 20/100) = 7670 Go

Calcul RAID 10 : 7670 × 2 = 15 340 Go

Besoin total ≈ 15 To de stockage

4. Répartition sur deux hôtes

CPU par hôte : 43 / 2 = 21,5 threads

RAM par hôte : 354 / 2 = 177 Go

Réserve par hôte :

CPU : 21,5 + 4 = 25,5 threads
RAM : 177 + 8 = 185 Go

5. Vérification de la plus grosse VM

VM : SRV-SQL01

8 threads
64 Go de RAM

Capacité d'un hôte :

25,5 threads
185 Go de RAM

La VM la plus grosse peut être exécutée sur un seul hôte.

6. Configuration de la RAM (barrettes de 32 Go)

Calcul : 185 / 32 = 5,78

6 × 32 = 192 Go

Il faut donc prévoir 6 barrettes de 32 Go.

Étape 5 — Choix du processeur

P1 n'est pas compatible car il n'y a pas assez de threads : 24 threads, alors qu'on en demande environ 25,5 (26).

P2 est compatible car il y a assez de threads, il y a même une marge de 6 threads.

P3 est compatible également, avec une marge de 6 threads.

P4 est compatible, cependant il y a une marge importante de 38 threads.

P5 n'est pas compatible malgré le fait qu'il ait suffisamment de threads. Le problème est le format ARM, qui est incompatible avec nos VM.

Je recommanderai le P3, car il a les mêmes performances au niveau des threads que le P2, une fréquence et un TDP presque identiques. Son prix est quasiment divisé par 2 comparé au P2.

Le P5 est totalement incompatible avec notre hyperviseur, qui nécessite du x86-64, alors que le P5 utilise de l'ARM. Toutefois, le P5 reste beaucoup plus puissant (64 threads), ce qui dépasse notre besoin réel (26 threads). Son prix reste aussi plus cher que le P3.

## CAHIER DES CHARGES 2 — POC multi-hyperviseurs : ESXi + Proxmox

Pour tester le ping, j'ai en premier lieu vérifié que j'étais sur le même sous-réseau que ma collaboratrice, qui avait installé Proxmox.
![Capture d'écran 2026-09-25 152158](https://hackmd.io/_uploads/rycrMRI9Gl.png)

Une fois cela effectué, je me suis rendu dans le terminal pour pinguer sa VM. Comme on peut l'apercevoir, le ping a réussi.
![Capture d'écran 2026-09-25 153212](https://hackmd.io/_uploads/rkp_MCU5Gl.png)


## CDC 3 — Cluster de virtualisation haute disponibilité
## Documentation étape par étape — Léman Transports & Logistique SA

---

## 0. Choix de la voie retenue

### Voie retenue : **Voie B — VMware ESXi + vCenter (VCSA)**

**Justification (5 lignes, lien avec CDC 1 et CDC 2) :**

VMware vSphere (ESXi + vCenter) est l'hyperviseur de référence en environnement d'entreprise et s'aligne directement sur le processeur retenu au CDC 1 (AMD EPYC 9124, x86-64, certifié sur la liste de compatibilité VMware "VCG"), garantissant un support matériel officiel que Léman Transports & Logistique peut exiger contractuellement, contrairement à une distribution communautaire. vSphere HA et vMotion sont des technologies matures et largement documentées en production, avec des SLA et un support éditeur (VMware by Broadcom) qui rassurent une DSI sur une charge critique comme l'ERP — exigence explicite du client ("Nous ne voulons plus jamais qu'une panne de serveur arrête l'ERP"). L'architecture réseau à 3 sous-réseaux du CDC 2 (MGMT/CLUSTER/STORAGE) se transpose nativement sur ESXi via des adaptateurs VMkernel dédiés (un par fonction : gestion, vMotion, stockage NFS), assurant la même isolation de trafic déjà planifiée. Le coût de licence supplémentaire (ESXi + vCenter, contrairement à Proxmox VE) est un compromis assumé en échange d'un écosystème d'outillage, de compatibilité tierce (sauvegarde, monitoring) et d'une compétence plus répandue sur le marché de l'emploi, facilitant le recrutement/la maintenance à long terme. Le choix est donc cohérent avec une stratégie de production réelle et durable, alors que la Voie A (Proxmox) resterait davantage indiquée pour un lab ou un budget contraint.

---

## 1. Rappel de l'architecture réseau imposée (3.1)

| Réseau | Usage | Sous-réseau |
|---|---|---|
| MGMT | Administration des hôtes, VMs | 192.168.50.0/24 |
| CLUSTER | vMotion | 10.10.10.0/24 |
| STORAGE | Accès au stockage NFS | 10.20.20.0/24 |

| Machine | MGMT | CLUSTER | STORAGE |
|---|---|---|---|
| NODE1 (esx-n1) | 192.168.50.31 | 10.10.10.31 | 10.20.20.31 |
| NODE2 (esx-n2) | 192.168.50.32 | 10.10.10.32 | 10.20.20.32 |
| NODE3 (esx-n3) | 192.168.50.33 | 10.10.10.33 | 10.20.20.33 |
| NAS-LAB01 (NFS) | 192.168.50.50 | — | 10.20.20.50 |
| VCSA | 192.168.50.40 | — | — |
| VM03-APP (test HA) | 192.168.50.60 | — | — |

Chaque hôte ESXi dispose de 3 cartes réseau virtuelles, une par sous-réseau — à créer au niveau de l'hyperviseur physique/hôte de virtualisation imbriquée hébergeant les 3 VM ESXi du lab, avant même l'installation d'ESXi.

 Le CDC autorise un minimum de 2 hôtes ESXi pour la voie B (contre 3 pour Proxmox) — mais la règle N+1 du CDC 1 (charge sur 2 hôtes/3) suppose bien 3 hôtes ESXi pour respecter la tolérance de panne ; ce document retient donc les 3 nœuds (esx-n1/n2/n3) en cohérence avec le dimensionnement du CDC 1.

---

## 2. Prérequis (3.2)

| Prérequis | Détail |
|---|---|
| Noms d'hôte uniques | Définis à l'installation d'ESXi (ex. `esx-n1.ltl.local`) |
| Résolution de noms | Fichier hosts sur la machine d'administration et sur la VCSA, **ou** DNS interne (fortement recommandé : la VCSA exige une résolution DNS fiable, directe et inverse, pour son propre FQDN) |
| NTP synchronisé | À configurer sur chaque hôte : `Configurer → Système → Heure` → ajouter un ou plusieurs serveurs NTP, démarrer le service `ntpd`. Une dérive d'horloge entre hôtes/VCSA casse l'authentification SSO et peut fausser les logs HA |
| Même version d'hyperviseur | Installer la même image ISO ESXi (ex. 8.0) sur les 3 hôtes, mêmes correctifs appliqués (`esxcli software vib` ou vLCM une fois le cluster géré par vCenter) |

**Exemple de configuration NTP (CLI ESXi) :**
```bash
esxcli system ntp set --server=pool.ntp.org
esxcli system ntp set --enabled=true
esxcli system ntp get
```

---

## 3. Configuration du serveur NFS (NAS-LAB01)

```bash
# Sur NAS-LAB01 (Ubuntu Server)
apt update && apt install -y nfs-kernel-server
mkdir -p /srv/nfs/ltl-vms
chown nobody:nogroup /srv/nfs/ltl-vms
chmod 777 /srv/nfs/ltl-vms

# Export limité au réseau STORAGE uniquement (exigence du CDC)
echo "/srv/nfs/ltl-vms 10.20.20.0/24(rw,sync,no_subtree_check,no_root_squash)" >> /etc/exports
exportfs -ra
systemctl restart nfs-kernel-server
exportfs -v
```
 Point de sécurité à documenter : l'export est restreint à `10.20.20.0/24` (réseau STORAGE) → inaccessible depuis MGMT, conforme à l'exigence du CDC. ESXi supporte NFSv3 et NFSv4.1 : NFSv3 est suffisant ici (pas besoin de Kerberos), mais NFSv4.1 apporte le multipathing s'il y a plusieurs interfaces réseau côté NAS.

---

## 4. Étapes spécifiques Voie B — VMware ESXi + vCenter (3.4)

### B1 — Déployer la VCSA (taille « Tiny »)

Le déploiement se fait en **2 étapes** via l'installateur `vcsa-ui-installer` (dossier `win32`, `lin64` ou `mac` selon le poste d'administration) monté depuis l'ISO VCSA officielle :

**Étape 1 — Déploiement de l'appliance (OVA) :**

| Paramètre | Valeur |
|---|---|
| Hôte cible | esx-n1 (192.168.50.31) |
| Nom de la VM | vcsa-ltl |
| Taille de déploiement | **Tiny** (jusqu'à 10 hôtes / 100 VM — largement suffisant pour 3 hôtes / 15 VM) → 2 vCPU, 10 Go RAM |
| Stockage | Datastore local de esx-n1 (avant que le NFS partagé ne soit monté) |
| Réseau | MGMT (192.168.50.0/24) |
| IP VCSA | 192.168.50.40 |

**Étape 2 — Configuration de l'appliance :**
- Synchronisation NTP
- Création du domaine SSO (ex. `vsphere.local`)
- Mot de passe administrateur SSO

**Accès une fois déployée** : `https://192.168.50.40/ui`

### B2 — Créer le datacenter DC-LTL et le cluster CLUSTER-LTL

Dans le vSphere Client (`https://192.168.50.40/ui`) :
1. Clic droit sur vCenter → **Nouveau centre de données** → nommer `DC-LTL`
2. Clic droit sur `DC-LTL` → **Nouveau cluster** → nommer `CLUSTER-LTL`
3. Ne pas encore activer HA/DRS à cette étape (activés en B6, une fois le stockage partagé opérationnel)

### B3 — Ajouter les 3 hôtes ESXi au cluster

Clic droit sur `CLUSTER-LTL` → Ajouter des hôtes → saisir l'IP/FQDN + identifiants root pour chacun des 3 hôtes (esx-n1, esx-n2, esx-n3), un par un ou par lot.

Point à documenter : l'hôte esx-n1 qui héberge la VCSA elle-même doit aussi être ajouté au cluster — attention à ne pas migrer/éteindre par erreur la VM de la VCSA lors des tests de panne, sous peine de perdre l'accès au vSphere Client pendant l'incident (SPOF, voir §6.4).

### B4 — Créer un adaptateur VMkernel vMotion sur le réseau CLUSTER (par hôte)

Pour chaque hôte : `Configurer → Mise en réseau → Adaptateurs VMkernel → Ajouter`

| Champ | Valeur (ex. esx-n1) |
|---|---|
| Groupe de ports / vSwitch | vSwitch dédié ou port group sur le vNIC branché sur le réseau CLUSTER |
| Adresse IP | 10.10.10.31 (32/33 pour n2/n3) |
| Masque | 255.255.255.0 |
| Services activés | **vMotion** (cocher la case) |

### B5 — Adaptateur VMkernel stockage + montage du datastore NFS (par hôte)

Pour chaque hôte, créer un second adaptateur VMkernel sur le réseau STORAGE :

| Champ | Valeur (ex. esx-n1) |
|---|---|
| Adresse IP | 10.20.20.31 (32/33 pour n2/n3) |
| Services activés | Aucun service spécial requis (NFS n'a pas de case à cocher comme vMotion) |

Puis, monter le datastore NFS sur les 3 hôtes : `Configurer → Stockage → Datastores → Nouveau datastore`

| Champ | Valeur |
|---|---|
| Type | NFS → NFS 3 (ou 4.1) |
| Nom du datastore | **NFS-LTL** |
| Dossier | /srv/nfs/ltl-vms |
| Serveur NFS | 10.20.20.50 |
| Hôtes | esx-n1, esx-n2, esx-n3 (tous, pour qu'ils voient le même datastore partagé — condition indispensable au vMotion et à HA) |

### B6 — Activer vSphere HA (DRS en option)

`Cluster CLUSTER-LTL → Configurer → Services → vSphere HA → Modifier` :
- Activer vSphere HA
- Réponse à la panne d'hôte : **Redémarrer les VM**
- Admission Control : réserver la capacité équivalente à **1 hôte** (cohérent avec la règle N+1 du CDC 1 : "2 hôtes sur 3" doivent absorber la charge)
- (Option) Activer DRS en mode "entièrement automatisé" pour équilibrer la charge, non requis explicitement par le CDC mais recommandé en complément de HA

### B7 — Réaliser un vMotion de VM03-APP

Clic droit sur VM03-APP → Migrer → choisir "Modifier uniquement l'hôte de calcul" (vMotion pur, sans déplacer le stockage puisqu'il est déjà partagé sur NFS-LTL) → sélectionner esx-n2 comme hôte de destination.

### B8 — Sauvegarde (export OVF planifié ou solution équivalente)

Le CDC laisse ce point ouvert ("à justifier"). Deux options à documenter :

**Option retenue : export OVF planifié via script PowerCLI**, solution native ne nécessitant aucun composant tiers payant (contrairement à Veeam Backup & Replication, qui serait le standard du marché en production réelle mais hors budget d'un lab/PoC) :

```powershell
# Exemple de script PowerCLI à planifier quotidiennement (tâche planifiée Windows / cron sur un jump-host)
Connect-VIServer -Server 192.168.50.40
Export-VApp -VM "VM03-APP" -Destination "\\10.20.20.50\ltl-vms\backups\" -Format OVF
Disconnect-VIServer -Confirm:$false
```

*Justification du choix* : l'export OVF capture l'état complet de la VM (config + disques) sans agent supplémentaire ; en production réelle, il faudrait migrer vers une solution de sauvegarde d'image dédiée (Veeam, ou vSphere Data Protection) avec gestion de rétention et sauvegardes incrémentales, non couvertes par un simple export OVF.

---

## 5. Exigences communes détaillées (3.2)

### 5.1 Création de VM03-APP

| Paramètre | Valeur |
|---|---|
| OS | Ubuntu Server ou Debian |
| vCPU | 1 |
| RAM | 1 Go |
| Disque | 10 Go, sur datastore **NFS-LTL** |
| IP | 192.168.50.60 (réseau MGMT) |

### 5.2 Test de migration à chaud (vMotion)

**Protocole à documenter :**
1. Démarrer un ping continu vers 192.168.50.60 depuis une machine tierce
2. Lancer le vMotion esx-n1 → esx-n2 (étape B7)
3. Relever le nombre de paquets perdus (attendu : 0 paquet perdu — vMotion est conçu pour une bascule totalement transparente, la VM continue de répondre sur le réseau MGMT tout au long du transfert de sa RAM, seul le "switchover" final dure quelques millisecondes)

### 5.3 Simulation de panne (test de bascule vSphere HA)

**Protocole à documenter :**
1. VM03-APP tourne sur, disons, esx-n1, sous protection vSphere HA
2. Couper brutalement esx-n1 (extinction forcée côté hyperviseur hôte — pas un arrêt propre "Mettre en veille prolongée"/`shutdown`, sinon vCenter migrerait proprement la VM au lieu de déclencher un vrai failover HA)
3. Chronométrer depuis la coupure jusqu'à la réponse au ping sur 192.168.50.60

**Ordre de grandeur documenté par VMware pour vSphere HA :**
- Détection de la perte de l'hôte par les autres hôtes du cluster (heartbeats réseau + heartbeats datastore) : généralement ~15 secondes avant déclaration d'isolement/panne
- Redémarrage de la VM sur un hôte survivant : quelques dizaines de secondes supplémentaires (dépend du temps de boot du système d'exploitation invité)
- Total théorique ≈ 1 à 2 minutes, avec coupure de service réelle pendant tout ce laps de temps

### 5.4 Retour à la normale

1. Redémarrer esx-n1
2. Vérifier dans vCenter : `Cluster CLUSTER-LTL → Hôtes` → esx-n1 doit repasser en statut "Connecté" et "Actif (mode veille de maintenance désactivé)"
3. Vérifier `Résumé du cluster → vSphere HA` : plus d'alerte de type "Protection HA en cours" ou "Hôte isolé"
4. (Si DRS actif) attendre le ré-équilibrage automatique de la charge sur les 3 hôtes de nouveau disponibles

---

## 6. Analyse demandée (3.5)

### 6.1 Pourquoi 3 nœuds et pas 2 ? Que se passerait-il avec 2 nœuds et coupure du lien CLUSTER ?

Techniquement, vSphere HA ne repose pas sur un vote de quorum de type Corosync : dans un cluster à 2 hôtes, si le lien réseau de heartbeat (généralement porté sur le réseau MGMT, redondé par le datastore heartbeat) est coupé entre les deux, chaque hôte croit l'autre en panne (situation de "réseau partitionné"/isolation). Avec l'Admission Control mal configuré ou en cas de "split-brain" non résolu par le heartbeat sur datastore, les deux hôtes peuvent chacun tenter de redémarrer les mêmes VM, provoquant un risque de corruption de disque (deux instances de la même VM actives simultanément) si le verrouillage des fichiers VMFS/NFS échouait. Avec 3 hôtes, en cas de perte du lien CLUSTER (vMotion) entre 2 d'entre eux, le 3ᵉ hôte et le mécanisme de heartbeat sur le datastore partagé permettent de déterminer sans ambiguïté quel hôte est réellement tombé plutôt qu'isolé réseau — cela lève l'ambiguïté qui existerait structurellement avec seulement 2 nœuds, et c'est la raison pour laquelle le CDC exige le respect de la règle N+1 sur 3 hôtes (issue du CDC 1) plutôt que le minimum technique de 2 hôtes qu'ESXi accepterait.

### 6.2 Pourquoi séparer les réseaux MGMT, CLUSTER et STORAGE ?

- Performance/latence : le trafic vMotion (transfert de RAM de VM, potentiellement plusieurs Go) est très consommateur de bande passante ; le mélanger avec le trafic NFS (accès disque permanent des VM) créerait de la contention et des ralentissements pour toutes les VM en production pendant chaque migration.
- Fiabilité du heartbeat HA : le réseau MGMT porte la communication de heartbeat entre hôtes ; le saturer avec du trafic de stockage ou de migration risquerait de déclencher de faux positifs d'isolement d'hôte (donc des bascules HA inutiles).
- Sécurité : l'accès au NFS restreint au seul réseau STORAGE limite la surface d'attaque — un poste compromis sur MGMT ne peut pas directement monter/altérer le datastore partagé.
- Isolation des pannes : un problème sur un seul segment (ex. switch STORAGE) n'affecte pas la capacité des hôtes à communiquer entre eux (CLUSTER) ni à être administrés (MGMT).

### 6.3 vMotion vs basculement vSphere HA : différences observées

| Critère | vMotion (migration à chaud) | Basculement vSphere HA |
|---|---|---|
| **Déclenchement** | Planifié, volontaire (maintenance, équilibrage DRS) | Automatique, suite à une panne d'hôte détectée |
| **Paquets perdus** | Quasi nul (0-1 paquet, coupure de quelques ms au switchover) | Coupure de service complète pendant toute la durée du basculement |
| **Durée** | Quelques secondes à quelques dizaines de secondes (dépend de la RAM allouée et de la bande passante du réseau CLUSTER) | ≈ 1 à 2 minutes (détection + redémarrage) |
| **Type de redémarrage** | Aucun : l'état RAM/CPU de la VM est transféré en direct, le processus ne s'arrête jamais | **Redémarrage complet à froid** de la VM sur un autre hôte — équivalent à un reboot brutal, avec fsck possible et perte de tout état non écrit sur disque au moment de la panne |

vMotion est donc **totalement transparent** pour l'utilisateur, alors que le basculement HA implique une **interruption de service réelle mais bornée dans le temps**, seul mécanisme possible en cas de panne matérielle imprévue et non planifiée.

### 6.4 Point de défaillance unique (SPOF) restant, et solution en production

**SPOF n°1 : NAS-LAB01 (serveur NFS unique).** Tout le stockage partagé — donc toutes les VM et leurs sauvegardes — dépend d'un seul serveur NFS. Sa panne rend indisponibles toutes les VM du cluster (même avec 3 hôtes ESXi et vSphere HA actif), car aucun hôte ne peut plus accéder aux fichiers disques.

**SPOF n°2, spécifique à la voie B : la VCSA elle-même.** Si l'hôte qui héberge la VCSA tombe, vSphere HA redémarre bien la VCSA sur un autre hôte (car elle est elle-même une VM comme les autres, sur le même stockage partagé), mais pendant la fenêtre de redémarrage, **la gestion centralisée (vSphere Client, création/modification de VM, déclenchement manuel de vMotion) est indisponible** — bien que les VM déjà en cours d'exécution, elles, continuent de tourner normalement (HA fonctionne au niveau des hôtes ESXi eux-mêmes, indépendamment de la disponibilité de vCenter à cet instant précis).

**Solutions proposées pour la production :**
- Stockage : remplacer le NAS unique par une baie SAN/NAS redondante (double contrôleur, double alimentation, multipathing sur le réseau STORAGE), ou une solution hyperconvergée type **vSAN** (natif VMware, réplique les données sur plusieurs hôtes/disques locaux, élimine le NAS externe comme SPOF).
- VCSA : déployer la VCSA en configuration **haute disponibilité native** (vCenter HA, "VCHA" — une VCSA active, une passive, un témoin), disponible à partir de l'édition Standard de vCenter.

### 6.5 Combien de VMs LTL le cluster de production pourrait-il encore accueillir en cas de perte d'un hôte (lien avec CDC 1) ?

Le dimensionnement du CDC 1 a été construit précisément autour de la règle N+1 : *"la charge totale doit tenir sur 2 hôtes sur 3"*. Les 15 VM du CDC 1 (44 threads et 354 Go de RAM au total avec la croissance +30%) ont été dimensionnées pour que **2 hôtes seulement suffisent à faire tourner l'intégralité du parc** (26 threads/hôte et 185-192 Go RAM/hôte, avec marge vérifiée à l'étape 4 du CDC 1, y compris pour la plus grosse VM SRV-SQL01).

Réponse : en cas de perte d'un hôte, le cluster de production continue d'accueillir l'intégralité des 15 VM existantes (les 4 critiques et les 11 standard), sans qu'aucune VM ne doive être coupée ou mise en pause — c'est exactement la contrainte qui a dicté le choix du processeur et de la RAM par hôte dès le CDC 1. La marge résiduelle calculée (environ +4 threads et +14 Go de RAM disponibles sur 2 hôtes cumulés) représente la seule capacité additionnelle exploitable pour de nouvelles VM en mode dégradé — donc quasiment nulle, ce qui confirme que le dimensionnement du CDC 1 est **juste suffisant** pour le parc actuel en mode N+1, sans marge significative pour une croissance non planifiée au-delà des +30% déjà intégrés.

---

## 7. Tableau récapitulatif du livrable

| Élément | Statut |
|---|---|
| Voie choisie et justifiée | Voie B — VMware ESXi + vCenter |
| Architecture réseau (3 sous-réseaux, IP par nœud) | Documentée §1 |
| Étapes B1 → B8 (VCSA, cluster, réseau VMkernel, stockage, HA, vMotion, backup) | Documentées §4 |
| VM03-APP et protocoles de test (migration, panne, retour à la normale) | Documentés §5 |
| 5 questions d'analyse (§3.5) | Répondues §6 |

---

## 8. Sources consultées (pour vérification et précision complémentaire)

- Déploiement VCSA (tailles Tiny/Small/Medium/Large, process en 2 stages) : https://1gbits.com/blog/how-to-install-vcenter/
- Guide détaillé pas-à-pas déploiement VCSA + création datacenter/cluster/ajout d'hôte : https://docs.vmware.com/en/VMware-Edge-Compute-Stack/services/utility-substation-vpac-ready-infrastructure/GUID-37A0F1BB-CAAB-4D67-8142-B5E5325A1F4C.html
- Retour d'expérience déploiement VCSA (taille Tiny, avertissements mémoire, etc.) : https://www.carlwebster.com/?p=30842
- Discussion communautaire sur le montage de datastores NFS sur plusieurs hôtes d'un même cluster (condition pour vMotion/HA) : https://community.netapp.com/t5/Active-IQ-Unified-Manager-Discussions/how-to-mount-datastores-for-a-new-host/m-p/41180
- Documentation officielle VMware — flux d'installation et de configuration vSphere : citée dans https://blog.matrixpost.net/?p=63774 (renvoie vers docs.vmware.com)

Les valeurs de timing HA (~15s détection + redémarrage) et de perte de paquets en vMotion (0-1 paquet) sont des ordres de grandeur documentés par VMware et la communauté; en situation réelle (TP physique), les valeurs mesurées doivent remplacer ces estimations dans le rapport final. Les étapes détaillées de configuration exacte (noms de menus) peuvent légèrement varier selon la version d'ESXi/vCenter installée (7.x vs 8.x) — à vérifier sur la documentation officielle VMware/Broadcom au moment de la réalisation.
