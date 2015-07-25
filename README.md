# usil-packaging
Ce depot contient des packaging RPM pour RedHat, CentOS pour des outils liés à Usine Logicielle

## Sujet
Industrialiser l'installation d'une Usine Logicielle.

## Existants
Il y a déjà des projets permettant de générer des RPM pour Jenkins et Sonar.
Mais je trouve que les RPM ne sont pas complets et ne répondent pas au problèmatique Entreprise.

## Objectif
* A partir des binaires applicatifs, de générer des packages installables sur les OS.

## Cibles
### Outils
* SonarQube
* Jenkins
* Nexus

### Packaging
* RPM
* Docker

### OS
* Redhat, Centos

## Propositions avec RPM
Je propose ici une solution à base de Maven/Nexus pour construire les RPM :
* Utilisation du plugin Maven Assembly
* Utilisation du plugin Maven Build Helper

### avec une Usine Logicielle à base de Jenkins, Nexus
Pour construire les RPM de manière industrielle, il faudra :
* un dépot Nexus pour stocker les applications SonarQube, Jenkins, Nexus ;
* un dépôt Nexus pour stocker les RPM généré et ce dépôt sera un dépôt Yum ;
* un build par application exécutée dans un Job Jenkins.

### sans une Usine Logicielle
Pour générer une première fois les RPM sans Usine Logicielle, il faudra mettre :
* les applications SonarQube, Jenkins, Nexus dans le dépot local Maven ;
* générer les RPM depuis un poste de travail ;
* installer les RPM à la main sur les serveurs cibles.

### RPM
Le RPM s'occupera :
* de construire les FS
* de construire le compte technique
* de configurer SELinux
* de configurer Firewall
* de configurer init.d ou system.d
* de configurer les log rotatives
* de mettre en place les fichiers system.d
Les RPM seront configurables :
* une partie lors de la construction contenue dans le dépôt de source
* une partie lors de l'installation contenue dans le fichier stocké dans system.d
* une partie lors du démarrage du service

