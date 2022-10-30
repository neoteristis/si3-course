# Harmonisation Réseaux et Sécurité - TD2
---

Lesson : 
- [[Summary - SI3 - Harmonisation Réseau et Sécurité]]
Tags : #network #security 
Date : 2022-09-20

---
#### Exercice 1 : Mot de passe et contrôle d'accès
---
##### Qu’est-ce qu’une attaque par force brute sur un mot de passe ? Dans quels cas a-t- elle plus de chance de réussir ? Comment peut-on la limiter ?

> In [cryptography](https://en.wikipedia.org/wiki/Cryptography "Cryptography"), a **brute-force attack** consists of an attacker submitting many [passwords](https://en.wikipedia.org/wiki/Password "Password") or [passphrases](https://en.wikipedia.org/wiki/Passphrase "Passphrase") with the hope of eventually guessing correctly. The attacker systematically checks all possible passwords and passphrases until the correct one is found.

On a plus de chances de réussir lorsque le mot de passe à deviner n'est pas très sécurisé. Un autre facteur est la puissance de calcul pour réaliser l'attaque.

On peut limiter ces attaques en :
- utilisant un mot de passe fort
- limitant le nombre d'essais possible pour essayer son mot de passe.

---
##### Qu’est-ce qu’une attaque par dictionnaire sur un mot de passe ?

> L'attaque par dictionnaire (ou en anglais « dictionary attack ») est une méthode utilisée pour pénétrer par effraction dans un ordinateur ou un serveur protégé par un mot de passe, en essayant systématiquement tous les mots d'un dictionnaire donné.

---
##### Quelles sont les bonnes pratiques pour choisir un mot de passe ?

- Never reveal your passwords to others
- Use different passwords for different accounts
- Use multi-factor authentication (MFA)
- Length trumps complexity : use long passwords
- Make passwords that are hard to guess but easy to remember
- Complexity still counts : to increase complexity, include upper and lower case letters, numbers, and special characters
- Use a password manager

Check [Have I Been Pwned](https://haveibeenpwned.com/) to see if you've been hacked

---
##### Quelles sont les bonnes pratiques pour conserver un mot de passe ?

- Online or locally ?
	- Both are dangerous because they both can be hacked
	- Your credentials are protected as much as the storage system you choose is protected
- Plain text or encrypted ?
	- Always use encryption
	- Most of them uses : AES-256
- Paid or free solutions ?
	- Paid solutions do not justifiy themselves
	- Some free solutions are as good as the paid ones
- Standalone software or browser extension ?
	- Browser
		- Default password manager in Chrome etc...
		- Third-party tools are being offered as browser extensions
		- Many malware pieces might be there
	- Using a separate software is recommended
- Autofill forms
	- All password managers offers an autofill features
	- Incredibly convenient
	- Incredibly risky from a security point of view
		- During a phishing attack, hackers may use this feature to collect data using invisible forms that will be auto filled with your credentials.

---
##### Installez le logiciel KeePassXC (https://keepassxc.org/) et testez-le. A quoi sert-il ?

> Securely store passwords using industry standard encryption, quickly auto-type them into desktop applications, and use our browser extension to log into websites.

---
##### Qu’est-ce qu’un captcha ?

> CAPTCHA : Completely Automated Public Turing test to tell Computers and Humains Apart

> Used to differentiate between real users and automated users (bots).
> They provide challenges that are difficult for computers to perform but relatively easy for humans.

CAPTCHAs are used for :
- Maintaining poll accuracy
- Limiting registration for services
- Preventing ticket inflation
- Preventing false comments

---
##### Qu’est-ce que l’authentification 2 facteurs ?

> aka 2FA
> Extra layer of security used to make sure that people trying to gain access to an online account are who they say they are.

First factor : 
- username
- password

Second factor :
- Something you know
	- PIN (personal identification number)
	- password
	- answers to "secret questions"
	- specific keystroke pattern
- Something you have
	- Credit card
	- Smartphone
	- Small hardware token
- Something you are
	- Biometric pattern or fingerprint
	- Iris scan
	- Voice print

---
##### Citez d’autres systèmes permettant de contrôler l’accès à un système informatique.

[Tech target : What is access control ?](https://www.techtarget.com/searchsecurity/definition/access-control#:~:text=Access%20control%20is%20a%20security,access%20control%3A%20physical%20and%20logical.)

---
#### Exercice 2 : Vecteurs d'attaque
---

Décrivez le fonctionnement des différents types de menaces ou de logiciels malveillants suivants :
- **Backdoor (porte dérobée)**
	- Fonctionnalité inconnue de l'utilisateur légitime qui donne un accès secret au logiciel
- **Bombe logique**
	- Dispositifs programmés dont le déclenchement s'effectue à un moment déterminé en exploitant la date du système, le lancement d'une commande, ou n'importe quel appel au système
- **Cheval de Troie (Trojan Horse)**
	- Type de logiciel malveillant, qui ne doit pas être confondu avec les virus ou autres parasites. Le cheval de Troie est un logiciel en apparence légitime, mais qui contient une fonctionnalité malveillante. Son but est de faire entrer cette fonctionnalité malveillante sur l'ordinateur et de l'installer à l'insu de l'utilisateur.
- **Virus**
	- Automate logiciel autoréplicatif
	- Conçu pour se propager sur d'autres ordinateurs en s'insérant dans des logiciels légitimes, appelés « hôtes » à la manière d'un virus biologique
- **Ver**
	- Logiciel malveillant qui se reproduit sur plusieurs ordinateurs en utilisant un réseau informatique comme Internet. Il a la capacité de se dupliquer une fois qu'il a été exécuté. Contrairement au virus, le ver se propage sans avoir besoin de se lier à d'autres programmes exécutables.
- **Adware**
	- Logiciel qui affiche de la publicité lors de son utilisation.
- **Espiogiciel**
	- Logiciel malveillant qui s'installe dans un ordinateur ou autre appareil mobile, dans le but de collecter et transférer des informations sur l'environnement dans lequel il s'est installé, très souvent sans que l'utilisateur en ait connaissance
	- Équivalent d'un mouchard
- **Keylogger**
	- It reads and logs keystrokes and can recognize patterns to make finding passwords easier.
- **Rançongiciel**
	- Logiciel malveillant qui prend en otage des données personnelles. Pour ce faire, un rançongiciel chiffre des données personnelles puis demande à leur propriétaire d'envoyer de l'argent en échange de la clé qui permettra de les déchiffrer.
- **Rootkit**
	- Ensemble de techniques mises en œuvre par un ou plusieurs logiciels, dont le but est d'obtenir et de pérenniser un accès (généralement non autorisé) à un ordinateur le plus furtivement possible
- **Botnet**
	- Réseau de bots informatiques, des programmes connectés à Internet qui communiquent avec d'autres programmes similaires pour l'exécution de certaines tâches.


Les logiciels antivirus permettent de tester la présence de certains de ces vecteurs d’attaque dans les logiciels.

---
#### Exercice 3 : HTTPS et certificats d'identité
---
- Que signifie le «s» de https?

> HTTPS : Hyper Text Transfer Protocol Secure

- Lancez le logiciel wireshark (https://www.wireshark.org/docs/), employé durant le
TD précédent, pour capturer les messages envoyés par votre navigateur. Que se
passe-t-il de différent entre les deux sites ?



- Comment pouvez-vous connaître avec certitude le propriétaire du site ? Indice : un
cadenas fermé doit apparaître à côté de l’URL du site (à défaut un cadenas ouvert ou un panneau d’avertissement). Que signifie-t-il ? Cliquez dessus pour plus d’informations.



- Confrontez vos informations aux informations fournies en tapant whois xxxx ou en utilisant un service whois en ligne (par exemple https://www.afnic.fr/noms-de-domaine/tout-savoir/whois-trouver-un-nom-de-domaine/ ou https://who.is).

---
#### Exercice 4 : Protection de la vie privée
---
##### Qu’est-ce qu’un cookie ?

> Cookies are text files with small pieces of data — like a username and password — that are used to identify your computer as you use a computer network. Specific cookies known as HTTP cookies are used to identify specific users and improve your web browsing experience.
> 
> Data stored in a cookie is created by the server upon your connection. This data is labeled with an ID unique to you and your computer.
> 
> When the cookie is exchanged between your computer and the network server, the server reads the ID and knows what information to specifically serve to you.

---
##### Quel est l’effet des cookies sur votre navigation sur différents sites web ?

- Session management
- Personalization : targeted ads
- Tracking : shopping sites can suggest other goods, keep items in the shopping cart

---
##### Pouvez-vous indiquer les cookies qui sont utilisés par les sites web indiqués ci-dessus ?

Pour http://www.nice.fr/fr/ : 
- 5 cookies
	- Cookies
		- PHPSESSID
		- \_pk\_id.19.1.1e2b
		- \_pk\_ses.19.1e2b
		- cc\_cookie\_accept
	- Stockage de session
		- http://www.nice.fr

Pour : https://univ-cotedazur.fr/ :
- 19 cookies

---
##### Essayez de supprimer certains cookies du navigateur, reconnectez-vous au site, et allez voir si les cookies ont été repositionnés.

Oui les cookies sont recréés.

---
##### Essayez ensuite de bloquer certains cookies positionnés par le site grâce au navigateur.

Une fois bloqués, ils ne sont plus recréés.

---
##### Cherchez maintenant dans votre navigateur l’option permettant de systématiquement bloquer les cookies et testez votre navigation avec différents paramètres de blocage.

Sur Sidekick (Chromium) :

`Paramètres` > `Confidentialité et Sécurité` > `Cookies et autres données des sites` > `Bloquer tous les cookies`

---
##### Connaissez-vous d’autres mécanismes de traçage contraires à la protection de la vie privée ?

- Account tracking
	- Data is stored in the account (Facebook, Google etc...) instead of cookies
		- Browsing activity can be tracked
- Tracking pixels
	- Transparent images that collect information on web traffic, user behaviour and conversions
	- Can't be disabled
	- Can track :
		- OS details
		- Mail information
		- Screen resolution
		- IP adress
- Browser fingerprinting
	- Creating a user's profile using the information gained from browser details and activities
	- Website can identify you accurately and track you easily using browser fingerprinting
- HTTP referrer
	- The referrer will pass the information about the previous page to the new page 
	- Helpful for statistical analysis and promotional purposes

---
##### Nous allons utiliser Thunderbird à l’exercice 7 : ce logiciel de messagerie peut être réglé afin de ne pas télécharger les images dans un mail. Quel est l’intérêt de cette fonction ?

- Ne pas installer de logiciel malveillant par inadvertance

---
##### Ce site comporte un cookie wall qui est actif sur les articles réservés aux abonnés. Qu’est-ce et comment fonctionne-t-il ?

Site : https://www.nicematin.com/

> Ce cookie wall permet de ne pas autoriser l'accès aux utilisateurs n'ayant pas login sur le site.
> Il vérifie qu'une session correcte a été ouverte. Cette information est présente dans les cookies du site.

---
#### Exercice 5 : Sécurité des réseaux d'entreprise - firewalls - VPN - wifi
---
##### Les réseaux d’entreprise sont sécurisés vis-à-vis d’attaques provenant d’Internet. Qu’est-ce que cela signifie ?

---
##### Un des mécanismes utilisés pour sécuriser un réseau d’entreprise est le filtrage réseau, effectué par un pare-feu (ou firewall). Nous allons visualiser l’effet d’un tel système avec le logiciel traceroute, qui permet d’afficher tous les nœuds traversés par un message que nous envoyons. Testez ceci avec la commande : traceroute -P ICMP www.google.fr. Testez maintenant la commande traceroute -P TCP -p 80 www.google.fr. Quelle différence voyez-vous ?

---
##### Un autre mécanisme est l’utilisation d’un réseau privé virtuel (VPN pour Virtual Private Network) qui permet notamment de chiffrer tout le trafic réseau entre un utilisateur et son réseau d’entreprise, à travers un réseau public. Pouvez-vous citer un autre cas d’utilisation des VPNs ?

---
##### Vous avez utilisé le logiciel SSH dans le TD précédent sur Core. A quoi sert ce logiciel ? Quelle est la différence par rapport au logiciel telnet ? Que remarquez-vous quand vous utilisez SSH ?

---
##### Les réseaux wifi sont très fréquents en entreprise et dans toutes les organisations (comme UCA) mais n’est pas sans danger. Quel est par exemple le risque des « rogue access points »?