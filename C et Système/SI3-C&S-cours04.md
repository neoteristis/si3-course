# SI3 - C et Système - Cours 4
---

Source : 
- [[Summary - SI3 - C et Système]]
- [[SI3-C&S-04-fonctions-variables-input-output.pdf]]
Tags : #C #C-functions #C-variables #C-input-output
Date : 2022-10-24

---
#### Définition de fonction K&R

```c
type_resultat nom(parametre)
	types des parametres
{
	corps de la fonction
}
```

Exemple : 

```c
int max(a, b)
	int a, b;
{
	return (a > b) ? a : b;
}
```

Si ce n'est pas précisé, le type par défaut est `int`.

Problèmes : 
- pas de vérification du type des paramètres
- pas de vérification du nombre de paramètres
- pas d'erreur ni de warning
Donc : ==NE JAMAIS UTILISER LA FORME K&R==
Cette méthode n'apporte que des problèmes.

---
#### Définition de fonction ANSI

La norme ANSI redéfinit la façon de définir une fonction avec des prototypes

```c
type_resultat nom(liste typée de paramètres) {
	corps de la fonction
}
```

Exemple : 

```c
int max(int a, int b) {
	return (a > b) ? a : b;
}
```

On est obligé de donner le type de chacune des variables.
Si on se trouve de type, le compilateur donne une erreur.

- Type de résultat : 
	- `void` : pas de type => procédure
	- n'importe quel type scalaire (entier, réel, pointeur, enum)
	- structure et union
	- Attention : ==pas de tableau==
- Types des paramètres
	- n'importe quel type scalaire (entier, réel, pointeur, enum)
	- structure et union
	- tableau
		- paramètre formel et paramètre effectif doivent être compatibles (cf. pointeurs)
		- la taille peut être spécifiée ou non

---
#### Résultat de la fonction

- La valeur de la fonction est donné par l''énoncé `return`
- Type de résultat : celui donné à la définition de la fonction
- Conversion éventuelle de la valeur du `return` vers le type de fonction (exemple int -> float)
- Si la fonction est de type `void`, on peut utiliser `return` sans valeur après

---
#### Passage de paramètre

- Un seul mode : passage par valeur
- Pour les tableaux, on passe un pointeur sur le début du tableau (par valeur)

```c
void f(int x) {
	x = x + 1;
	printf("In function f : %d\n", x);
}

void main(void) {
	int a = 1;
	f(a);
	prinf("After call to f : %d\n", a)
}

==> In function f : 2
	After call to f : 1
```

- L'ordre d'évalutation n'est pas garanti

```c
i = 5
f(i++, t[i]) /* t[5] ou t[6] ??*/
```

---
#### Déclaration de fonction

- Déclarer une fonction = donner son type avec un header ou prototype
- C'est utile : 
	- si la fonction est utilisée "en avant"
	- si la fonction est définie dans un autre fichier
- Définition K&R
```c
double cos(); /* paramètres absents (inutiles) */
```
- Définition ANSI
```c
double cos(double x); /* en-tête complet */
```

- Si utilisation de la fonction sans prototype
	- auto déclaration de la fonction par le compilateur -> il met un warning
	- résultat de type entier
	- pas de contrôle du nombre et du type des paramètres

Même en ANSI C, la rétro compatibilité avec le C de K&R peut être source d'erreurs.

---
#### Fonctions à arité variable

- C'est une extension ANSI
- La liste de paramètres variable est dénotée par "..." après le dernier paramètre fixe
- Il doit y avoir au moins un paramètre fixe
- On ne peut avoir qu'un seul type de paramètre dans la liste

```c
#include <stdarg.h>
void ma_fonction(type1 arg1, type2 arg2, ...) {}
```

Le fichier `<stdarg.h>` définit les macros suivantes : 
```c
void va_start(va_list ap, last_fixed_parameter)
type va_arg(va_list, ap, type)
void va_end(va_list ap)
```

##### Exemple

```c
#include <stdarg.h>
int max(int first, ...) { /* Liste terminée par un nombre < 0 */ 
	va_list ap; 
	int M = 0; 
	va_start(ap, first); 
	while (first > 0) { 
		if (first > M) M = first; 
		first = va_arg(ap, int); 
	} 
	va_end(ap); 
	return M; 
} 

void main(void) { 
	int x = max(12, 18, 17, 20, 1, 34, 5, -1); 
	... 
}
```

---
#### Variables

##### Globale et locale

- On ne considère ici que les programmes mono fichier
- Variable globale : 
	- Définition en dehors d'un bloc
	- Durée de vie : tout le programme
	- Visibilité : depuis son point de définition jusqu'à la fin de fichier (avec possibilité de masquage d'un bloc)
- Variable locale
	- Définition : dans un bloc
	- Durée de vie : la durée de vie du bloc
	- Visibilité : restreinte au bloc de définition

```c
int counter = 0;

int f(void) {
	counter += 1; /* incrementing the global variable */ 
	x += 1; /* error: x unknown */
}

int x; /* now, x is known */

int g(void) {
	int counter = 0; /* mask global variable */ 
	counter += 1; /* incrementing the local variable */ 
	x += 1;
}
```

##### Statique

- Toujours dans le cas de programmes mono-fichiers
- Variable statique : 
	- Définition : dans le bloc (doit être préfixée par `static`)
	- Durée de vie : tout le programme (comme une globale)
	- Visibilité : restreinte au bloc de définition (comme une locale)

```c
void f1(void) {
    static int counter = 0;
    printf("f1 was called %d times\n", ++counter);
}

void f2(void) {
    static int counter = 0;
    printf("f2 was called %d times\n", ++counter);
}

void main(void) {
    f1(); f2(); f1();
}

==> f1 was called 1 times
    f2 was called 1 times
    f1 was called 2 times

// Le counter dans f1 est différent du counter dans f2.
// On voit bien que la valeur de la variable existe encore une fois sortie de la
// fonction f1 puisqu'une fois que l'on rappelle f1, le résultat est 2.
```

---
#### I/O avec format

```c
int printf(const char *format, ...);
``` 
- le format spécifie le nombre, le type et les contraintes sur la représentation textuelle des expressions passées dans la liste variable

```c
int scanf(const char *format, ...)
```
- [ ] A COMPLETER

`sprintf` et `sscanf`
- identique à `printf` et `scanf` mais l'I/O se fait dans une chaîne au lieu d'un fichier

`snprintf`
- la taille de la chaîne résultat est passée en paramètre (plus sûr)
- [ ] EXEMPLE

`vprintf` et `vscanf`
- I/O avec une liste variable d'arguments

---
#### Le type `FILE`

- Le type `FILE` est défini dans `<stdio.h>`
- Un objet de type `FILE` est un flux
	- supporte accès séquentiel et direct
	- accès par caractère
	- I/O bufferisées
		- avant d'être envoyé sur le terminal, c'est d'abord stocké en mémoire
		- dans le cas du terminal c'est bufferisé par ligne donc il attend d'avoir toute la ligne avant d'imprimer quelque chose au lieu de le faire caractère par caractère

Ouverture d'un fichier : 
```c
FILE *fopen(const char *name, const char *mode);
/* mode peut être "r", "w", "a", ... */
```

Fermeture d'un fichier : 
```c
int fclose(FILE *fp);
/* renvoie 0 si OK et EOF sinon */
```

Beaucoup de fonctions sur la lecture et l'écriture de fichier.
Il en existe dans la norme ANSI et d'autres dans la norme POSIX.

- [ ] Accès direct
- [ ] Gestion des buffers

#### Exemple : le programme `cat`

```c
void copy(FILE *fp) {
	int c; /* et pas char! */
	while ((c = getc(fp)) != EOF)
	  putc(c, stdout);
}

int main(int argc, char *argv[]) {
	FILE *fp;
	if (argc == 1) copy(stdin);
	else {
		while (--argc) {
			 if ((fp = fopen(*++argv, "r")) == NULL) {
				fprintf(stderr, "cannot open %s\n", *argv);
				exit(1); 
			}
			else {
				copy(fp);
				fclose(fp);
			}
		}
	}
	return 0; 
}
```
