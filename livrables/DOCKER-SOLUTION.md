# Rendu de l'exercice Docker 

**Auteur: [Michael] [Triponez] (`Michael.Triponez@heig-vd.ch`)**

## Compte rendu

Expliquez ici quelle stratégie vous avez utilisée pour vous connecter au service exécuté dans le container, en décrivant les étapes suivies:

La commande docker run à été utilisée afin de lancer les deux containers.
J'ai ensuite recuperer les adresses IP grace à docker inspect (  172.17.0.2  et  172.17.0.3)

normalement afin de communiquer avec les deux containers il faudrais utiliser netcat  dans un container ( en ajoutant l'instalation de netcat dans le docker file 
en effectuant 

RUN apt-get update && \
  apt-get -y install netcat && \
  apt-get clean 
  
  et en lançant un container dans la même plage d'adresse ip ou l'on ferais nc -l -p 2020  pour se connecter et dialoguer.
  
  
  étanttant donné que je me suis perdu en faisant n'importe quoi je n'est pas pu effectuer tout ce qu'il fallais faire je n'ais donc pas de captures
  
  
## Capture d'écran

Assurez-vous que vous avez placé la capture d'écran dans un fichier nommé `CAPTURE-RES.png`.

## Remarques

Si vous avez des choses à partager au sujet de l'exercice, utilisez cette dernière section.

