# Hébergeur

*  🔖 **Service**
*  🔖 **Transférer**
*  🔖 **Framework**
*  🔖 **Alternative**

___

## 📑 Service

Pour rendre votre projet visible de tous il doit être hébergé sur un serveur distant.

![image](https://raw.githubusercontent.com/seeren-training/Wordpress/master/wiki/resources/server.jpg)

Il existe de nombreuses offres d'hébergement mutualisé, dédié, gratuit, payant.

![image](https://raw.githubusercontent.com/seeren-training/Wordpress/master/wiki/resources/ovh.png)

Il faut posséder un nom de domaine, une adresse qui pointe vers un espace disque puis un hébergement qui correspond à cet espace disque.

___

👨🏻‍💻 Manipulation

Comparez les offres puis souscrivez à une offre gratuite pour l'exemple
___

## 📑 Transférer

Pour transférer votre projet, les procédures diffèrent. Il faut migrer votre code source puis les bases de données rattachées.

### 🏷️ **Informations sensibles**

Dans le cadre d'un projet natif vous ne disposez pas d'environnement de dev et de prod et donc pas de fichier de configuration spécifique à chaque environnement.

Vous devez absolument stocker vos informations de connexion ou vos clefs d'api dans des fichiers de configurations pour le mode production, des fichiers qu'il ne faut pas versionner et qu'il faut différencier en utilisant une extension '.prod'. Exemple: database.prod.json.

___

👨🏻‍💻 Manipulation

Externalisez vos identifiants de base de données et vos clefs d'API dans des fichiers pour le dev et la prod.

___

### 🏷️ **Exporter**

Vous devrez migrer votre code source ainsi que vos bases de données. Je vous invite à exporter vos bases de données sans résultat de données dans un fichier sql que vous déposer dans le dossier 'migrations' de votre projet par exemple.

___

👨🏻‍💻 Manipulation

Exporter votre base de données dans un fichier de migration au format sql

___

### 🏷️ **Importer**

Dans votre espace d'administration de base de données en production vous devez importer votre fichier exporté précédemment.

___

👨🏻‍💻 Manipulation

Importez votre base de données

___

### 🏷️ **Transférer**

Vous devz maintenant transférer votre code source en utilisant un client de transfert de fichier.

🔗 [Filezilla](https://filezilla-project.org/)

Vous devez être en possession des informations ftp, host, port, user, password pour la connexion.

___

👨🏻‍💻 Manipulation

Transférez votre projet et fixer les problèmes de chemins.

___

## 📑 Framework

Dans le cadre d'un projet fait sous Framework, vous devez vous reporter à la procédure de migration de l'outil.

🔗 [Symfony](https://symfony.com/doc/current/deployment.html)

___

👨🏻‍💻 Manipulation

Déployer une application Symfony

___

## 📑 Alternative

Pour les projet déposé sur des hub git, de type outil de productivité en langage client, il est possible d'utiliser l'hébergement de votre hub.

Pour github cela s'appel les githubpages.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/githubpages.jpg)

___

👨🏻‍💻 Manipulation

Je vous invite à apprendre dans un premier temps les bases de git avec comme objectif de relier votre code source à un dépôt puis de l'héberger. Partant?

___
