# Référencement

*  🔖 **Validation**
*  🔖 **Les balises**
*  🔖 **Les micro data**
*  🔖 **Les URL**
*  🔖 **La performance**
*  🔖 **Le maillage**
*  🔖 **Robots**
*  🔖 **Sitemap**
*  🔖 **Le Responsive**
*  🔖 **Mots-clés**

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/seo.jpg)

> Les différentes section doivent s'appliquer sur un projet de votre production que je vous invite à déterminer

___

## 📑 Validation

Certains développeurs Web ont le sentiment commun que si une page Web semble correcte dans les navigateurs, peu importe si elle ne se valide pas. Ils décrivent la validation comme un objectif idéal, mais pas comme un problème noir et blanc.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/validation.jpg)

### 🏷️ **Pourquoi**

Il y a deux raisons très puissantes pour valider votre code HTML lors de sa création:

* Vous n'êtes pas toujours parfait, et votre code non plus - nous commettons tous des erreurs et vos pages Web seront de meilleure qualité (c'est-à-dire qu'elles fonctionneront de manière plus cohérente) si vous éliminez toutes les erreurs.

* Les navigateurs changent. À l'avenir, il est probable que les navigateurs seront moins indulgents lors de l'analyse du code invalide. Lorsqu'un navigateur rencontre du code HTML non valide, il doit faire une estimation éclairée de ce que vous vouliez faire, et différents navigateurs peuvent trouver des réponses différentes.

### 🏷️ **Validateur**

Pour valider son code il y a de nombreux outils, à installer ou en ligne. ESlint ou le linter d'un IDE peut faire le job, mais leur configuration peut se personnaliser et s'éloigner du standards.

Le W3C possède un validateur en ligne.

[Validateur](https://validator.w3.org/)

___

👨🏻‍💻 Manipulation

Validez et corrigez un document venant de votre production.

___

## 📑 Les balises 

Chaque balise doit s'utiliser dans le contexte qui lui correspond en fonction de sa documentation.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/balise.png)

Par exemple le document dot posséder un `h1` et un paragraphe doit lui succéder. La balise `main` doit être unique et les balises `header` et `footer` peuvent hiérarchiser chaque bloc. La balise `nav` regroupe les navigations etc.

Il faudra apporter un soin particulier aux balises `title` et `meta` description.

🔗 [Balises](https://github.com/seeren-training/HTML/wiki/02#%EF%B8%8F-reference)

___

👨🏻‍💻 Manipulation

Vérifiez vos titres et descriptions

___

## 📑 Les micro data

Les micro data permettent au robots d'indexation de qualifier votre contenu sur un schéma précisé.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/micro-data.jpg)

### 🏷️ **Item Type**

La première étape est de relier à conteneur d'information à un schéma disponible sur https://schema.org/. Il faut procéder par une recherche sur pour trouver un type qui correspond au contenu. L'attribut itemscope et itemtype qualifient le type de schéma pour le scope à l'intérieur du conteneur.

[Schema.org/](https://schema.org/)

```html
<div itemscope itemtype="http://schema.org/Movie"></div>
```

### 🏷️ **Item Prop**

Vous pouvez alors utiliser `itemprop` pour choisir une propriété du schéma à appliquer sur une balise.

```html
<div itemscope itemtype="http://schema.org/Movie">
    <h1 itemprop="name">Sharknado 6</h1>
</div>
```

### 🏷️ **Item scope**

Dans un scope vous pouvez déclarer d'autres scopes

```html
<div itemscope itemtype="http://schema.org/Movie">
    <h1 itemprop="name">Sharknado 6</h1>
  <p itemprop="aggregateRating" 
     itemscope 
     itemtype="https://schema.org/AggregateRating">
    RATING: <span itemprop="ratingValue">0.6</span>
  </p>
</div>
```

___

👨🏻‍💻 Manipulation

Utilisez les texts enrichis ou micro data sur votre document

___

## 📑 Les URL

Les url devraient pointer sur des identifiants indirectes et devraient masquer l'extension des fichiers en utilisant la réécriture d'URL.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/url.jpg)

 Pour ce faire vous avoir la possibilité de mettre en place des directives à votre serveur apache.

### 🏷️ **PHP**

Côté serveur vous remarquez différents comportements du serveur en fonction de son mode d'exécution.

#### **Built in server**

Avec le serveur embarqué vous remarquez que les url arbitraires sont disponibles, sur la super globale server ce chemin d'url est disponible à l'index '`PATH_INFO`'.

```bash
php -S localhost:8000 -t my-directory
```

#### **Apache**

En démarrant le service apache cette fonctionnalité n'est pas présente, il faut spécifier l'activation du module via un fichier de configuration apache.

```bash
# Deny access to the .htaccess file and will trigger a 403 status code
<Files .htaccess>
    order allow,deny
    deny from all
</Files>
#Turn RewriteEngine to On
RewriteEngine On
#Deliver static file
RewriteCond %{REQUEST_FILENAME} -f
RewriteRule ^ - [L]
#Trigger index.php and add query string append flag
RewriteRule ^(.*)$ index.php [QSA,L]
```

La super globale server ce chemin d'url est disponible à l'index '`REDIRECT_URL`'.

___

👨🏻‍💻 Manipulation

Utilisez la réécriture d'url pour pouvoir router vos pages avec des URL user friendly.

___

### 🏷️ **JavaScript**

En JavaScript c'est une autre paire de manche. Si vous avez développé une application de plusieurs pages, il faudra en premier temps qu'elle soit desservie par un serveur acceptant le mécanisme de redirection d'URL cité.

Il faudra modifier l'URL du navigateur et mettant à jour l'état de l'historique.

```js
const state = { }
const title = 'Titre de la page'
const url = '/ma-page'

history.pushState(state, title, url)
```

Au démarrage de l'application il faudra relever l'URL en cours pour faire une opération de routing.

```js
console.log(location.href.pathname); //'/ma-page'
```

Je vous conseille pour disposer d'un router sur ce langage de passer par un Framework ou une librairie spécialisée.

___

👨🏻‍💻 Manipulation

Essayer **à l'avenir** de router un JavaScript natif pour disposer de plusieurs URL

___

## 📑 La performance


Votre page ne doit pas peser plus d'1 mo, toutes ressources confondues. Pour ce faire il faut optimiser la tailles des images, scripts, links. Vous devez limiter le nombre de liens et éviter des liens vers des serveurs saturés.

Programmatiquement, si vous faites des requêtes vers une api en utilisant un langage server c'est le temps de réponse de votre page qui posera problème. Une politique de mise en cache doit être envisagée.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/cache.jpg)

En cas de galerie, des scripts de lazy loader d'images doivent être utilisés.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/lazy-load.jpg)

___

👨🏻‍💻 Manipulation

Utiliser un cache sur vos requêtes http, ou utiliser un lazy loader d'image pour optimiser le temps de chargement de vos pages.

___

## 📑 Le maillage

Il représente l'ensemble des liens permettant de naviguer dans un site.

### 🏷️ **PageRank**

Plus une page est pointée par un lien, plus elle est importante et monte dans le rang des pages. Pour donner du poind au pages, il faut essayer de créer des liens vers des thématiques communes et d'éviter des liens vers d'autres thématiques: c'est la technique du silo. Les liens vers les différentes thématiques du site doivent être regroupés dans un élément de navigation.

### 🏷️ **No follow**

Certaines pages ne doivent pas avoir de pond, comme les mentions légales ou la connexion, création de compte. Pour ces liens il est conseillé d'utiliser l'attribut `rel` avec la valeur `nofollow` pour que le robot ne suive pas ce lien et ne donne pas de poid à la page.

```html
<a href="/login" rel="nofollow">Login</a>
```

___

👨🏻‍💻 Manipulation

Optimiser votre maillage

___

## 📑 Robots

Un fichier `robots.txt` indique aux robots d'exploration des moteurs de recherche les pages ou les fichiers qu'ils peuvent ou ne peuvent pas demander à votre site. Son objectif principal est d'éviter de surcharger votre site de demandes. Il ne sert pas à empêcher qu'une page Web figure dans les résultats de recherche Google.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/robots.jpg)

Le fichier doit se trouver à la racine du répertoire public. Vous pouvez spécifier le nom d'un robot d'indexation puis une autorisation ou une interdiction d'indexation de contenu. Il est possible d'indiquer l'adresse de la carte du site.

```bash
User-agent: *
Disallow: /répertoire1/
Disallow: /répertoire2/
Allow: /répertoire2/sous-répertoire1/

Sitemap: http://www.example.com/sitemap.xml
```

[Règles d'indexation](https://support.google.com/webmasters/answer/6062596?hl=fr)

### 🏷️ **No index**

Cela sert à gérer le tarfic mais ne bloque de l'apparition dans les résultats de recherche. Pour ce faire il faut utiliser la directive noindex.

```html
<meta name="robots" content="noindex" />
```

___

👨🏻‍💻 Manipulation

Créez votre fichier `robots.txt` et limiter le trafic vers des ressources non utiles.

___

## 📑 Sitemap

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/sitemap.jpg)

Il s'agit d'un plan de site (« sitemap ») compréhensible par les robots d'indexation, rédigé sous forme d'un fichier XML ou texte qui répertorie les URL d'un site permettant ainsi d'inclure des informations complémentaires sur chaque adresse, comme sa date de dernière modification, la fréquence de mise à jour et son importance par rapport aux autres adresses du site. 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
	<url>
		<loc>http://www.seeren.fr/</loc>
		<lastmod>2020-10-18T17:15:46+01:00</lastmod>
		<priority>1.0</priority>
	</url>
	<url>
		<loc>http://www.seeren.fr/formations/</loc>
		<lastmod>2020-10-18T17:15:47+01:00</lastmod>
		<priority>0.8</priority>
	</url>
	<url>
		<loc>http://www.seeren.fr/audit/</loc>
		<lastmod>2020-10-18T17:15:47+01:00</lastmod>
		<priority>0.8</priority>
	</url>
	<url>
		<loc>http://www.seeren.fr/ebooks/</loc>
		<lastmod>2020-10-18T17:15:47+01:00</lastmod>
		<priority>0.8</priority>
	</url>
</urlset>
```

Il est possible de créer un sitemap à la main mais une fois le site en ligne il est possible d'utiliser un générateur de sitemap pour ensuite modifier le fichier généré afin de hiérarchiser les page.

🔗 [Générateur](https://www.mysitemapgenerator.com)

___

👨🏻‍💻 Manipulation

Une fois le site en ligne, générer un sitemap

___

## 📑 Responsive

Ne pas avoir plusieurs version d'un site pour moniteurs et smartphone est une bonne option évitant les redirection et favorisant l'indexation d'URL.

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/responsive.jpg)

Pour rendre responsive votre site vous connaissez la procédure: l'utilisation d'un framework CSS.

___

👨🏻‍💻 Manipulation

Vérifiez votre utilisation des grilles sur votre framework CSS

___

## 📑 Mots-clés

Le choix des mots clés est déterminant pour la qualité d'un résultat de recherche. Afin de choisir les mots clefs adaptés en rapport avec une audience, une recherche et une sélection doit se faire sur google trends

🔗 [Google Trends](https://trends.google.fr/trends/?geo=FR)

![image](https://raw.githubusercontent.com/seeren-training/WebMastering/master/wiki/resources/trend.png)

___

👨🏻‍💻 Manipulation

Sélectionner les mots clefs en rapport avec votre activité.

___

### 🏷️ **Rédaction**

L'utilisation des mots clés doit maintenant se faire dans votre contenu, c'est la rédaction pour le web en rapport avec la qualité marqueting. L'utilisation doit se faire dans:

* Le titre
* La meta descritpion
* Les sous-titres
* Le contenu en utilisant l'interrogatif
* Les images
* Les URL
* Les texts de liens

___

👨🏻‍💻 Manipulation

Utilisez vos mots clés.