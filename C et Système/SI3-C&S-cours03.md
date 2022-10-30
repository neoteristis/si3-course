# SI3 - C et Système - Cours 3
---

Source : 
- [[Summary - SI3 - C et Système]]
- [[SI3-C&S-03-enonces-expressions.pdf]]
Tags : #C
Date : 2022-10-17

---
#### Énoncé composé

Un énoncé composé (ou bloc) sert à : 
- regrouper plusieurs énoncés
- restreindre la visibilité d'une variable
- dénoter le corps d'une fonction

---
#### Énoncés

`if` : 
0 <=> faux
autre <=> vrai

`switch` 
À partir du moment où un cas est valide, le programme passe sur tous les énonces suivants même s'il ne respecte pas le cas du dit énoncé. Il est obligatoire d'utiliser `break` pour sortir du `switch`.

`while` et `do while`
- un `while` peut ne pas s'éxécuter
- un `do`  s'exécute au moins une fois 

`for`
```c
for (<initialisation>; <condition>; <increment>)
	<action>
```
est équivalent à 
```c
<initialisation>
while (<condition>) {
	<action>;
	<increment>;
}
```

`break`
- utilisé dans une boucle ou un switch pour en sortir

`continue`
- utilisé dans les boucles pour pouvoir passer au cas suivant de la boucle

`return`
- sort de la fonction courante
- donne le résultat de la fonction

---
#### Expressions - Opérateurs

- une expression fournit une valeur
- un énonce change un état
- En C, n'importe quelle expression peut être transformée en énoné en lui ajoutant un **;**

```c
x = 1; 123 ; y = 2;
/* ici 123 est 'oublié'*/
```

##### Affectation

- utilise le signe **=** 
- est à la fois un énoncé et une expression
	- a un effet de bord (valeur de l'opérande guache est changée)
	- a un résultat (lopérande gauche après affectation)
	- a un type (type de l'opérande gauche)
	- peut être utilisée de façon multiple
	- peut être composé avec un opérateur $\Theta$
		- $x \Theta = y \Leftrightarrow x = x \Theta y$
		- Liste des opérateurs : 

Opérateur préfixe et postfixe : 
`++i`  et  `i++`
`--i`  et  `i--`

```c
i = 3; j = 3;
printf("i = %d j = %d", i++, ++j); /* 3 and 4*/
printf("i = %d j = %d", i, j); /* 4 and 4*/
```

ATTENTION
```c
t[i++] = v[i++]; /* ??? */
printf("%d %d", i++, i++); /* ??? */
```

---
#### Opérateurs sur les types

`sizeof`
```c
sizeof(type)
sizeof(variable)
```

Conversion explicite : cast
```c
(type) expr
/* expr va être dans converti dans le type "type"*/
(int) 2.0
3 / (float) 4 /* = 0.75 alors que 3/4 = 0 */
```

---
#### Conversions de type implicites

- les règles de conversions sont assez complexes
- en gros, convertir vers le type le plus grand
	- promotion entière (sous-types de `int` => `int`)
	- ensuite : 
		- long
		- ...
	- On omet les nombres complexes et les `long long`

Dans une affectation
```c
the_char = 0xabcdef; /* the_char == 0xef */
the_int = 2.3; /* the_int == 2 */
the_float = 2; /* the_float == 2.0 */
```
- les bits supplémentaires sont perdus

Dans le passage de paramètre : 
- règles identiques à celles de l'affectation

- conversions *value preserving* sont toujours légales
- conversions non *value preserving* provoquent un *warning*
	- il faut préciser le cast explicitement pour enlever le warning si on est sûr de ce que l'on fait

---
#### Opérateurs de conditions

Opérateur ternaire
```c
condition? expr1 : expr2
```

```c
int min (int a, int b)
{
	return (a < b) ? a : b;
}

abs_of_x = (x < 0) ? -x : x;
```

---
#### Opérateur virgule

- permet de séparer deux expressions
- permet de mettre plusieurs expressions là où la syntaxe n'en permet qu'une -> dans les boucles

---
#### Priorités des opérateurs

GROS TABLEAU SUR LE DIAPO

Si a un doute sur l'ordre d'évaluation, on met des parenthèses.

---
#### Exemple `strcat()`

- permet de concaténer deux chaînes de caractères
- 3 versions disponibles sur le diapo

---
#### Exemple : conversion `atoi`

- character array to integer
- défini dans une bibliothèque C

---
#### Résumé : structures de contrôle

- Tests
	- Énoncé `if`
	- Énoncé `switch`
	- Expression conditionnelles `? : `
- Itérations
	- Énoncé `for`
	- Énoncé `while`
	- Énoncé `do while`
	- Énoncé `break`
	- Énoncé `continue`
	- Énoncé `goto` -> permet de faire du traitement d'exception artificiellement mais à utiliser avec parcimonie
