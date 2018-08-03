# Integrate Bootstrat Template to Rails App


Ex template bootstratpbay -Velonic : https://bootstrapbay.com/theme/velonic-admin-dashboard-frontend-B4864F4
> permet de récupérer un dossier avec html, assets, fichiers css, fonts, js, ...

## 1. Intégration code html
Ouvre index.html et copie le contenu dans home.html.erb (en enlevant body et head)

## 2. Import de bootstrap
Récupérer les fichiers CSS et les mettre dans 'stylesheets'

## 3. Importer les images
* ajouter toutes les images dans le dossier 'images'
* remplacer les balises img (html) en balises image_tag (erb)
! il peut y avoir des images dans la partie css également : pour celles-ci, il suffit de modifier l'url (ne laisser que le nom du fichier)

## 4. Intégrer les polices
Via ```@import``` (façon CDN)
> aller sur google font > sélectionner une police > cliquer sur "customize" > copier/coller "@import + url..."
![Image of google fonts](https://octodex.github.com/images/yaktocat.png)


## 5. Intégrer le javascript
* récupérer les fichiers js du template et les intégrer dans /assets/javascript
! : copier les fichiers ne suffit pas, il faut ensuite décider de l'ordre dans lequel ils vont être importés
> dans le fichier 'application.js', on require tous les fichiers .js présents dans le dossier

https://html5up.net/
https://bootstrapbay.com/

---

David

Je rjoute la gem boostrap
dans application.css > @import "bootstrap";
@import "custom";
puis je renomme en .scss
je créé un fichier custom.scss
dans application.js >> rajouter require jquery
create controller
> https://startbootstrap.com/template-categories/all/ > choisir template 'bare'
