
Instructions pour tester la solution

1) activer module reverse proxy : a2enmod proxy proxy_http && systemctl restart apache2
2) copier siteJetty.conf dans /etc/apache2/sites-available/
3) activer le siteJetty a2ensite siteJetty.conf
4) systemctl reload apache2
5) modifier le fichier /etc/hosts : 127.0.0.1 siteJetty
6) Démarrer le serveur Web Jetty : java -jar NoDBRunTest.jar
7) lynx http://siteJetty
