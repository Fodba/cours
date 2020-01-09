<!-- HB, 23/10/2019 -->

# GIT : les branches 

Les branches permettent de copier le dépôt d'origine, donc d'obtenir d'autres versions du projet; on pourra alors travailler dans ces versions sans détériorer la principale/initiale.

## Lister les branches existantes

	git branch

Il n'y a pour le moment que la branche `master`, créée par défaut  lors de l'initialisation.

## Créer une branche 

	git branch nombranche

Exemples : `git branch dev`, `git branch v1`, `git branch oreo`, `git branch 2019_01_16`...

> Le nombre de branches est illimité.

## Changer de branche

Pour choisir la branche dans laquelle on souhaite travailler : 

	git checkout nombranche

## Je ne sais plus où j'en suis

Si vous ne savez plus dans quelle branche vous êtes, faites un `git branch` : la branche en couleur (et précédée d'un *) est celle dans laquelle vous travaillez.
 
## Fusionner des branches

Il arrive un moment où il faut publier votre travail effectué dans une branche avec la branche principale :

* On se place dans la branche qui va recevoir les nouvelles modif, ici la branche _master_ : 

	 `git checkout master`  

* On va chercher les modifications dans la branche où elles ont été effectuées (ici _nombranche_) :

	 `git merge nombranche`

Etape 3 (facultatif) : supprimer la branche à partir de laquelle on a importé les modifications : 

	 `git branch -d nombranche`

> Réfléchir s'il faut oui ou non la supprimer. Il est prudent de vérifier d'abord que la fusion s'est bien passée.  

 










 
 



