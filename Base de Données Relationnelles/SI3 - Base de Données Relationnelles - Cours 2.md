# SI3 - Base de Données Relationnelles - Cours 2
---

Source : 
- [[Summary - SI3 - Base de Données Relationnelles]]
- [[SI3-BDR-02-algebre-relationnelle.pdf]]
Tags : #SI3 #database #relational-database 
Date : 2022-10-10

---
#### Algèbre relationnelle *in a nutshell*

- Opérations ensemblistes : 
	- Union, intersection, différence
	- Produit cartésien
- Opérations relationnelles
	- Projection
	- Sélection
	- Jointure naturelle
	- Division
	- Renommage

---
#### Union, Intersection, Différence

Pour faire une opération entre deux instances, il faut que ces instances aient le même schéma de relation.
Le résultat de cette opération aura aussi le même schéma de relation.

$$ r \cup s = \{ t \text{ | } t \in r \text{ ou } t \in s\}$$
$$ r \cap s = \{ t \text{ | } t \in r \text{ et } t \in s\}$$
$$ r - s = \{ t \text{ | } t \in r \text{ et } t \notin s\}$$


---
#### Produit cartésien

Le produit cartésien n'est possible que si les deux instances de schémas de relation n'ont aucun attribut commun.

$$  r \times s = \{\text{ ( }t_{1},t_{2}\text{ ) } \text{ | } t_{1} \in r \text{ et } t_{2} \in s\} $$

![[BDR-produit-cartesien.png | center | 600]]

---
#### Projection

![[BDR-projection.png | center | 600]]

Il a distributivité de la projection par rapport à l'union.

---
#### Sélection

![[BDR-selection.png | center | 600]]

- La sélection est commutative.
- Il y a distributivité de la sélection sur les opérations ensemblistes. (i.e. $\cap \text{ et } \cup \text{ et } -$)
- Il y a commutativité de la sélection avec la projection

---
#### Sélection étendue

Permet d'avoir des conditions différentes de juste l'égalité.
On peut donc faire des $A \leq 13 \text{ et } A \neq 8$, etc...

---
#### Jointure naturelle

- Permet de joindre des relations entre elles et construire une table de tuples à partir de deux tables.

---
#### Jointure naturelle de tuples

- La jointure se fait sur tous les attributs communs
	- Généralement il n'y qu'un seul attribut commun
	- S'il n'y a pas d'attributs communs -> la jointure de ces éléments a pour résultat la concaténation des éléments <=> produit cartésien
