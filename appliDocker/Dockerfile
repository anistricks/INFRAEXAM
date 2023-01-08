FROM debian
MAINTAINER Assaidi Anis
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install apache2 -y
COPY ./syllabusHTML /var/www/syllabusHTML
COPY syllabusHTML.conf /etc/apache2/sites-available/000-default.conf
EXPOSE 80
CMD ["apache2ctl", "-D", "FOREGROUND"]




