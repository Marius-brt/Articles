## Introduction

Dans cet article, nous allons explorer un solveur d'expressions mathématiques en C++ que j'ai développé pour faciliter l'évaluation d'expressions complexes. Ce solveur utilise une approche basée sur les piles (stacks) pour gérer les opérations et les valeurs lors de l'évaluation de l'expression.
Il supporte l'utilisation de parenthèses, de puissances, de nombres négatifs et décimaux.

## Explication du code

Le programme est organisé en plusieurs parties :

### Fonction de précédence

```cpp
int precedence(char op) {
	if (op == '+' || op == '-')
		return 1;
	if (op == '*' || op == '/' || op == '^')
		return 2;
	return 0;
}
```

Cette fonction attribue des niveaux de priorité aux opérateurs mathématiques. Les opérateurs avec une priorité plus élevée seront évalués en premier.

### Fonction de calcul

```cpp
float calculate(float a, float b, char op) {
    switch (op) {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/': return a / b;
        case '^': return pow(a, b);
    }
}
```

La fonction `calculate` effectue les opérations mathématiques de base en fonction de l'opérateur donné.

### Fonction solve

La fonction solve est la pièce maîtresse du solveur. Elle parcourt l'expression mathématique et utilise des piles pour gérer les opérations et les valeurs.

## Détails de l'implémentation
### Gestion des parenthèses
Le solveur prend en charge les parenthèses pour définir l'ordre d'évaluation. Lorsqu'une parenthèse ouvrante est rencontrée, elle est ajoutée à la pile des opérateurs. Lorsqu'une parenthèse fermante est trouvée, le solveur évalue toutes les opérations à l'intérieur des parenthèses.

```cpp
if (ex[i] == '(')
    ops.push(ex[i]);
else if (ex[i] == ')') {
    while (!ops.empty() && ops.top() != '(') {
        // ... (voir le code complet sur github)
    }
    if (!ops.empty())
        ops.pop();
}
```
### Gestion des nombres négatifs
Le solveur prend également en charge les nombres négatifs, identifiant les opérateurs de soustraction et les traitant correctement lorsqu'ils sont à la position initiale ou après une parenthèse ouvrante.

```cpp
else if (is_digit(ex[i]) || (ex[i] == '-' && (i == 0 || ex[i-1] == '(')))
```
### Boucle principale
La boucle principale parcourt l'expression, évaluant les opérations en fonction de la priorité des opérateurs.

```cpp
while (!ops.empty()) {
    // ... 
}
```
## Conclusion
Ce solveur d'expressions mathématiques en C++ offre une solution flexible et efficace pour évaluer des expressions complexes. En utilisant des piles pour gérer les opérations, il garantit une évaluation correcte et respecte les règles de priorité des opérateurs.