# NOTES DU COURS 
---

Source : 
- 
Tags : 
Date : 2022-10-25

---

Topologie
- en anneau : chaque élément transmet les paquets après un temps prédéfini
- en bus : interconnecter les ordinateurs avec un le hub central en utilisant des câbles
	- ancienne topologie internet
	- On ne peut envoyer que quand le bus est libre
- en étoile : dispositif central qui permet d'accéder à tous les autres trucs
	- ce dispositif = switch ou commutator, dans le cas d'un réseau
- en mesh : pas d'ordre pour les connexions
- full mesh : chaque client possède un lien vers tous les autres clients
- tree : arbre

![[Pasted image 20221025173233.png | center]]
SWITCH ---------- ROUTEUR

- switch : link et physical du model OSI
	- fonctionne que avec l'adresse MAC
- routeur : network, link et physical du model OSI
	- fonctionne avec l'adresse IP

---

SWITCHING = choisir le chemin pour envoyer des infos d'un truc à un autre

- Circuit switching :
	- un chemin spécifique dédié pour la communication (comme un câble pour les vieux téléphones)
	- the entire data travels over the dedicated path
	- when all the data has been transmitted, you can now use the path again

- Packet switching (plus spécifiquement datagramme switching):
	- le truc à envoyer est divisé en paquets, et chacun prend le chemin le plus optimale
- Packet switching (virtual circuit switching):

- Message switching : 
	- no dedicated path
	- message is forwarded from one switch to another
	- each switch stores the whole message and when it has any resources, it sends it to the next one

---







---
#### À savoir

- [ ] savoir compter le nombre de switch nécessaire, avec x ports, pour brancher n machines

