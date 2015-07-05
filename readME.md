
# Démarche pour ajouter la fonctionnalité des favoris

## Création du nouveau factory "manageFavorite"

Le factory permet de centraliser les fonctionnalités qui seront accessibles depuis plusieurs controllers.

Création du factory avec la commande suivante:

```sh 
yo angular:factory manageFactory -- save 
```

Ajout des fonctions javascript dans le manageFactory
Les fonctions du manageFactory communiquent avec le localStorage qui est un endroit de stockage interne au navigateur. Dans le lequel nous allons stocker nos favoris sous forme de liste d'id de films.

## Modification de la page principale

+ Sur la page principale nous avons ajouté à côté de chaque poster deux boutons, un permettant l'ajout du film aux favoris et l'autre permettant de retirer le film des favoris.
+ Il y a toujours qu'un des deux boutons affiché selon si l'id du film est présent ou non dans la liste des favoris.
+ Pour ce faire nous avons utilisé la directive angular ng-show, qui apelle une fonction isFavorite() qui retourne vrai ou faux si l'id du film est dans la liste des favoris ou pas. 
En cliquant sur les boutons la directive angular ng-Click apelle la fonction qui ajoute l'id du film dans la liste ou qui retire l'id du film de la liste.

## Création d'une nouvelle page "Favoris"

Ensuite nous avons ajouté une nouvelle page "Favori" composée d'une vue et d'un controller créé avec les commandes suivantes:

```sh 
yo angular:controller Favori -- save
yo angular:view Favori -- save
```

Pour chacun d'entre-eux, un fichier .html et un fichier.js à été créé.

Sur cette nouvelle page nous avons affiché tous les films présents dans la liste des favoris avec la possibilité de les retirer des favoris.
Nous avons créer une liste < ul > < /ul > dans la quelle il créé dynamiquement grâce à la directive angular ng-repeat un < li >< /li > pour chacun des films présents dans la liste des favoris retournée par le factory.

La difficulté est que dans la liste nous stockons uniquement des ids, nous devons donc aller chercher les posters et les titres des films dans la liste principale pour chaque id.

Design:
+ Nous avons utilisé la librairie slick qui permet de faire un bandeau déroulant avec les posters des films.
+ Nous avons utilisé les < div >< /div > pour aligner les élèments.
Nous avons utilisé une variable stocker dans le $rootScope qui est le scope la plus haut dans l'arborescence donc accessible depuis partout. Ce qui nous permet de définir une variable nbImage dans laquelle nous mettons le chemin de l'image du poster. Elle sera affichée en image de fond du body (sur le fichier index.html) visible dans les détails du film.

Déployement:
+ Afin de déployer notre site nous lançons la commande suivante:

```sh 
grunt build
```

Cette commande nous permet de créer un fichier dist contenant nos fichiers en version optimisée web.
Attention à ce que toutes les dépendances soient installées ! Il faut aussi corriger toutes les erreurs html que le navigateur nous avait autorisé. Afin de tester notre dist nous pouvons utiliser la commande suivante:

```sh 
grunt serve:dist
```
commande nous permet de créer un fichier dist contenant nos fichiers en version optimisée web

## Suivi du projet et gestion des versions
Nous avons utilisé [github] pour suivre et historiser les différentes versions de notre projet. Etant donné que les éléments placés sur github sont sur internet, nous avions chacun accès au répertoire de développement. Github nous a été utile pour identifier rapidement les modifications entre deux versions. Lors du développement il est nécessaire de faire souvent des "commit" et des "push" sur github afin que les évolutions entre deux versions se limitent a une fonctionnalité. Ainsi il est plus aisé de mettre en commun (fusionner) les développements et en cas d'erreur, de pouvoir revenir à une version précédente

Lien utile:

[directive angular]

[directive angular]:https://docs.angularjs.org/api/ng/directive
[github]:http://www.github.com