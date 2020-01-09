<!-- HB, 23/10/2019 -->

# Git : un outil de gestion de versions

## Objectifs

* Mettre en oeuvre un outil de gestion de versions et de partage de code au sein d'une équipe de développement
* Utiliser Git en lignes de commandes et la plateforme Github

## Qu'est-ce Git et Github ?

GIT est un outil de suivi de version 

2<sup>ème</sup> fonction essentielle de Git : partager son code dans le cadre du travail en équipe ou le diffuser publiquement. On va alors créer un dépôt distant (le vôtre est un dépôt local) : c'est-à-dire envoyer notre code sur un serveur public (cloud). Il existe différents services/plateformes de ce type : Github, Gitlab...

## Présentation

Assister à la présentation par votre formateur de ce [document](git.pdf).

## Mise en oeuvre

Maintenant que vous connaissez un outil de gestion de versions, mettez-le en oeuvre dans **la suite de la formation** (projets _Jarditou_ ou _Fil rouge_ notamment) selon les étapes suivantes.

## Etape 1 : Installation de Git

Téléchargez et installez l'application officielle [Git for Windows](https://gitforwindows.org) (également connue sous le nom _msysGit_) :

* Choisir _Notepad++_ comme éditeur 
* Cochez _Use Git from the Windows Command Prompt_  
* Cochez _Use the OpenSSL library_  
* Laissez les autres propositions cochées par défaut

* Vérifier l'installation : ouvrir le terminal (ou encore console) : touche Windows + R, saisir `cmd`, entrer la commande qui doit afficher le numéro de version : 

		git --version

### Configurer vos identifiants 

	git config --global user.name "Dave Loper"
	git config --global user.email "dave.loper@afpa.fr"

### Création d'un dépôt 

> Par sécurité, faites d'abord une sauvegarde de vos fichiers

Un dépôt est l'endroit où les versions du code source d'un projet seront stockées; concrètement il s'agit d'un répertoire physique. Un dépôt peut se trouver sur votre PC (_dépôt local_), sur un serveur ou des services cloud telles que Github, on parle alors de _dépôt distant_.  

On va initialiser un dépôt pour le projet _jarditou_ (par exemple) situé dans `C:/Wamp`. Dans l'invite de commande Windows, tapez :

    cd c:/wamp/www/jarditou
    git init

* 1ère ligne : on se place dans le répertoire où se situe le projet 
* 2ème ligne : commande d'initialisation d'un dépôt Git pour le projet 

Vérifiez que la seconde commande a bien créé un sous-répertoire `.git` dans `c:/wamp/www/jarditou` (ou le projet de votre choix).

### Déposer les fichiers pour la première fois (tous les fichiers)

	git add .

### Valider le dépôt et mettre une indication
	
    git commit -m "Dépôt initial"

### Afficher les ajouts/modifications effectuées 

	git status

ou encore :

    git log

### Ignorer des fichiers

Il est possible d'ignorer des fichiers, c'est-à-dire que ceux-ci ne seront pas pris en compte dans les dépôts.

[Lire cette ressource](https://perhonen.fr/blog/2015/03/exclure-fichiers-depot-git-gitignore-1476).

## Les branches

[Lire cette ressource](git_branches.html).

## Github 

Les développeurs du monde entier utilisent la plateforme [GitHub](https://github.com) (27 millions d'utilisateurs !), un service de partage de code. Les projets peuvent être rendus publics (ils sont alors téléchargeables librement) et en mode collaboratif, dans ce cas tout le monde peut contribuer au développement d'un projet. 

Créer un compte sur le site. Il vous permettra de publier dans un ou plusieurs dépôts le résultat de votre production.

**Objectifs :** 

* Créer un compte sur Github. 
* Créer un dépôt (= _repository_) pour publier votre code
* Importer des projets hébergés sur Github 

### Générer une paire de clés SSH

Secure SHell (SSH) est un outil de communication permettant de se connecter de façon sécurisé sur un serveur distant. Le protocole SSH propose un système d4authentification sans mot de passe en utilisant la [cryptographie asymétrique](https://fr.wikipedia.org/wiki/Cryptographie_asym%C3%A9trique).

Une paire de clé doit être créée, une publique, une privée. La clé publique est installée sur les serveurs où l'on veut se connecter, la clé privée est conservé en lieu sûr dans le poste de travail. Lors de la connexion un échange de clés permet de valider l'authentification.

* Sur Windows, aller dans le répertoire contenant votre projet.
* Clic droit, choisir _Git bash here_, entrez la commande :

	ssh-keygen -t rsa -b 4096 -C "votreadresse@email.com"

* Le chemin d'enregistrement du fichier sous Windows vous est demandé, faites _Entrée_ pour laisser le chemin par défaut proposé (`C:\users\votreprofil\.ssh`). 
* Une _passphrase_ facultative est demandée, faites _Entrée_ (pas de passphrase, on pourra en définir une plus tard). Idem pour la confirmation.
* Une fois la commande exécutée, une paire de clés est installée dans le répertoire `c:\users\votreprofil\.ssh`.
	* Une **clé privée**, dans le fichier `id_rsa`.
	* Une **clé publique**, dans le fichier `id_rsa.pub`.

> [Documentation](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)

### Ajouter la clé publique sur Github

Pour pouvoir utiliser l'authentification SSH :

* Déclarer la clé publique dans votre profil GitHub :
	* Sur Github, allez dans **Your profile**
	* Cliquez sur **Edit profile**
	* Cliquez sur **SSH Keys**
	* Cliquez sur **New SSH Keys**
	* Coller votre clé publique (éditez le fichier `id_rsa.pub`, puis cliquez sur **Add SSH Key**

* Associer le dépôt local avec le dépôt distant Github :
	
	    git remote add origin https://github.com/votreidentifiant/votredepot.git

* Avant d'envoyer notre code local, on doit d'abord récupérer celui qui se trouve sur le serveur avec la commande `pull` ("tirer") (car d'autres personnes auraient pu y publier leur code : 

        git pull

* Envoyer ("pousser") le code local vers Github : 

	    git push origin master

### Ajouter un nouveau fichier

	git add nouveau.php 
    git commit -m "Ajout du fichier 'nouveau.php'" 
    git log 

### Prendre en compte des fichiers modifiés

	git add index.php 
    git commit -m "Modification du titre" 
    git log

## Importer des projets hébergés sur Github

Pour initialiser un projet hébergé sur Github, par exemple Code Igniter, cherchez la page [CodeIgniter](https://github.com/bcit-ci) sur Github, cliquez alors sur le bouton `Clone or download` pour obtenir l'url (`https://github.com/bcit-ci/CodeIgniter.git` dans notre cas puis utilisez la commande `git clone` :   

    cd c:/wamp/www
    git clone https://github.com/bcit-ci/CodeIgniter.git lambda

Dans cet exemple, `lambda` est le répertoire cible du projet; il sera créé par Git s'il n'existe pas dans _c:/wamp/www_.

## Git et Intégration continue

[Explications](integrationcontinue.html)

## Ressources

* [tutoriel vidéo](https://www.youtube.com/watch?v=4o9qzbssfII)
* [Site officiel](http://git-scm.com/book/fr)
* [Rappel des principales commandes GIT](rappel_commandes_git.html)
* [Pour aller plus loin ...](https://delicious-insights.com/fr/articles/bien-utiliser-git-merge-et-rebase)