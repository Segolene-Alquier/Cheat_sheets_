## ✅ | Les étapes pour créer une page Rails qui fonctionne

⚠️ ALERTE BONS PLANS ⚠️ : Pour éviter les galères en fin de projet, il est recommandé de TOUJOURS commencer son app par la configuration heroku, puis de push une première fois, et de voir si ça marche en ligne.

**1. Création de l'app Rails**

Entrer dans le terminal ```$ rails new [blog]```

Le dossier créé contient les fichiers suivants :

Dossier | Fonction / contenu
------------ | -------------
app/ | Contient les controllers, models, views, helpers, mailers, channels, jobs et assets
bin/ | Contient les scripts qui permettent à l'application de démarrer (javascript, CSS...)
config/ | Configure les routes et BDD de l'app
db/ | Schéma de la BDD actuelle ainsi que les migrations de BDD
lib/ | Extensions pour l'app
log/ | Fichiers de connexion de l'app
public/ | Fichiers publics comme certains fichiers statiques
test/ | Tests unitaires et autres dispositifs de tests
tmp/ | Fichiers temporaires (comme les caches)
vendor/ | Code de tiers

-> On se sert principalement des dossiers "app", "config" et "db".

**2. Se déplacer dans le nouveau fichier créé**

**3. Remplacer le 'gemfile' à cause de non concordance entre SQLite3 et PG**

Remplacer le 'gemfile' de l'app rails crééé par :

```
source 'https://rubygems.org'
ruby '2.3.4'

gem 'rails',        '5.1.4'
gem 'puma',         '3.9.1'
gem 'sass-rails',   '5.0.6'
gem 'uglifier',     '3.2.0'
gem 'coffee-rails', '4.2.2'
gem 'jquery-rails', '4.3.1'
gem 'turbolinks',   '5.0.1'
gem 'jbuilder',     '2.7.0'

group :development, :test do
  gem 'sqlite3', '1.3.13'
  gem 'byebug',  '9.0.6', platform: :mri
end

group :development do
  gem 'web-console',           '3.5.1'
  gem 'listen',                '3.1.5'
  gem 'spring',                '2.0.2'
  gem 'spring-watcher-listen', '2.0.1'
end

group :production do
  gem 'pg', '0.20.0'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```

**4. Installer le bundle**

Pour installer et inclure les gems nécessaires au fonctionnement du projet

Taper dans le terminal ```$ bundle install --without production```

**5. Créer l'application heroku**

Taper dans le terminal ```$ heroku create```

Puis ```$ git add .``` > ```$ git commit -m 'xxxxx'```

Pour push : ```$ git push heroku master```

> si le push a fonctionné, alors on continue avec la configuration de l'app rails, sinon... courage ! 🙌


**6. Configurer l'application**

_**Configurer les routes**_

Ouvrir le fichier config/routes.rb
Il faut ensuite définir la méthode home au root du programme, puis mets les méthodes xx et yy à /xx et /yy de la manière suivante :
```
Rails.application.routes.draw do
  get 'blog/home'
  root 'blog#home'

  get 'blog/xx', to: 'blog#xx'

  get 'blog/yy', to: 'blog#yy'
end
```
-> a été créé lorsque l'on a tapé dans le terminal ``` bin/rails generate controller Welcome index```

_**Lancer le serveur pour s'assurer que les routes sont bien configurées**_

```$ rails server```

_**Créer un controller**_

La fonction du *controller* est de recevoir des requêtes spécifiques pour une application.
C'est le routeur qui décide quel controller reçoit quelle requête.
Il y a souvent plusieurs routes pour un même controller.

```$ rails generate controller Welcome index```

-> 'Welcome' est le nom du controller et index l'action qu'on lui assigne
-> Cela crée automatiquement une view 'Index'

> Tous les controllers créés héritent du controller 'ApplicationController', qui hérite lui-même de 'ActionController::Base'. C'est ce qui permet aux objets des modèles de communiquer avec la BDD.
> Puisque tous les controllers héritent de 'ApplicationController', les méthodes appliquées dans celui-ci s'appliquent automatiquement à chaque action de l'application.

_**Modifier la view**_

C'est la partie qui s'affichera pour l'utilisateur, il faut donc la soigner !
Elle est au format html.erb, c'est de l'html un peu spécial car les balise ressemblent à ça ```<%= … =%>``` ou ça ```<% … %>``` plutôt qu'à ça ```< > … </>```
Tout ce qu'il y a dans une balise ERB : <%= C'est du code Ruby ici =%>
> **ERB = "Embedded RuBy" = Du Ruby dans de l'html**

_**Créer un modèle**_

⚠️ Le model ne prend jamais de s à la fin, c'est le controller qui met des s ⚠️

```$ bin/rails generate model Article title:string text:text```
-> on crée un modèle 'Article' avec un attribut 'titre' de type string et un attribut 'text' de type text

Il faut ensuite faire la migration : ```$ rails db:migrate```

⚠️ A chaque fois que l'on modifie la base de données, il faut effectuer une migration

_**Remplir la base de données**_

```$rails c``` ou ```$ rails console```
> permet de lancer un IRB dans la console

Pour ajouter des données dans la BDD, taper dans la console :
```movie1 = Movie.create(id: "", title: "", year: "")```
-> à répéter pour chaque item

> Pourquoi une majuscule à l'un et pas à l'autre ?

Model | Class	Table
-------|------------
Article |	articles
LineItem |	line_items
Deer	| deers
Mouse	| mice
Person	| people

**7. Déployer une app sur Heroku**

```
$ git status
$ git add -A
$ git commit -m "Final"
$ git push heroku
```
Puis migrer la BDD de production : ```$ heroku run rails db:migrate```
