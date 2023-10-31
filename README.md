# m2i-tp3

## Fichiers fournis
'pipeline.yml' contient une pipeline destiné à l'outil github action. L'outil étant integré dans github, la pipeline n'a pas besoin d'un fichier Docker-compose pour se lancer.

Notre pipeline va commencer par cloner le projet python depuis le github vanessakovalsky/python-api-handle-it. nous allons utiliser cette application pour nos test ainsi que son Dockerfile pour performer nos test jusqu'au push sur le Docker-hub.

Pour commencer, nous lançons un linter avec pytlint pour verifier les normes de codage (un score de minimum 5 est configuré ici).
Ensuite on analyse la complexité cyclomatique avec Radon.
Enfin les test unitaires avec html-testrunner.
Pour chaque test nous conservant le rapport dans un fichier stocké dans le folder report

Pour finir nous faisant notre build d'image et on push celle ci sur notre docker-hub.

> [!NOTE]
> Notre pipeline est composé de plusieurs job, de ce fait, nous allons utiliser les artefacts. Chaque resultat de job est uploadé dans une artefact qui sera utilisée sur le job suivant.

## pré-requis
> [!NOTE]
> - Il est recommandé de commencer par parametrer les crédentials de votre docker hub dans votre espace github dans : Settings -> Security: secrets ans variables -> actions
>   - DOCKER_USERNAME avec comme value votre identifiant et DOCKER_PASSWORD avec comme value votre TOKEN
> - Cloner le repo sur votre workspace.
> - Le trigger de la pipeline est configuré 'on Push'.

# Remarque:
Futur amélioration pour une V2, variabiliser le projet.