# B3 Devops - Projet 1

## Info
Team 2

---

mail: thomas.flitterman@ynov.com  
github_username: tofl

---

mail: yvesmichel.dieme@ynov.com   
github_username: yves1997-dieme

---

## Dockerhub

link: https://hub.docker.com/repository/docker/tomflitterman/projet-devops


## Changelog

Template:

```
## [Unreleased]

## [1.0.0] - 2019-06-20
### Added
- Feature 1
- ...

### Changed
- Feature 1

### Removed
- Feature 1

### Fixed
- Problem 1
```

## Versionning

(from https://semver.org/)

Given a version number MAJOR.MINOR.PATCH, increment the:

- MAJOR version when you make incompatible API changes,
- MINOR version when you add functionality in a backwards compatible manner, and
- PATCH version when you make backwards compatible bug fixes.


## Fichiers

### Dockerfile

Le Dockerfile installer les paquets npm (`npm install`) et exécute le fichier app.js avec le script `serve` de npm.

### app.js

Il s'agit du l'API, lancée en développement avec nodemon.

### test.js

Il s'agit du fichier de tests lancé avec `npm run test`. Le test fonctionnera toujours.

### .circleci/config.yml

Ce fichier définit deux jobs:

- test : lance les tests avec `npm run test` après avoir installé les dépendences.
- dockerize : créé une nouvelle image, et l'envoit sur Docker Hub.

Dans le cas d'un git push, le job `test` sera exécuté.  
Dans le cas d'un nouveau tag, le test sera lancé puis le projet sera dockerisé. La nouvelle image sera hébergée dans Docker Hub. Pour se connecter au compte, le fichier `config.yml` utilise les identifiants renseignés dans les variables d'environment de CircleCI. Aussi, grâce à la variable `CIRCLE_TAG`, nous récupérons le tag de git et l'utilisons pour tagger la nouvelle image.