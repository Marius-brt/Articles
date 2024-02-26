Ce projet avait pour but de créer un algorithme basique de pathfinding en C.
Il ne trouve pas toujours le chemin le plus court mais il est un bon compromis entre la vitesse de calcul et la longueur du chemin.

## Exemple de chemin

On peut représenter le chemin par une matrice de caractères :
- `x` = position de départ
- `o` = objectif
- `#` = obstacle
- .` = case vide

Voici un exemple de matrice de 8 par 5 :
```bash
x . . # . . . .
# . . . . . . .
. . . # . . . .
. . . # . # . .
. . . . . o . .
```

En lançant l'algorithme, on obtient le chemin suivant (avec `* pour représenter le chemin) :

```bash
x * * # . . . .
# . * . . . . .
. . * # . . . .
. . * # . # . .
. . * * * o . .
```