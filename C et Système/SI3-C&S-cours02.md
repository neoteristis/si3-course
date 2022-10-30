# SI3 - C et Système - Cours 2
---

Source : 
- [[Summary - SI3 - C et Système]]
- [[SI3-C&S-02-variables-constantes-types.pdf]]
Tags : #C #variable #constant #data-type 
Date : 2022-10-10

---
#### Identificateurs

`_` : considéré comme une lettre

[[C - Keywords]]

`auto` -> backward compatibility pour pouvoir faire des variables locales
-> quasiment jamais utilisé

`register` : allouer la variable dans un registre du processeur au lieu de le faire classiquement

---
#### Types simples

| Type              | C declaration          |
| ----------------- | ---------------------- |
| character         | `char`                 |
| short integer     | `short int` ou `short` |
| integer           | `int`                  |
| long integer      | `long int` ou `long`   |
| long long integer | `long long int`        |
Each integer type can be signed or not

\[`unsigned` | `signed`\] `char`
\[`unsigned` | `signed`\] \[`long`\] \[`short` | `long`\] \[`int`\]

`signed` by default

---

Les constantes entières sont décimales par défaut

---

Type booléen `_Bool` (apport C99)
- souvent utilisé avec le fichier [[C - stdbool | stdbool.h]]
	- `bool` est équivalent à `_Bool`
	- `false` -> 0
	- `true` -> 1
- On peut se passer de ce type
	- `0` est faux
	- toute autre valeur est vraie

Le type booléen est très très peu utilisé en C.

---
#### Déclaration de variables

```c
/* déclarations simples */
int x;
int a, b, c;
/* déclaration et initialisation */
unsigned int v1 = 0xabcd;
unsigned long int v2, v3 = 1234UL; // only v3 is initialized
float v4 = 123.45,
	  v5 = 0.0;
/* déclarations de constantes */
const int size = 100;
const double Pi = 3.14159;
```

Rien n'est défini dans la norme C concernant la taille des types simples. C'est donc toujours >= à quelque chose.
La seule chose qui est sûre est que `sizeof(char) == 1` par définition.

---
#### Types tableau

- Borne inférieur est toujours égale à 0
- Possibilité d'initialiser un tableau dès sa déclaration
`t[3][10]` -> tableau de 3 lignes et 10 colonnes

Si on déclare un tableau sans rien initialiser -> le compilateur met ce qu'il veut dedans.
Si on déclare un tablea avec initialisation -> il remplit ce qui n'est pas initialisé par des 0.

La dimension peut être calculée automatiquement par le compilateur mais seule la première dimension peut être omise.

---
#### Chaînes de caractères

> [!warning] Warning
> La chaîne de caractères n'est pas un type C mais un tableau.
> Le dernier élément du tableau est `\0`. 

Si on déclare un tableau de caractère, le `\0` n'est pas aujouté automatiquement.
Donc dans un tableau de taille `n` on ne peut mettre que `n-1` caractères car il faut laisser une place pour le `\0`.

```c
char string1[100],

string1 = "I'm a string";
// Le \0 est automatiquement ajouté
```

---
#### Types énumérés

- Permettent de nommer des constantes

Si pas initialisé, chaque constante de l'énum est associé à un nombre dans l'ordre croissant
Les valeurs des constantes peuvent être spécifiées par l'utilisateur.

Les `enum` sont assez peu utilisé en réalité.

---
#### Structures

[[C - Structure]]

---
#### Unions

- Semblable aux structures mais où un seul champ n'est valide à un instant donné
- Utile pour : 
	- partager de la mémoire entre des objets qui sont accédés exclusivement
	- interpréter la représentation interne d'un objet comme s'il était d'un autre type

Dans une union, une seule des variables de l'union peuvent être utilisées.
Cela permet, en fonction des cas, d'utiliser seulement la place de la plus grande variable de l'union.

Quand un emplacement est créé en mémoire, c'est aligné avec le système (32 bits, 64 bits) pour aller plus vite. Donc il y a perte de mémoire.

---
#### Champs de bits

- peuvent être utilisés pour des accès de bas niveau

Permet de spécifier la taille en bit que doit prendre une variable
`unsigned int day : 5` -> ce sera un `int` de 5 bits

---
#### Complexes

Permet d'avoir des nombres complexes avec une partie réelle et une partie imaginaire.

---
#### Définition de types (typedef)

- Permet de simplifier l'écriture en donnant un nom à un type

```c
typedef struct {
	int x, y;
} Position; /* Position est une struct. de 2 entiers */

typedef enum {false, true} Boolean; /* ~ _Bool */
```

