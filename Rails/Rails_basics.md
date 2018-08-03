# RUBY ON RAILS, YAAAY

Hello Moussaillon 👋,

Aujourd'hui, on s'attaque à **Ruby on Rails** !
On va essayer de résumer sur ce README les principes de base du framework, pour devenir des EXPERTS de la chose.
Alors on s'accroche, c'est parti sur l'autoroute de l'apprentissage ! 🤓

## 🔎 | First thing first - à quoi sert Ruby on Rails ?

C'est un framework de Ruby, qui permet de faire des sites avec du back-end sur internet.
Rails va faire tourner le code sur les serveurs pour renvoyer les bons contenus.
> c'est par exemple le cas sur Facebook, où le contenu diffère selon la personne connectée

## 💻 | La différence entre un site statique et un site dynamique

Un _**site Web statique**_ est un site où chacune des pages est créée en HTML. Un ordinateur qui se connecte au serveur demande une page. Celle-ci lui est directement servie car elle est stockée toute prête sur le serveur. Le serveur obéit et  renvoie le document demandé.

Par opposition, un _**site Web dynamique**_ est un site Web dont les pages sont générées dynamiquement à la demande (le fichier HTML n'existe pas encore), elles changent en fonction des interactions avec l'utilisateur.
Le contenu est obtenu (par exemple) en combinant l’utilisation d’un langage de scripts ou de programmation et une base de données.
Dans les sites dynamiques, le contenu (articles) est séparé de l’habillage (modèles ou squelette). Cette séparation contenu/présentation/logique est le credo des développements actuels.


## 👓 | Le MVC - Model View Controller

Rails suit le modèle architectural _**Model View Controller**_. Ce modèle crée une séparation entre la "logique domaine" et les entrées, et l'interface utilisateur. Dans le cas des applications web, la "logique domaine" consiste typiquement en modèles de données pour des choses telles que les utilisateurs, les articles et les produits, et l'interface graphique est juste une page web dans un navigateur web.

![MVC](http://i67.tinypic.com/5f3if5.png)

Le chemin entier d'une requête est le suivant :
1. Le navigateur envoie une requête à un serveur web
2. Le serveur web reçoit la requête et utilise un routeur pour définir le contrôleur correspondant
> le chemin par défaut est "/controller/action/id", comme défini dans ```config/routes.rb```
3. Le serveur web utilise ensuite le dispatcher qui va créer un nouveau contrôleur, appeler l'action et donner les paramètres
4. Le contrôleur analyse la requête, les données entrées et les cookies pour déterminer quelle réponse envoyer à l'utilisateur. En fonction, il va interroger le modèle pour obtenir les informations nécessaires.
5. Le modèle est une classe Ruby, qui va faire une requête SQL vers la base de données, stocke les données et les renvoie au contrôleur.
6. Le contrôleur va ensuite transmettre les données à la vue, qui représente le contenu visible par l'utilisateur.
7. La vue va recevoir un fichier 'html.erb' et construit à partir de cela la page en html/css, puis la renvoie au contrôleur
8. Le contrôleur renvoie la page au format html ou xml au serveur.
9. Le serveur transforme enfin la page en réponse HTTP et l'envoie à l'utilisateur

## 🚦 | Les routes

Les routes permettent d’interpréter les URL et d’orienter vers les bonnes actions des controlleurs. La configuration se trouve dans le fichier ```config/routes.rb```.

La configuration se fait via la ligne de commande :
> ```resources :xxx```

Il est possible d'en déclarer plusieurs :
> ```resources :xxx, :xxx, :xxx```

## 💽 | Les Bases de Données

Une base de données est un **ensemble qui permet le stockage des données**. Les données sont écrites de manière structurée, c’est à dire que chaque donnée est enregistrée dans une table. Lorsque les tables ont des relations entre elles, on parle de bases de données relationnelles. Ces tables peuvent être indexées pour permettre des accès plus rapides à certaines données et permettre aussi des tris.

YAML est le format de fichier de configuration par défaut utilisé dans tous les projets Rails. C'est un format assez simple à appréhender.


## 📮 | GET / POST

**GET** et **POST** sont des méthodes qui permettent respectivement de récupérer des informations depuis le serveur et d'envoyer des informations au serveur.
* **GET permet de recevoir des informations** depuis le serveur
* **POST sert à envoyer des informations**.

Le protocole utilisé pour la communication entre client et serveur est souvent HTTP (Hypertext Transfer Protocol).
Ces deux méthodes sont des méthodes REST. On les utilise dans les routes pour savoir comment traiter une donnée.

## 🚀 | Le concept de migration

Les migrations sont des classes de Ruby qui **permettent de créer et modifier simplement des tableaux de bases de données.**
Une migration te permet d'ajouter des données (Tables, modèles...) dans ta database et d'en prendre une "photo". Ainsi, il est possible de revenir à d'anciennes migrations et les modifier ou les supprimer.

Pour créer une nouvelle base de données, on emploie la méthode ```rails db:migrate```

## 👭 | Les relations entre les modèles des BDD

Il est fréquent dans un projet d'avoir différentes bases de données qui sont toutes connectées. Pour relier 2 modèles entre eux, il faut préciser dans la rail app qui hérite de qui.

On utilise pour cela les "liens de parenté" via 'has_many' ou 'belong_to'.
Ces deux expressions permettent de dire que le modèle - Article - has many - Comments - et que le modèle -Comment- belong to -Article-, c'est à dire que chaque article peut posséder plusieurs commentaires, mais que chaque commentaire appartient a un seul article.

👉 [Pour en savoir plus](http://guides.rubyonrails.org/association_basics.html)


## 💡 | Les fonctions du CRUD

CRUD renvoie à 4 types d'opérations sur les éléments d'une base de données :
* **Create** : permet à l'utilisateur de créer du contenu
* **Read** : permet à l'utilisateur de lire du contenu
* **Update** : permet à l'utilisateur de mettre à jour du contenu
* **Delete** : permet à l'utilisateur de supprimer du contenu
-------
Si tu arrives jusqu'au bout, c'est a priori bon signe ! J'espère que tu auras appris des choses et que c'est que le début d'une belle histoire entre Rails et toi... 🎈

Si t'as encore la foi, tu peux continuer pour lire les différentes étapes pour créer une page d'une app Rails 👇

-------

## ✅ | Les étapes pour créer une page qui fonctionne
**1. Entrer dans le terminal ```$ rails new blog```**

Le dossier contient les fichiers suivants :

Dossier | Fonction / contenu
------------ | -------------
app/ | Contient les controllers, models, views, helpers, mailers, channels, jobs et assets
bin/ | Contient les scripts qui permettent à l'application de démarrer
config/ | Configure les routes et BDD de l'app
db/ | Schéma de la BDD actuelle ainsi que les migrations de BDD
lib/ | Extensions pour l'app
log/ | Fichiers de connexion de l'app
public/ | Fichiers publics comme certains fichiers statiques
test/ | Tests unitaires et autres dispositifs de tests
tmp/ | Fichiers temporaires (comme les caches)
vendor/ | Code de tiers

-> On se sert principalement des dossiers "app", "config" et "db".

**2. Appeler le web server via ```$ rails server```**

> aller sur http://localhost:3000/ pour vérifier que la page d'accueil de Rails s'affiche

**3. Créer un "controller" et une "view"**

La fonction du *controller* est de recevoir des requêtes spécifiques pour une application.
C'est le routeur qui décide quel controller reçoit quelle requête.
Il y a souvent plusieurs routes pour un même controller.

La fonction de *view* est d'afficher ces informations à l'utilisateur.

**Créer un controller**

```$ bin/rails generate controller Welcome index```
-> 'Welcome' est le nom du controller et index l'action qu'on lui assigne

**4. Définir la page d'accueil**

Ouvrir la page config/routes.rb
Ajouter ```$ root 'welcome#index'```
> indique à Rails de renvoyer les requêtes de la root jusqu'à la page choisie
> ```get 'welcome/index'``` indique à Rails de renvoyer les requêtes de http://localhost:3000/welcome/index à l'action du welcome controller index.
-> a été créé lorsque l'on a tapé dans le terminal ``` bin/rails generate controller Welcome index```

**5. Créer une ressource**

C'est le terme utilisé pour définir une série d'objets similaires (articles, personnes, animaux).
On peut créer, lire, mettre à jour et supprimer ces objets : ce sont les CRUD opérations.

Pour déclarer une ressource standard REST, on utilise la méthode dans config/routes.rb :
```resources :articles```
En tapant ensuite ```$ bin/rails routes``` dans le terminal, on peut voir que Rails a pris en compte cette information.

**6. Créer un modèle**

```$ bin/rails generate model Article title:string text:text```
-> on crée un modèle 'Article' avec un attribut 'titre' de type string et un attribut 'text' de type text
