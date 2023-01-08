# INFRAEXAM


DOCKER :
11.2.3 Installation de Docker
Sous Debian :
apt-get remove docker docker-engine docker.io containerd runc

apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common &&
curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - &&
add-apt-repository "deb https://download.docker.com/linux/debian $(lsb_release -cs) stable" &&
apt-get update &&
apt-get install docker-ce docker-ce-cli containerd.io

Vérification de l’installation :
docker run hello-world

Lister les images :
docker images

Supprimer une image :
docker rmi <IMAGE>

Lister les conteneurs :
docker ps

Lister tous les conteneurs :
docker ps -a

Démarrer, arrêter, stopper un conteneur :
docker container start/stop/kill/rm <CONTAINER>

Se connecter à l’intérieur d’un conteneur :
docker exec -it <CONTAINER_ID> /bin/bash

Déboguer un conteneur :
docker logs <CONTAINER_ID>

Il est souvent utile pour y voir plus clair de stopper et supprimer tous les conteneurs :

docker stop $(docker ps -aq) && docker rm $(docker ps -aq)
