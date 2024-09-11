

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




    

_________________ AssetMapper : gestion CSS et JS simple et moderne   _________________
  

  Il est installer par default sur symfony sinon si ce n'est pas le cas voila la commande à taper
Pour installer le composant AssetMapper, exécutez :

        composer require symfony/asset-mapper symfony/asset symfony/twig-pack

        voila le résultat : 
        assets/app.js Votre fichier JavaScript principal ;
        assets/styles/app.css Votre fichier CSS principal ;
        config/packages/asset_mapper.yaml Où vous définissez vos « chemins » d’actifs ;
        importmap.php Votre fichier de configuration importmap.


importmap() permet de linker notre application à nos fichiers de css et js 'app' concerne le app.js.
c'est le point d'entrée de nos fichiers css et js
 {% block importmap %}{{ importmap('app') }}{% endblock %}





_________________ CREATION DE LA BASE DE DONNEES   _________________
  
création de l'entité user pour authentification

         symfony console make:user
resultat : 
 created: src/Entity/User.php
 created: src/Repository/UserRepository.php
 updated: src/Entity/User.php
 updated: config/packages/security.yaml


 on va ajouter des attributs à notre entité user
        symfony console make:entity




on fait la meme chose avec l'entity  : 
        Keyword
        Category
        Trick
        Comment
        rating

les relations :

        - les asctuces (tricks) ne peuvent pas avoir q'un seul user
        - peuvent avoir plusieurs mots-clés (Keyword) et les Keyword peuvent avoir plusierus asctuces
        - un Trick peut avoir plusieurs comments et un comment ne peut aprtenir qu'un seul post et seul user
        - un trick peut avoir plusieurs rating mais un rating ne peu appartenir  qu'un seul trick

une fois les entités finis : 

on crée les requetes : 
        symfony console make:migration

si touche se passe bien un fichier de migration sera crée dans le dossier migrations qui contient toutes les requetes liées aux entités

pour le faire correspondre à notre base de données on fait : 


symfony console doctrine:migrations:migrate


et la tous nos tables et leurs colonnes sont crées





_________________   AUTHENTIFICATION   _________________
faire L'authentification

        symfony console make:auth  

...suivre les instructions

voila ce qui a été crée : 

        created: src/Security/UserAuthentificatorAuthenticator.php
        updated: config/packages/security.yaml
        created: src/Controller/SecurityController.php
        created: templates/security/login.html.twig

...lire les instructions qui suivent





faire l'inscription : 
        symfony console make:registration

voila le résultat : 

 updated: src/Entity/User.php
 created: src/Form/RegistrationFormType.php
 created: src/Controller/RegistrationController.php
 created: templates/registration/register.html.twig


...lire les instructions qui suivent







_________________   ENVOIE DE MAIL  _________________

on va simuler un envoie de mail avec mailhog avec docker

on éxcécute docker compose pour créer un nouveau container enfin que l'image soit pris en compte

aller dans .env.local decommenter cette ligne et configurer comme ceci : 
        MAILER_DSN=smpt://mailhog:1025


puis aller dans configs/packages/messenger.yaml et decommenter cette ligne : 
        #Symfony\Component\Mailer\Messenger\SendEmailMessage: async

cela permet d'ignorer le systeme par defaults de symfony qui permet d'envoyer des mails


et si vous voulez mettre un systéme fil d'attente il faut décommenter cette ligne


Je vais dans env.local pour créer un clé token qui me permet d'activer mon compte si j'envoie le mail
JWT_SECRET = 'messiTheGreatest'


pour acceder à JWT_SECRET dans notre controller ex il faut aller le déclarer dans config/services.yaml dans les parameters : 
          app.jwtsecret: '%env(JWT_SECRET)'


donc pour envoyer l'email il faut aller dans la fonction register (fonction pour s'enregistrer) dans le controller RegistrationController
        - generer le tocken
        - envoyer le mail 








aller dans src créer un dossier services pour y mettre mes services 
après s'y met s'y crée le service SendEmailService.php

pour le template de l'email d' inscription on crée un dossier emails dans templates et on y crée le fichier register.html.twig



on va créer un service JWTService.php

on va créer 
        - la fonction qui génére le token
        - fonction qui vérifie si le token est valide
        - fonction qui récupére le Payload
        - fonction qui récupére le header
        - fonction qui vérifie si le token a expiré
        - fonction qui vérifie la signature du Token

après inscription :
        - on génére le token
        - et envoie le mail





activer le compte si on on clique sur un lien dans le mail d'inscription







_________________   MOT DE PASSE OUBLIE  _________________

créer une fonction forgottenPassword dans le controller SecurityController

Créer un formulaire lié au mot de passe oublié

        symfony console make:form 

il n 'est pas relié à un entité











<!-- <div class="checkbox mb-3"><label><input type="checkbox" name="_remember_me">Se souvenir de moi</label></div>-- >