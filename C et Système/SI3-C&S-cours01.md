# SI3 - C et Système - Cours 1
---

Source : 
- [[Summary - SI3 - C et Système]]
- [[SI3-C&S-01-introduction-langage-C.pdf]]
Tags : #C
Date : 2022-10-03

---
#### Paradigme : Définitions

[[Programming Paradigm]]

-> ayant cours à une certaine époque
-> modèle théorique sur une manière de penser qui va orienter la recherche
-> manière de voir les choses, modèle cohérent du monde
-> révolutions informatiques <=> changement de [[Paradigm|paradigme]]

- Manière de programmer un ordinateur basé sur un ensemble de principes et théories
- Un paradigme = un ensemble de concepts

![[principal-programming-paradigm.png | center | 600]]

---
#### Les concepts majeurs

- L'enregistrement
- La fermeture
	- La continuation
	- L'exception
- L'indépendance
	- La concurrence
	- L'interaction : affectation unique, choix non-déterministe ou état partagé
- L'état
	- La variable affectable (1ère forme de l'état)
	- Le canal de communication (2ème forme de l'état)
- L'abstraction de données
	- [[Encapsulation|L'encapsulation]]
	- [[Polymorphism|Le polymorphisme]]
	- [[Inheritance|L'héritage]]
- La programmation orientée but
	- [ ] [[Programmation Paresseuse|La programmation paresseuse]]
	- [ ] [[Programmation par Contraintes|La programmation par contraintes]]

---
#### Familles de programmation

- Programmation Impérative
	- [ ] [[Programmation Structurée]] -> programmation spaghetti ( `goto` )
	- [ ] [[Programmation Procédurale]] : [[C]], Ada, Pascal
	- [[Object Oriented Programming|Programmation Orientée Objet]] : C++, Java, C#

- Programmation Déclarative
	- [ ] [[Programmation Fonctionnelle]]
	- [ ] [[Programmation Logique]]
	- [ ] [[Programmation par Contraintes]]

![[programming-family01.png | center | 250]]

---
#### Programmation Impérative vs Déclarative

![[Imperative Programming#Definition | no-h nlk clean]]

![[Declarative Programming#Definition | no-h nlk clean]]

![[imperative-vs-declarative-programming.png | center | 600]]

---
#### Pourquoi le language C

- [[C]] inventé pour construire le système d'exploitation Unix
- C = un des langages plus efficaces

---

![[C#Un peu d'histoire]]

---

![[C#Buts du langage]]

---

![[C#Évaluation du langage]]

---
#### Hello, world!

![[C - Hello World]]

`printf` est dans le module `stdio.h` donc il faut l'importer.

[[C - stdio]]

La fonction `main` doit obligatoirement retourner un `int`
- 0 si ça s'est bien passé
- un chiffre négatif si ça s'est mal passé

---
#### [[gcc]]

---
#### Autres

Si il n'y pas d'accolades dans une boucle, la première et seulement la première instruction après est exécutée dans la boucle.
