

        créer le projet symfony 
symfony new my_project_directory --version="7.1.*" --webapp


pour stopper le container :
        docker system prune -a

Commande pour accéder au shell du container php-fpm
docker compose exec php-fpm  /bin/bash




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



