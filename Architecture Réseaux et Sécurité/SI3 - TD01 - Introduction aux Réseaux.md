# TD01 - Introduction aux Réseaux
---

Source : 
- [[Computer Science Knowledge/SI3/Architecture Réseaux et Sécurité/attachments/td01.pdf|TD01]] 
Tags : #SI3 
Date : 2022-10-07

---
#### 1 - Introduction

Dans ce TP, vous trouverez quelques exercices qui vous permettront de réaffirmer vos connaissances acquises à propos de l’architecture physique des réseaux, ainsi que les phénomènes observés lors de l’échange de paquets (messages).

---
#### 2 - Architecture Internet

> [!question] Question 1
> Les switches sont utilisés pour fournir un accès aux clients des réseaux locaux filaires. Supposez que vous avez des commutateurs (switches) avec 5 ports chacun. Nous réserverons cependant un port pour l’accès Internet (ce qui laisse donc 4 ports pour les clients). Quelle topologie réseau construire afin de donner accès internet à 20 clients ? combien de switches vous faut-il au total ? Dessinez votre topologie.

Pour calculer la profondeur d'un arbre : 
	- Root = niveau 0
	- Chaque étage supplémentaire += 1

cf papier

> [!question] Question 2
> Quelle profondeur doit avoir une topologie arbre pour pouvoir donner service à n clients si on possède de switches à p ports uniquement ?

$$
\displaylines{
p : \text{nombre de ports} \newline
n : \text{nombre de clients} \newline
log_{p-1}(n) \leq \text{profondeur} \Leftrightarrow n \leq (p-1)^{profondeur}
}
$$

> [!question] Question 3
> Les routeurs sont de dispositifs qui permettent d’accéder à d’autres réseaux. De ce fait, chaque réseau doit posséder au moins 1 routeurs afin d’accéder à l’Internet. Ajoutez un routeur à votre topologie réseau de la question 1.

> [!question] Question 4
> Supposez que l’architecture réseau faite dans le point 3 doit être répliqué 4 fois, car par exemple, nous avons 4 départements indépendants dans des bâtiments séparés. Si nous savons que chaque routeur doit avoir au moins 2 liaisons vers d’autres routeurs afin d’éviter les isolements en cas de panne, proposez une topologie valable pour l’interconnexions de vos 4 sites.

cf papier

> [!question] Question 5
> En partant du schéma entier d’interconnexion des 4 sites, identifiez les topologies réseaux qui ont été utilisés.

> [!question] Question 6
> Les réseaux n’ont pas une capacité infinie. Décrivez comment un réseau à commutation de circuit et un réseau à commutation de paquets peuvent expérimenter des phénomènes de congestion.

> [!question] Question 7
> Combien de serveurs au total on pourrait héberger dans un réseau k-6 fat tree ? Dessinez le réseau.

k-ary fat tree :
- k PoDs (Point of Delivery)
- (k/2)^2 servers per pod
- k/2 edge and aggregation switches per pod
- Each edge switch connects to k/2 servers and k/2 aggregation switches
- Each aggregation switch connects to k/2 edge switch and k/2 core switches
- (k/2)^2 core switches, each connected to k pods

$$
\displaylines
{
	k=6 \rightarrow \text{number of pods} \newline
	\left(\frac{2}{6}\right)^{2} = 9 \newline
	9*6 = 54 \rightarrow \text{number of servers}
}
$$

cf paper for the schema

---
#### Capture de trafic réseau

[Using tcpdump on the command line](https://docs.netgate.com/pfsense/en/latest/diagnostics/packetcapture/tcpdump.html)


---
#### Notes
