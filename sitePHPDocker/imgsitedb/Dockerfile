# Utilisation d'une image MySQL
FROM mysql
LABEL maintainer = "olivier.choquet@vinci.be"
# Définition des variables nécessaires pour la DB
ENV MYSQL_DATABASE=bdbn
ENV MYSQL_ROOT_PASSWORD=ipl
# Création d'une DB vide 
COPY bdbn.sql /docker-entrypoint-initdb.d
