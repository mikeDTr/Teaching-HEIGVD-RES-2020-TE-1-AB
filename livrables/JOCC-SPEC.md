# Protocole JOCC 0.9 

**Auteur: [Michael] [Triponez] (`michael.triponez@heig-vd.ch`)**
## Introduction

Le protocole Jokes give hOpe during the Covid Confinement period (JOCC) est conçu pour que des clients puissent obtenir ou soummettre "jokes" à des serveurs au traver d'un réseau TCP/IP. 
Tout serveurs conforme à la spécification , doit être capable de recevoir des jokes et les stocker, permettre de les catégoriser, de les evaluer et de les renvoyer en cas d'une demande faite par un client.
Les jokes devrons pouvoir être renvoyées sous forme de liste les classant par évaluation ou par date d'ajout la plus récente.
le classement des membres doit aussi pouvoir etre recupéré en fonction du nombre soumnis ou de l'évaluation.

Les serveurs pourrons au vouloir implémenter plus de types de retour pour les jokes ou les membres.


## Fonctionnement

Le protocole de transport utilisé est celui de TCP. Le port 8080 est définit défaut. Une fois la demande de connection au serveur acceptée, celui-ci envois un méssage de bienvenue incluant les actions possibles.
Le client pourra envoyer ses opération jusqu'a l'envois d'un QUIT qui fermera la connection.
Pour chaque opérations effectuée par le client le serveur renvera un message avec le nom du client suivi de la réponse qui lui est destinée. Si l'opération est correcte le résultat attendu sera delivré, sinon un méssage d'érreur sera retourné.

Le protocole JOCC est statefull afin de pouvoir garder en mémoire les informations des users qui ont envoyé les jokes et qui seronts évalués puis pouvoir les redistribuer en cas de demande.


## Syntaxe

Le protocole JOCC définit 6 méssages TELL, SEND, GETJ, GETR, RATE, QUIT. afin d'indiquer une fin de ligne le client doit utiliser la séquence CRLF.

voici un exemple de communication attendu après avoir accepeter la connection.

##Erreurs 

##exemple


S:Bienvenue sur JOCC, voici les differentes actions possibles
	Vos opérations devrons etres fermée par un 
	TELL 	| TELL "name" vous identifie sur le server en temps que "name"
	SEND 	| Envois des Jokes au serveur avec ou sans categorie 
				SEND "jokes" 				| envois sans catégorie
				SEND "jokes", "categorie"	| envois catégorisé
	
	GETJ	| Renvois des Jokes aléatoires ou sous forme de listes
				GETJ "joke" 				| retourne une Joke aléatoire
				GETJ "joke", "categorie"		| retourne une joke selon la catégorie
				
	GETR	| Renvois le classement des membres 
				GETR -J						| classement par evaluation de joke
				GETR -N						| classement par nombre de jokes envoyés
				
	RATE	| Evalue une Joke
				RATE "joke" | evalue la joke entrée en parametre

	QUIT 	| Termine la connection
C:TELL michael CRLF
S:Bienvenue michael CRLF
C: SEND ta mère pendant le COVID, dark humour CRLF
S: JOKE received from michael CRLF
...
