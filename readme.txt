

        créer le projet symfony 
symfony new my_project_directory --version="7.1.*" --webapp


en cas de problémes de, de conflits de ports dans le container on relance le moteur docker
        service docker restart
 

pour stopper et supprimer tous les containers :
      docker rm -f $(docker ps -aq)


supprimer tous images en meme temp
        docker rmi $(docker images -q)

Commande pour accéder au shell du container php-fpm
docker compose exec php-fpm  /bin/bash


lien pour la gestion les images et containers: https://www.hostinger.fr/tutoriels/supprimer-toutes-les-images-docker#:~:text=Pour%20supprimer%20plusieurs%20images%20Docker,images%20que%20vous%20souhaitez%20supprimer.&text=La%20commande%20docker%20images%20%2Dq,supprime%20toutes%20vos%20images%20Docker.



un conseil : éxécuter vos commandes dans le container


1 - Pour créer un controller 

symfony console  make:controller

Cette commande  src/Controller/MainController.php et templates/main/index.html.twig



le css se troue dans assets/styles/app.css









pour acceder au settings et faire des configs du coté graphique...
 ctrl + shift + p

....il est possible de faire les configs du coté fichier en cliquant sur l'icone fichier


pour trouver le namespace d'un objet, fuction ou class
ctrl + alt + i 





//EXTENSIONS VISUAL STUDIO A INSTALLER SUR SYMFONY :  

1. PHP Intelephense
2. PHPDoc Comment
3. PHP Namespace Resolver
4. Symfony code snippets
5. Symfony for VSCode
6. Symfony Snippets
7. Twig
8. Twig Language 2
9. HTML CSS Support
10. Twig
11. JavaScript (ES6) code snippets
12. Community Material Theme (Extra)
13. French Language Pack for Visual Studio Code
14. Live Sass Compiler

NB: voir ce lien : https://blog.codewithdary.com/must-have-vscode-extensions-for-symfony




  