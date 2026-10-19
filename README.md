# Sokoban en C
Jeu de logique Sokoban en C avec raylib

Projet académique : Structures de données avancées et programmation structurée.

## Membres du groupe

| Nom | Rôle |
|---|---|
| EYAMBE NADIANGI CHRISTIAN DAVY | Chef de projet |
| WAMBO NOEL | Membre |
| NDE TIWA NEL ARCHANGE | Membre |
| NOUTACKDIE ELISABETH CASSANDRA | Membre |

## Description
Sokoban est un jeu de logique. Le joueur se déplace dans un entrepôt et pousse des caisses pour les placer sur des cibles. Il ne peut pousser qu'une caisse à la fois, et seulement si la case derrière est libre.

## Règles
1. Le joueur se déplace avec les flèches ou W A S D.
2. Il ne peut pousser qu'une caisse à la fois.
3. Une caisse ne peut pas être poussée contre un mur ou une autre caisse.
4. La touche U annule le dernier coup.
5. La touche R recommence le niveau.
6. La partie est gagnée quand toutes les caisses sont sur les cibles.

## Format des niveaux
Les niveaux sont écrits dans un fichier texte (par exemple `niveaux/niveau1.txt`). Dans ce fichier, les symboles suivants décrivent la grille :

| Symbole | Signification |
|---|---|
| `#` | mur |
| espace | sol |
| `$` | caisse |
| `.` | cible |
| `*` | caisse sur une cible |
| `@` | joueur |
| `+` | joueur sur une cible |

Dans la fenêtre du jeu, ces éléments sont affichés sous forme de formes colorées : murs marron foncé, sol beige, cibles en rouge, caisses en marron (vertes lorsqu'elles sont sur une cible) et joueur en bleu.

## Structures de données
- **Matrice** : grille du niveau et position des caisses.
- **Pile** (liste chaînée) : historique des coups, pour l'annulation.
- **Fichiers** : chargement des niveaux depuis un fichier texte.

## Statut
Projet en cours. Le code source sera ajouté progressivement.
