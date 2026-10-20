# 📦 Sokoban en C

Jeu de logique Sokoban en langage C avec interface graphique (raylib), réalisé dans le cadre du cours **Structures de données avancées et programmation structurée**.

## 👥 Équipe (Groupe)

| Nom & prénom | Rôle |
|---|---|
| EYAMBE NADIANGI CHRISTIAN DAVY | Chef de projet : dépôt Git, pile d'annulation, déplacements, intégration |
| WAMBO NOEL | Développeur : chargement des niveaux, règles de victoire, niveaux |
| NDE TIWA NEL ARCHANGE | Développeur : affichage et contrôles, tests |
| NOUTACKDIE ELISABETH CASSANDRA | Membre : tests, documentation |

## 📝 Description

Sokoban est un jeu de réflexion. Le joueur se déplace dans un entrepôt et pousse des caisses pour les placer sur des cibles. Il ne peut pousser qu'une caisse à la fois, et seulement si la case derrière elle est libre. Une partie se gagne quand toutes les caisses sont sur les cibles.

## ✨ Fonctionnalités

- Chargement de niveaux depuis un fichier texte (un niveau = un fichier).
- Déplacements au clavier, avec poussée des caisses.
- Annulation illimitée des coups (touche U), grâce à une pile.
- Recommencer le niveau (touche R).
- Compteur de coups.
- Détection automatique de la victoire, avec message « Niveau terminé ! ».

## 🎮 Règles du jeu

1. Le joueur se déplace d'une case à la fois, avec les flèches ou W A S D.
2. Il ne peut pousser qu'une seule caisse à la fois.
3. Une caisse ne peut pas être poussée contre un mur ou contre une autre caisse.
4. La partie est gagnée quand toutes les caisses sont sur les cibles.

## ⌨️ Commandes

| Action | Touche |
|---|---|
| Déplacer le joueur | Flèches ou W A S D |
| Annuler le dernier coup | U |
| Recommencer le niveau | R |
| Quitter | Échap (ou fermer la fenêtre) |

## 🖥️ Installation et lancement

### Windows (MSYS2 UCRT64)

1. Installez **MSYS2** depuis [msys2.org](https://www.msys2.org). Gardez le dossier d'installation par défaut (`C:\msys64`), sans accent.
2. Ouvrez **MSYS2 UCRT64** (pas MSYS2 MSYS ni MINGW64).
3. Installez les outils (une seule fois) :

```bash
   pacman -S mingw-w64-ucrt-x86_64-gcc make mingw-w64-ucrt-x86_64-raylib mingw-w64-ucrt-x86_64-pkgconf
```

4. Placez le dossier du projet dans `C:\msys64\home\<votre-nom>\sokoban`, puis compilez et lancez :

```bash
   cd sokoban
   make
   ./sokoban.exe niveaux/niveau1.txt
```

### Linux (Ubuntu / Debian)

```bash
sudo apt install build-essential libraylib-dev pkg-config
make
./sokoban niveaux/niveau1.txt
```

### Commandes make

| Commande | Effet |
|---|---|
| `make` | compile le programme (`sokoban` ou `sokoban.exe`) |
| `make clean` | supprime le programme compilé |

## 🗂️ Structure du projet

```
sokoban/
├── Makefile          # règles de compilation
├── README.md         # cette documentation
├── src/
│   ├── main.c        # fenêtre, boucle principale, affichage, contrôles
│   ├── jeu.h         # structures Niveau et Position, prototypes
│   ├── jeu.c         # chargement du niveau, déplacements, annulation, victoire
│   ├── pile.h        # structures Coup et Pile
│   └── pile.c        # empiler, depiler, libérer la pile
└── niveaux/
    └── niveau1.txt   # premier niveau
```

## 🧩 Format des niveaux

Chaque niveau est un fichier texte. La grille est décrite avec les symboles suivants :

| Symbole | Signification |
|---|---|
| `#` | mur |
| espace | sol |
| `$` | caisse |
| `.` | cible |
| `*` | caisse sur une cible |
| `@` | joueur |
| `+` | joueur sur une cible |

Pour créer un niveau, il faut :
- un seul joueur (`@` ou `+`) ;
- autant de caisses que de cibles ;
- des murs `#` autour de la zone de jeu.

Limites : 20 lignes et 30 colonnes au maximum (définies dans `src/jeu.h`).

Dans la fenêtre, ces éléments sont affichés sous forme de formes colorées : murs marron foncé, sol beige, cibles rouges, caisses marron (vertes sur une cible) et joueur bleu.

## 🧠 Structures de données (lien avec le cours)

| Structure | Fichier | Rôle |
|---|---|---|
| Matrice (tableau 2D) | `jeu.h` / `jeu.c` | grille du niveau (`sol`) et position des caisses (`caisse`) |
| Structure (`struct`) | `jeu.h`, `pile.h` | `Niveau`, `Position`, `Coup` |
| Pile (liste chaînée) | `pile.c` | historique des coups : le dernier coup joué est le premier annulé (LIFO) |
| Fichiers | `jeu.c` | chargement des niveaux depuis un fichier texte |

## 🔁 Fonctionnement de l'annulation

À chaque déplacement, le programme empile un `Coup` contenant la direction et le fait qu'une caisse a été poussée. Pour annuler, il dépile le dernier coup et fait l'inverse : il remet la caisse à sa place si elle avait été poussée, puis recule le joueur.

## 🌿 Organisation Git

- `main` : version stable du projet.
- Une branche par membre ou par fonctionnalité (par exemple `christian-pile`, `noel-chargement`).
- Commits clairs : `feat: ...`, `fix: ...`, `docs: ...`.
- Intégration par Pull Request, validée par le chef de projet.

## 📄 statut

Projet pédagogique, ISESTMA 2026-2027.
Projet en cours. Le code source sera ajouté progressivement.
