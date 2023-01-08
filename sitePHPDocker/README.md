# Mode d'emploi du déploiement d'un site PHP avec une DB MySQL sous Docker 

## Description

Le site sera déployé via 2 conteneurs : 
  - 1 conteneur pour la DB
  - 1 conteneur pour le code 

## Arborescence

sitePHPDocker
    - imgsitephp : image pour la création du conteneur code  
    - imgsitedb  : image pour la création du conteneur DB

## Commandes pour l'exécution

Dans le répertoire sitePHPDocker : 
# création image site php code
docker build -t imgsitephp imgsitephp/.
# création image site php db
docker build -t imgsitedb imgsitedb/.
# voir les images
docker images
# création du conteneur avec la DB
docker run -d --name contsitedb imgsitedb 
# création du conteneur sitephp
docker run -d -p 8081:80 --name contsitephp imgsitephp
# voir les conteneurs
docker ps -a
# A ce stade 
-> lynx http://localhost:8081 affiche le site php mais erreur dans le menu "Livres" car connexion à la DB
# Erreur :  Name or service not know -> erreur réseau
# Il faut connecter les conteneurs -> les placer dans un même réseau
docker network ls
# création de notre réseau
docker network create sitephpnet 
# connecter le premier conteneur
docker network connect sitephpnet contsitephp
# connecter le deuxième conteneur
docker network connect sitephpnet contsitedb

# Remarques 
Le fichier Db.class.php contient la connexion vers la DB et doit être éventuellement adapté.
Il doit contenir le nom du conteneur -> docker utilisera le nom du conteneur au niveau réseau
Le mot de passe pour la DB dans ce fichier doit être le même que celui précisé dans le Dockerfile du conteneur DB