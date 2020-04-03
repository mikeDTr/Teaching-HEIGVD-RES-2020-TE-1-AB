# Protocole JOCC 0.9 

**Auteur: [Michael] [Triponez] (`michael.triponez@heig-vd.ch`)**
## Introduction

Le protocole Jokes give hOpe during the Covid Confinement period (JOCC) est conçu pour que des clients puissent obtenir ou soummettre "jokes" à des serveurs au traver d'un réseau TCP/IP. 
Tout serveurs conforme à la spécification , doit être capable de recevoir des jokes et les stocker, permettre de les catégoriser, de les evaluer et de les renvoyer en cas d'une demande faite par un client.
Les jokes devrons pouvoir être renvoyées sous forme de liste les classant par évaluation ou par date d'ajout la plus récente.
le classement des membres doit aussi pouvoir etre recupéré

MAY :


## Fonctionnement

Le protocole de transport utilisé est celui de TCP. Le port 8080 est définit défaut. Une fois la demande de connection au serveur acceptée, celui-ci envois un méssage de bienvenue incluant les actions possibles.

A vous de structurer ce document, en utilisant plusieurs sections. Une de ces sections doit être consacrée à la gestion de l'état, où vous nous expliquez si votre protocole est avec ou sans état, et pourquoi.

## Remarques

Si vous avez des choses à partager au sujet de l'exercice, utilisez cette dernière section.




C:connection 
S:Bienvenue sur JOCC, voici les differentes actions possibles
	TELL 	| TELL "name" vous identifie sur le server en temps que "name"
	SEND 	| Envois des Jokes au serveur avec ou sans categorie 
				SEND "jokes" 				| envois sans catégorie
				SEND "jokes" "categorie"	| envois catégorisé
	
	GETJ	| Renvois des Jokes aléatoires ou sous forme de listes
				GETJ "joke" 				| retourne une Joke aléatoire
				GETJ "joke" "categorie"		| retourne une joke selon la catégorie
				
	GETR	| Renvois le classement des membres 
				GETR -J						| classement par evaluation de joke
				GETR -N						| classement par nombre de jokes envoyés
				
	RATE	| Evalue une Joke
				RATE "joke" | evalue la joke entrée en parametre

C:
S:
C:
S:
C:
S:
C:
S:
C:
S:
C:
S:
C:
S:


client envois joke
categories
get jokes (categorisable)
evaluation de joke

liste des joke mieux evaluées
liste recent
classement membre

statefull