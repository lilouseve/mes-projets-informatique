# Projet 5 — Comparatif d'hyperviseurs pour un cahier des charges client

## 1. Contexte et scénario client

Un client hésite entre plusieurs solutions de virtualisation pour son infrastructure et demande une recommandation argumentée.

> ⚠️ **À REMPLACER par le scénario donné par le formateur.** Scénario d'exemple utilisé dans ce document :
>
> PME de 25 salariés, 3 serveurs à virtualiser (fichiers, application métier, messagerie), budget limité, un administrateur système polyvalent à l'aise avec Linux, besoin de sauvegardes simples et de pouvoir évoluer.

## 2. Critères de comparaison

| Critère | Pourquoi il compte | Poids (sur 5) |
|---|---|---|
| **Coût** | Budget limité du client | 5 |
| **Licences** | Risque de conformité, évolution des tarifs | 4 |
| **Facilité d'administration** | Un seul administrateur | 4 |
| **Performances** | Fluidité des applications | 3 |
| **Écosystème** | Outils, sauvegarde, support, communauté | 4 |
| **Fonctions de production** | Cluster, haute disponibilité, snapshots, sauvegarde | 4 |

## 3. Présentation des solutions

| Solution | Type | Principe |
|---|---|---|
| **Proxmox VE** | Type 1 (installé directement sur le serveur) | Plateforme open source basée sur Debian, avec KVM (VM) et LXC (conteneurs), administrée par une interface web |
| **Hyper-V** | Type 1 | Hyperviseur de Microsoft, intégré à Windows Server et à Windows Pro/Entreprise |
| **VMware** | Type 1 (vSphere/ESXi) et type 2 (Workstation Pro) | Référence du marché en entreprise ; Workstation Pro est le poste de travail |
| **VirtualBox** | Type 2 (installé sur un système existant) | Hyperviseur d'Oracle, polyvalent et très répandu pour les postes de travail et les tests |

## 4. Cas d'usage et protocole de test

### 4.1 Cas d'usage identique

Une VM **Ubuntu Server** avec un serveur web **Apache**, configurée de la même façon sur les deux hyperviseurs testés :

| Paramètre | Valeur |
|---|---|
| vCPU | 2 |
| RAM | 2 Go |
| Disque | 20 Go |
| Réseau | NAT |
| Application | Apache, page de test |

### 4.2 Mesures relevées

Chaque mesure est faite **3 fois**, puis on garde la moyenne.

| Mesure | Outil / commande |
|---|---|
| Temps de démarrage de la VM | `systemd-analyze` |
| Performance du processeur | `sysbench cpu --threads=2 run` (événements par seconde) |
| Performance du disque | `dd if=/dev/zero of=test.img bs=1M count=1024 oflag=direct` |
| Mémoire utilisée sur l'hôte (VM au repos) | Gestionnaire des tâches (processus de l'hyperviseur) |
| Création et restauration d'un snapshot | Observation de la durée et du comportement |

## 5. Résultats des tests

### 5.1 Création de la VM sur chaque hyperviseur

![VMware Workstation : paramètres de la VM](A_AJOUTER)
*Paramètres de la VM sous VMware Workstation Pro.*

![VirtualBox : paramètres de la VM](A_AJOUTER)
*Paramètres de la VM sous VirtualBox.*

![Page web servie par la VM (VMware)](A_AJOUTER)
![Page web servie par la VM (VirtualBox)](A_AJOUTER)
*Serveur web fonctionnel sur les deux hyperviseurs.*

### 5.2 Mesures

| Mesure | VMware Workstation Pro | VirtualBox | Écart observé |
|---|---|---|---|
| Démarrage de la VM (`systemd-analyze`) | ___ s | ___ s | ___ |
| CPU (`sysbench`, événements/s) | ___ | ___ | ___ |
| Disque (`dd`, Mo/s) | ___ | ___ | ___ |
| RAM hôte au repos | ___ Mo | ___ Mo | ___ |
| Snapshot : création et restauration | ___ s | ___ s | ___ |

![Mesures sous VMware](A_AJOUTER)
![Mesures sous VirtualBox](A_AJOUTER)
*Captures des résultats (`systemd-analyze`, `sysbench`, `dd`).*

### 5.3 Observations

- Facilité d'installation et de configuration : ___
- Interface et prise en main : ___
- Différences notables : ___

## 6. Tableau comparatif

| Critère | Proxmox VE | Hyper-V | VMware (vSphere / Workstation) | VirtualBox |
|---|---|---|---|---|
| **Coût** | Logiciel gratuit ; abonnement optionnel de 120 à 1 100 €/an par processeur physique (2026) | Inclus avec Windows Server (licence Windows Server) et Windows Pro/Entreprise | vSphere : abonnement par cœur, au moins 16 cœurs facturés par processeur ; Workstation Pro : gratuit | Gratuit (version de base) |
| **Licences** | Open source ; l'abonnement donne accès au dépôt de mises à jour stable et au support | Licences Windows Server à prévoir selon le nombre de cœurs et de VM | Modèle par abonnement (Broadcom), tarifs non publics et en forte hausse | Pack d'extension : gratuit en usage personnel et éducatif, payant en entreprise |
| **Administration** | Interface web complète, ligne de commande | Hyper-V Manager, Windows Admin Center, PowerShell | vSphere Client / vCenter, très complet | Interface graphique simple, ligne de commande |
| **Performances** | Bonnes (KVM, type 1) | Bonnes (type 1) | Très bonnes (type 1) | Correctes pour des tests (type 2) |
| **Écosystème** | Communauté active, sauvegarde dédiée (Proxmox Backup Server) | Intégration Active Directory, outils Microsoft | Écosystème très large (sauvegarde, supervision, partenaires) | Communauté large, usage poste de travail |
| **Production** | Cluster, haute disponibilité, stockage Ceph intégrés | Cluster de basculement, réplication | Haute disponibilité, vMotion, vSAN | Non adapté à la production serveur |

> Les prix et licences ont été relevés en ligne en octobre 2026 : ils évoluent vite (surtout VMware), à revérifier avant toute décision.

## 7. Recommandation argumentée

### 7.1 Notation selon le scénario

Notes sur 5 (appréciation motivée par les critères ci-dessus, à ajuster avec tes tests) :

| Critère (poids) | Proxmox VE | Hyper-V | VMware vSphere | VirtualBox |
|---|---|---|---|---|
| Coût (5) | 5 | 3 | 1 | 5 |
| Licences (4) | 5 | 3 | 2 | 3 |
| Administration (4) | 4 | 4 | 5 | 3 |
| Performances (3) | 4 | 4 | 5 | 2 |
| Écosystème (4) | 4 | 4 | 5 | 3 |
| Production (4) | 5 | 4 | 5 | 1 |
| **Total pondéré (sur 120)** | **108** | **87** | **87** | **70** |

### 7.2 Recommandation

Pour le scénario d'exemple (PME, budget limité, administrateur à l'aise avec Linux), je recommande **Proxmox VE**.

- **Coût et licences** : le logiciel est gratuit et le coût éventuel est limité à un abonnement par processeur, sans frais par VM ni par cœur.
- **Fonctions de production** : cluster, haute disponibilité et sauvegarde sont intégrés, ce qui répond au besoin d'évolution.
- **Administration** : une interface web suffit à un seul administrateur.

**Alternatives selon le contexte :**

- **Hyper-V** si l'entreprise est déjà très intégrée à Windows Server et à Active Directory, avec des licences Microsoft existantes.
- **VMware vSphere** si l'infrastructure VMware existe déjà et que le budget permet l'abonnement par cœur, avec son écosystème étendu.
- **VirtualBox** reste un outil de test et de formation, pas une solution de production serveur.

> ⚠️ Si le scénario du formateur est différent (grande entreprise, parc Windows, contrainte de support 24/7...), la recommandation doit être adaptée.

## 8. Plan de la présentation (5 minutes)

| # | Diapositive | Contenu | Durée |
|---|---|---|---|
| 1 | Contexte | Scénario client et besoin | 30 s |
| 2 | Critères | Les 6 critères et leur poids | 30 s |
| 3 | Solutions | Les 4 hyperviseurs en une phrase chacun | 30 s |
| 4 | Tests | Cas d'usage identique et résultats mesurés (VMware et VirtualBox) | 1 min |
| 5 | Tableau comparatif | Synthèse et notation | 1 min 30 |
| 6 | Recommandation | Choix argumenté et alternatives | 1 min |

## 9. Limites de l'étude

- Les deux solutions testées (VMware Workstation et VirtualBox) sont de **type 2** et tournent sur un poste de travail : leurs performances ne représentent pas celles d'un hyperviseur de **type 1** sur un serveur.
- Proxmox VE et Hyper-V sont comparés sur documentation et critères objectifs, sans test pratique.
- Les mesures varient selon la machine hôte et la charge au moment du test.
- Les tarifs évoluent, surtout ceux de VMware.

## Sources consultées

- Tarifs Proxmox VE : https://www.proxmox.com/proxmox-ve/pricing
- Licences VMware (gratuité de Workstation Pro, tarification par cœur de vSphere) : https://next.ink/brief-article/vmware-workstation-pro-et-fusion-pro-desormais-gratuits-en-usage-commercial/ et https://vates.tech/en/pricing-and-support/vmware-cost-calculator
- Licence du pack d'extension VirtualBox : https://open.windriver.com/info/uni-license-list/licenses/oracle-vb-puel-12.html
