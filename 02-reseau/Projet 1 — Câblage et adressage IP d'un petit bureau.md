# Projet 1 — Câblage et adressage IP d'un petit bureau


## 1. Objectif

Câbler et adresser le réseau d'un petit bureau dans GNS3 : 8 postes reliés à un switch, et un routeur R1 qui sert de passerelle. Puis vérifier que tous les postes communiquent entre eux et avec la passerelle.

## 2. Étape 1 : schéma du réseau

### 2.1 Topologie dans GNS3

![Capture d'écran 2026-10-13 094342](https://hackmd.io/_uploads/SkzH-Piofl.png)

### 2.2 Schéma annoté

```mermaid
graph TB
 R1["R1 – Routeur / passerelle<br/>g0/0 : 192.168.10.1/24"]
 SW["Switch<br/>Ethernet switch GNS3"]
 PC1["PC1<br/>192.168.10.11/24"]
 PC2["PC2<br/>192.168.10.12/24"]
 PC3["PC3<br/>192.168.10.13/24"]
 PC4["PC4<br/>192.168.10.14/24<br/>(injoignable : bug GNS3)"]
 PC5["PC5<br/>192.168.10.15/24"]
 PC6["PC6<br/>192.168.10.16/24"]
 PC7["PC7<br/>192.168.10.17/24"]
 PC8["PC8<br/>192.168.10.18/24"]

 R1 ---|"g0/0 – e8"| SW
 SW --- PC1
 SW --- PC2
 SW --- PC3
 SW -.- PC4
 SW --- PC5
 SW --- PC6
 SW --- PC7
 SW --- PC8
```

## 3. Étape 2 : plan d'adressage IP

| Paramètre | Valeur |
|---|---|
| Réseau | 192.168.10.0/24 |
| Masque | 255.255.255.0 |
| Passerelle | 192.168.10.1 (R1, g0/0) |

| Équipement | Interface | Adresse IP | Masque | Passerelle |
|---|---|---|---|---|
| R1 | g0/0 | 192.168.10.1 | 255.255.255.0 | n/a |
| PC1 | e0 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| PC2 | e0 | 192.168.10.12 | 255.255.255.0 | 192.168.10.1 |
| PC3 | e0 | 192.168.10.13 | 255.255.255.0 | 192.168.10.1 |
| PC4 | e0 | 192.168.10.14 | 255.255.255.0 | 192.168.10.1 |
| PC5 | e0 | 192.168.10.15 | 255.255.255.0 | 192.168.10.1 |
| PC6 | e0 | 192.168.10.16 | 255.255.255.0 | 192.168.10.1 |
| PC7 | e0 | 192.168.10.17 | 255.255.255.0 | 192.168.10.1 |
| PC8 | e0 | 192.168.10.18 | 255.255.255.0 | 192.168.10.1 |

## 4. Étape 3 : câblage

| Liaison | Port source | Port destination | Câble |
|---|---|---|---|
| PC1 à PC8 → Switch | e0 de chaque PC | ports e0 à e7 du switch | Ethernet droit |
| Switch → R1 | e8 | g0/0 | Ethernet droit |

**Légende :**

- Réseau du bureau : `192.168.10.0/24`, passerelle `192.168.10.1`.
- Postes : PC1 à PC8 en IP statique, de `192.168.10.11` à `192.168.10.18`.
- Trait pointillé : liaison touchée par le bug de GNS3 (voir partie 7).

## 5. Étape 4 : configuration des PC et du routeur

Chaque poste reçoit son adresse IP, son masque et sa passerelle, et l'interface `g0/0` du routeur R1 est configurée en `192.168.10.1/24`.

![Capture d'écran 2026-10-12 094031](https://hackmd.io/_uploads/BkfVGM5jGx.png)
![Capture d'écran 2026-10-12 094130](https://hackmd.io/_uploads/rkGNzfqiGx.png)
![Capture d'écran 2026-10-12 094250](https://hackmd.io/_uploads/ryG4GM9jGg.png)
![Capture d'écran 2026-10-12 094454](https://hackmd.io/_uploads/ryfVzfqiGe.png)
![Capture d'écran 2026-10-12 094634](https://hackmd.io/_uploads/SkMEGGcjMg.png)
![Capture d'écran 2026-10-12 094757](https://hackmd.io/_uploads/rylzNGfciGl.png)
![Capture d'écran 2026-10-12 095108](https://hackmd.io/_uploads/Byf4MG9jfl.png)
![Capture d'écran 2026-10-12 095217](https://hackmd.io/_uploads/SkzEGfcjGg.png)
![Capture d'écran 2026-10-12 103517](https://hackmd.io/_uploads/HJFZDS9ofl.png)
![Capture d'écran 2026-10-12 104223](https://hackmd.io/_uploads/ry7MvS5sGe.png)
![Capture d'écran 2026-10-12 111011](https://hackmd.io/_uploads/ry5XPScozx.png)
![Capture d'écran 2026-10-12 131927](https://hackmd.io/_uploads/r1gHDHcozx.png)
![Capture d'écran 2026-10-12 132230](https://hackmd.io/_uploads/BJoHPBciGl.png)

## 6. Test et résultat

Je teste la connectivité avec des pings entre les postes et vers la passerelle.

![Capture d'écran 2026-10-12 132912](https://hackmd.io/_uploads/HJ7fOIosfx.png)
![Capture d'écran 2026-10-12 132921](https://hackmd.io/_uploads/SJTz_LooGe.png)
![Capture d'écran 2026-10-13 090349](https://hackmd.io/_uploads/HyLmOLsoMe.png)
![Capture d'écran 2026-10-13 090358](https://hackmd.io/_uploads/B1CQ_8iize.png)
![Capture d'écran 2026-10-13 090756](https://hackmd.io/_uploads/BJEkFIjjze.png)
![Capture d'écran 2026-10-13 090800](https://hackmd.io/_uploads/Sk31Y8jjMe.png)
![Capture d'écran 2026-10-13 091050](https://hackmd.io/_uploads/BkvqtIjizg.png)
![Capture d'écran 2026-10-13 091059](https://hackmd.io/_uploads/Hy1jF8joGl.png)
![Capture d'écran 2026-10-13 091406](https://hackmd.io/_uploads/SJPU58soMl.png)
![Capture d'écran 2026-10-13 091311](https://hackmd.io/_uploads/SJl45Iosfx.png)
![Capture d'écran 2026-10-13 091623](https://hackmd.io/_uploads/ByyljIjizx.png)
![Capture d'écran 2026-10-13 091635](https://hackmd.io/_uploads/rk6xjIisMx.png)
![Capture d'écran 2026-10-13 091845](https://hackmd.io/_uploads/B1fOi8soze.png)
![Capture d'écran 2026-10-13 091855](https://hackmd.io/_uploads/HkqdjIjjGe.png)

| Test | Résultat |
|---|---|
| PC1, PC2, PC3, PC5, PC6, PC7, PC8 vers la passerelle et entre eux | ✅ |
| Tous les postes vers PC4 | ❌ Injoignable (bug GNS3) |
| PC4 vers les autres postes et la passerelle | ❌ Injoignable (bug GNS3) |

## 7. Difficultés rencontrées


> ⚠️ PC4 n'a pas pu être pingué par les autres postes, ni joindre le routeur R1, à cause d'un bug de GNS3.


**Symptômes observés :**

- Depuis PC1, `ping 192.168.10.14` répond `host (192.168.10.14) not reachable`.
- PC4 ne parvient pas à joindre la passerelle `192.168.10.1`.
- Les autres postes communiquent normalement entre eux et avec le routeur.

**Vérifications effectuées :**

- Adressage de PC4 contrôlé avec `show ip` (`192.168.10.14/24`, passerelle `192.168.10.1`).
- Câble de PC4 vérifié dans GNS3.
- Redémarrage de PC4, puis de l'application GNS3.

Le problème est resté malgré ces manipulations. L'adressage et la configuration de PC4 sont corrects : la panne vient du simulateur, pas du plan d'adressage ni de la configuration.

Ping de PC1 vers `192.168.10.14` :

![Capture d'écran 2026-10-13 093053](https://hackmd.io/_uploads/HJepALoiMx.png)

## 8. Conclusion

Le réseau du bureau est câblé et adressé dans le réseau `192.168.10.0/24`, avec R1 comme passerelle. Tous les postes communiquent entre eux et avec la passerelle, sauf PC4, bloqué par un bug de GNS3 alors que sa configuration est correcte.
