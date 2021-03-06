# Django le framework !

1. Introduction à Django
    1. Qu’est ce qu’un framework ?
    2. Types de frameworks
    3. Frameworks : Quels avantages et quels inconvénients ?
    4. Django, c'est quoi ?
    5. Design patterns et bonnes pratiques
    6. Ecosystème d'une application Django
2. Créer son premier projet sur Django
    1. Créer un projet et une première application
    2. Conception des premiers modèles
    3. Le traitement des données avec les vues et le routage d'URL
    4. Présentation du contenu avec les templates
    5. Administration du projet avec le scaffolding

# I - Introduction à Django

## 1 - Qu'est ce qu'un framework ?  
Un framework est l'ensemble de composants logiciels à la base d'un logiciel ou d'une application( bibliothèques,classes, helpers..etc).Il décrit les types de programmes à concevoir et leur mode d'interaction.  
Un framework permet de **simplifier le travail des développeurs informatiques** en offrant une architecture réutilisable et adaptée à leurs besoins. En outre, il peut être amélioré par l'expérience des développeurs.Les frameworks sont utilisés pour développer une application mobile, un site web, un jeu,..etc 

## 2 - Types de frameworks  
On peut classer les frameworks de la manière suivante:  
* **Frameworks d'infrastructure système** utilisés pour le développement des systèmes d'exploitation et des interfaces graphiques (Microsoft .Net, Apache Struts,...).
* **Frameworks d'intégration intergicielle** permettent l'interconnexion de systèmes divers.
* **Frameworks d'entreprises** sont spécifiques aux applications utilisées par les entreprises. 
* **Frameworks de gestion de contenu** sont les fondations d'un système de gestion de contenu — pour la création, la collecte, le classement, le stockage et la publication de « biens numérisés ».

Source : [Wikipedia](https://fr.wikipedia.org/wiki/Framework)

## 3 - Frameworks : Quels avantages et quels inconvénients ?  
En utilisant les frameworks, les développeurs codent de façon homogène. Ainsi, quand un développeur rejoint un projet basé sur un framework qu'il connaît, la compréhension de l'architecture lui sera plus simple et plus rapide que s'il avait dû s'approprier les outils au préalable. De plus, l'adoption d'une structure commune garantit un code organisé et facilement réutilisable. 

En revanche, les frameworks doivent être souples et modulables afin qu'ils soient adaptés à différents projets. Certains nécessitent cependant un temps d'apprentissage plus long que d'autres. 

Source: [Openclassrooms](https://openclassrooms.com/fr/courses/1871271-developpez-votre-site-web-avec-le-framework-django/1871361-creez-vos-applications-web-avec-django)  

## 4 - Django, c'est quoi ?  

Django est l'un des  frameworks applicatifs Python destinés au développement d’applications web. Créé en 2003 dans une agence de presse, Lawrence Journal-World, le framework est proposé au grand public deux ans plus tard. En 2008, la fondation Django Software a été créée. Aujourd'hui, Django est très populaire. Il est utilisé dans des applications web très célèbres comme *Instagram* ou *Pinterest*.  

Django permet le développement rapide de meilleures et plus performantes applications web. Il automatise des tâches répétitives  telles que l'écriture de requêtes destinées à une base de données. Il propose d'autres fonctionnalités comme une bibliothèque de traduction on un espace membres. 

## 5-**MVC/MVT**:   

Le Modèle-vue-contrôleur ou MVC est un type d'architecture logicielle destiné aux interfaces graphiques lancé en 1978 et très populaire pour les applications web. Le motif est composé de trois types de modules assurant différents rôles:  
   * Un modèle (Model) contient les données à afficher.
   * Une vue (View) contient la présentation de l'interface graphique.  
   * Un contrôleur (Controller) contient la logique concernant les actions effectuées par l'utilisateur.source: [Wikipédia](https://fr.wikipedia.org/wiki/Mod%C3%A8le-vue-contr%C3%B4leur)  
   ![](https://upload.wikimedia.org/wikipedia/commons/b/b4/MVC_Diagram_%28Model-View-Controller%29.svg)
   Django utilise l'architecture MVT (modèle-vue-template)qui s'inspire de MVC:   
   * Le **modèle** interagit avec une base de données.Un **ORM** (Object Relational Mapping) traduit les réponses à une requête [SQL](file:///C:/Users/admin/Documents/EGDownloads/Sql_1_Cours.pdf) ( langage de consultation de base de données) en **objets Python** exploitables par le programme.Tous les modèles sont réunis dans un fichier python **models.py**.  
   * La **vue** reçoit [une requête HTTP](https://openclassrooms.com/fr/courses/1118811-les-requetes-http) et renvoie une réponse HTTP convenable (par exemple si la requête est une interaction avec une base de données, la vue appelle un modèle pour récupérer les items demandés).Les vues se trouvent dans le fichier **views.py**
   * Le **template** est un fichier [HTML](https://openclassrooms.com/fr/courses/1603881-apprenez-a-creer-votre-site-web-avec-html5-et-css3/1604361-votre-premiere-page-web-en-html) récupéré par la vue et envoyé au visiteur.

## 6- Ecosystème d'une application Django

# II - Créer son premier projet sur Django
## 1 - Créer un projet et une première application
## 2 - Conception des premiers modèles
## 3 - Le traitement des données avec les vues et le routage d'URL
## 4 - Présentation du contenu avec les templates
## 5 - Administration du projet avec le scaffolding

Une des grandes forces de Django est de proposer la création très rapide d'une interface permettant d'administrer son site. Pour cela on va utiliser les fonctionnalités de _scaffolding_ (littéralement _échaffaudage_ ou _structure_) de Django.

La première étape est d'ajouter l'application d'administration dans la liste des applications utilisées dans notre projet. Pour ce faire il faut modifier la variable `INSTALLED_APPS` dans le ficher `settings.py` du projet :

```python
INSTALLED_APPS = (
    ...,
    'django.contrib.admin',
    ...,
)
```

Maintenant que l'application est active, il faut permettre son accès. Pour ce faire il faut rajouter une route pointant vers l'interface d'administration. Modifiez le fichier `urls.py` du projet (et non de l'application) pour rajouter ces lignes :

```python
from django.contrib import admin

admin.autodiscover()

urlpatterns = [
    ...,
    path('admin/', admin.site.urls),
    ...,
]
```

Ne vous attardez pas trop sur la ligne `admin.autodiscover()`, il nous permet simplement _"d'ajouter"_ automatiquement les modules d'administration de chaque application.

Afin de pouvoir utiliser notre interface, il nous faut créer un utilisateur qui a les droits d'accès à l'interface. Dans une console, se placer dans le dossier de notre projet, là où se trouve le fichier `manage.py` et taper : `python manage.py createsuperuser` (ou `python3 manage.py createsuperuser` si vous utilisez Python 3) puis suivez les étapes affichées. Une fois cette étape effectuée, vous pouvez lancer le serveur pour tester votre interface. Vous devriez arriver sur une interface comme celle-ci :

![Connexion à la plateforme d'administration](http://formation-django.fr/media/images/cms/authentification-interface-administration.png)
Source : [formation-django.fr](http://formation-django.fr/framework-django/scaffolding/mise-en-oeuvre.html)

Django gérant lui même toutes les questions de sécurité et d'authentification, il vous suffit de vous connecter avec les identifiants créés précédemment et vous avez accès à l'interface de gestion.

![Interface d'administration](http://formation-django.fr/media/images/cms/django-scaffolding-accueil.png)
Source : [formation-django.fr](http://formation-django.fr/framework-django/scaffolding/mise-en-oeuvre.html)

On a accès à la gestion des groupes d'utilisateurs, ainsi qu'au utilisateurs eux-mêmes, mais pas à la gestion de notre application en elle même, ce qui rends l'interface peu utile. Rajoutons donc nos modèles dans l'administration.

Pour ce faire, il faut modifier le fichier `admin.py` de notre application pour rajouter les lignes suivantes :

```python
from django.contrib import admin
from chistera.models import *

admin.site.register(Team)
admin.site.register(Project)
admin.site.register(ProductBacklog)
admin.site.register(Sprint)
admin.site.register(UserStory)
```

(L'importation du module à la deuxième lignes ainsi que les modèles utilisé sont à adapter selon votre application).

En raffraichissant simplement la page d'administration (avec le serveur lancé), nous voyons tous nos modèles dans l'interface : 

![Interface d'administration mise à jour avec les modèles](http://formation-django.fr/media/images/cms/django-application-admin.png)
Source : [formation-django.fr](http://formation-django.fr/framework-django/scaffolding/mise-en-oeuvre.html)