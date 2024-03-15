# Python-CI-CD

## Description du projet et étapes suivies

L'application est un Fast API avec une route Hello World à la racine.

Elle contient un test dans le fichier ```test_main.py```, et un ```Dockerfile``` pour dockeriser l'application.

### Préparations du déploiement

On a choisi de déployer l'application sur un EC2, on a donc préparé une instance ou on a installé Docker dessus.

### CI/CD

Pour cette partie, on a utilisé les github actions. On a donc créé 2 workflows. 
Le 1er execute les tests quand on fait une pull request sur la main.
Le 2ème, pour le déploiement quand on push sur la main, on relance les tests pour vérifier et on déploie sur l'EC2.

On a ajouté le ```HOST```, la ```SSH_KEY``` et le ```USERNAME``` dans les variables d'environnement Git pour pouvoir accéder à l'instance.

Pour l'action de déploiement, on se connecte juste à l'EC2 et on pull les dernières modifications. 
On build l'image docker et on la run.

Nous avons réussi à déployer notre container Docker de notre App python.
![Running Docker](/running_docker.png)

## Amélioration

Le mieux aurait été de stocker l'image Docker sur le ghcr (le container Registry de Github), et d'uniquement pull l'image sur l'EC2 et la run directement.
