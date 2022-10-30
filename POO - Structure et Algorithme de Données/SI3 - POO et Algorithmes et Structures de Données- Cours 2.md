# SI3 - POO et Algorithmes et Structures de Données- Cours 2
---

Source : 
- [[Summary - SI3 - POO et Algorithmes et Structures de Données]]
Tags : 
Date : 2022-10-11

---
#### Introduction

Benefits of inheritance (cf [[Inheritance]])

Inheritance in the heart of Java : `Object` and `Class`

The `Object` class, super class of all classes
The `Class` class, of which all classes are instances

All class inherit from the class `Object`
`Object` définit un certain nombres de méthodes par défaut.

![[object-class-default-method.png | center | 600]]

---
#### `toString`

Defined in `Object` : 
```java
public String toString() {
	return getClass().getName() + '@' + Integer.toHexString(hashCode());
}
```

On peut `@Override` cette méthode pour avoir notre propre `toString`.

---
#### `equals` and `hashCode`

L'égalité entre deux objets est vérifié par le hash code de chaque objet.
On peut redéfinir le equals pour que cela correponde à nos besoins.

Exemple : 
```java
public boolean equals(Object o) {
	if (this == o) return true; // default equals, objects are the same
	if (o == null || getClass() != o.getClass()) return false;
	Color color = (Color) o;
	return r==color.r && g==color.g && b==color.b;
}

public ... hashCode(Object o) {
	// TO FILL FROM THE PPTX
}
```

Quand on redéfinit le `equals` il faut OBLIGATOIREMENT redéfinir le `hashCode` pour être sûr que l'on compare les bonnes choses.
-> sinon les collections peuvent ne pas fonctionner correctement

Il est obligatoire que `equals` respecte quand on le redéfinit : 
- reflexive : `x.equals(x) -> true`
- symmetric : `x.equals(y) -> y.equals(x)`
- transitive : `x.equals(y) & TO FILL`
- consistent

---
#### `getClass`

Autre méthode : `ClassName.class`

---
#### Inheritance and Visibility

[[Java - private Keyword | private]] element : not visible ouside the class

[[Java - default Keyword | default]] (package private) : visible in the package

[[Java - protected Keyword | protected]] : visible in all subclasses (and the package)

A subclass cannot weaken the accessibility of its superclass. <=> On ne peut pas réduire la visibilité

- a subclass can replace a protected method in its superclass and change its visibility to public
- if a method is defined as public in the superclass .... TO FILL

---
#### Héritage des constructeurs

Tous les constructeurs de toutes les classes, expectés ceux de la classe `Object` ... TO FILL

On est obligé d'appeler le constructeur parent quand celui a des paramètres, sinon non. Donc le `super()` n'est pas obligatoire.