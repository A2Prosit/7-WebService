Team
Animateur : Gillyyyyyyyyy
Secrétaire : Fantou
Scribe : Flo
Gestionnaire : Yugo

## Mots Clés
- Client Web : 
- service web : systèmes logiciels, permettant l'intéropérabilité entre plusieurs systèmes logiciels (agents) sur un réseau informatique.
- Module Symfony : -
- API Rest
- Requête HTTP : -
- Reponse HTTP : -
- Laravel : framework
- PHP Web Service: 


## Contexte
Quoi ?
- Interroger les ressources du site

Comment ?
- En faisant des requêtes http
- En utilisant une API

Pourquoi ?
- Afin de requêter les articles en vente
- Interfacer facilement les données sur tous les supports actuels

Contraintes
- Utiliser une architecture donnée

## Problématique
Comment interroger des ressources à l’aide d’une API

## Généralisation
Communication

## Hypothèses
- Une API est une interface de programmation
- Une API -> Interface en Java
- ‘’ sert à utiliser l’application depuis un environnement extérieur



## Plan d'action

### **Etudes :**
### REST

L'architecture orientée services comme un style d'architecture qui a comme objectif une interdépendance faible (loose coupling) entre différents agents logiciels (modules, services). L'architecture orientée services promeut la réutilisation de composants logiciels au niveau macro. (Comparée à la programmation orientée objet qui promeut la réutilisation au niveau micro, classes, objets). 

Pour atteindre une réutilisation maximale, les services doivent être interopérables. Pour atteindre cette intéropérabilité, la définition des services doit avoir un certain nombre de caractéristiques :

 * Le fonctionnement d'un service est défini par un contrat
 *  Le langage informatique d'implémentation du service n'importe pas
 *   L'échange d'information entre services doit être standardisé
 *   La manière d'utiliser le service est définie par une interface
 *   Le service ne laisse pas transparaître la manière dont il est implémenté dans son interface
 *   Le service doit pouvoir se décrire aux autres agents
 *  Le service doit pouvoir être découvert par un mécanisme
 *  Transactions, sécurité, etc.


**utiliser un web service**:

UDDI (Universal Description, Discovery and Integration Service) est la norme qui définit le mécanisme pour découvrir dynamiquement des services. Un client pointe vers un registraire UDDI, qui lui donnera la définition du service recherché. Le registraire UDDI sert de pages jaunes et liste les services disponibles. Le registraire UDDI est lui-même un Web Service qu'un client peut questionner.

Pour être capable d'utiliser un Web Services et de programmer un client, il est nécessaire d'en connaître la définition. Le langage WSDL (Web Services Definition Language) décrit l'interface au service. En utilisant XML Schema, WSDL défini les paramètre d'entrée et de retour d'un appel au service Web.

Les appels sont effectués avec le protocol SOAP (Simple Object Access Protocol). SOAP offre le transport d'objets sérialisés et autres données en XML et l'appel de procédures distantes.

UDDI, WSDL et SOAP sont les trois normes principales des Web Services. Les normes UDDI sont proposées par OASIS. WSDL et SOAP font parties des normes W3C.

![](https://benoitpiette.com/labo/img/arch-typique.png)

WSDL décrit qu'est-ce que le service Web, où le trouver et comment l'appeler. WSDL utilise le concept de port pour définir la connexion au service Web.

Le WSDL est subdivé en plusieurs parties :

* la balise types : définie les type de données utilisés par le service en utilisant généralement xml schema
* les balises message : une abstraction plus haut niveau des paramètres (messages) pour les appels possibles au service Web
* le balise portType : contient des abstractions haut niveau des opérations possibles du service Web.
* la balise binding : défini les liens entres les opérations du service Web et le protocole de communication utilisé (généralement SOAP). C'est ici qu'on défini comment on utilise SOAP, les paramètres d'entrées et de sorties.
* les balises service et port : la balise service contient contient les points limites (port). Le port est défini par les binding du protocole réseau et une addresse réseau.


**REST**

REpresentational State Transfer inventé en 200 par le même mec qui a créé HTTP, HTML, URI et Apache (pas seul hein) pour son PhD

il s'agit d'un style d'architecture pour les systèmes hypermédia distribués (web services)

Le terme RESTful est un adjectif qui qualifie une application qui suit les principes REST.

La communication REST est basée sur HTTP

critères d'une API REST:

* client-serveur :  le serveur s’occupe de la gestion des règles métier et des données et le client se concentre sur l’interface utilisateur
* sans état : le serv ne garde pas les info du client entre chaque requête
* cacheable : le client peut grader les info en mémoire plutot que d'envoyer 5000 requêtes ( le serveur doit ajouter une étiquette de cache à toutes les réponses)
* interface uniforme : REST repose sur 4 contraintes d'interface:
	* l'id de manière unique des ressources
	* interaction avec le sressources via des représentations
	* messages auto-descriptifs
	*  HATEOAS (Hypermedia As The Engine Of Application State) : l'état de l'app, les différentes interactions possibles entre client et serveur doivent être décrites à traversles liens hypermédia dans les réponses serv
* système de couche : isolation des différents composants de l’application pour bien organiser leurs responsabilités, on peut prendre comme exemple une couche dédiée au stockage des données mais qui n’a pas conscience de leur origine
* code à la demande (optionnel): permet l’extension des fonctionnalités du client en fournissant du code téléchargeable et exécutable


Vrais API existants:

* instagram : pour recup des photos d'endroits en spécifiant des latitudes longitdes. ex: photo de San-Franciso
	
		GET /v1/locations/search?access_token=ACCESS_TOKEN&lat=40.7127&lng=74.0059
* gmail : fonctionnalitées mail si on veut faire une appli avec un service mail. ex : tous les messages envoyés entre le 1/1/14 et 30/1/14

		GET https://www.googleapis.com/gmail/v1/users/me/messages?q="in:sent after:2014/01/01 before:2014/01/30"

* github : stats sur les users des repo, info sur le repo. ex: info d'un utilisateur

		GET /users/:username

* Weather underground : info météo. ex: info de San Francisco

		GET http://api.wunderground.com/api/Your_Key/conditions/q/CA/San_Francisco.json
		GET http://api.wunderground.com/api/dd99676d41de9084/conditions/q/France/Labege.json


* Waston. Ex d'upload d'un fichier audio

		curl -u USERNAME:PASSWORD -X POST --header "Content-Type: audio/mp3" --header "Transfer-Encoding: chunked" --data-binary @"Desktop/fichier.mp3" "https://stream.watsonplatform.net/speech-to-text/api/v1/recognize?continuous=true"


URI : Uniform Resource Identifier  /!\  != liens vers la ressource
URL : Uniform Resource Locator

accéder aux ressources: la première partie de l'URI est toujours la ressource, on peut récupérer tous les objets d'une catégorie

Une représentation désigne toutes les informations (données et métadonnées) utiles qui décrivent une ressource.

format d'une requête : 

	verbe URI verion HTTP en-têtes corp

en-têtes : contient les info sur le client. Ex: date, langue, cookie (plutôt explorateur)
corps : souvent vide ou les info qu'on veut envoyer


avantages de REST :

* couplage client-serv faible comparé aux méthodes du type Remote Procedure Call (RPC) comme SOAP
* uniformisation des APIs
* plus grande tolérance à la panne
* app facilement portable et extensible

### API

Application Programming Interfaces. En utilisant l'API d'une appli on a accès à des données utiles, par exemple des info météo

Une API sers d'interface entre 2 appli afin qu'elles puissent communiquer


types d'API : REST, SOAP, JavaScript, XML-RPC, Atom



### Laravel/Symfony -> Interaction avec REST

**TO DO**

### Requêtes HTTP

<table>
<tr>
<th>Http verb</th>
<th>CRUD</th>
<th>Entire Collection (e.g. /customers)</th>
<th>Specific Item (e.g. /customers/{id})</th>
</tr>

<tr>
<td>POST</td><td>Create</td><td>201 (Created), 'Location' header with link to /customers/{id} containing new ID.</td><td>404 (Not Found), 409 (Conflict) if resource already exists..</td>
</tr>


<tr>
<td>GET</td><td>Read</td><td>	200 (OK), list of customers. Use pagination, sorting and filtering to navigate big lists.</td><td>200 (OK), single customer. 404 (Not Found), if ID not found or invalid.</td>
</tr>


<tr>
<td>PUT</td><td>Update/Replace</td><td>405 (Method Not Allowed), unless you want to update/replace every resource in the entire collection.</td><td>200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid.</td>
</tr>


<tr>
<td>PATCH</td><td>Update/Modify</td><td>405 (Method Not Allowed), unless you want to modify the collection itself.</td><td>200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid.</td>
</tr>


<tr>
<td>DELETE</td><td>Delete</td><td>405 (Method Not Allowed), unless you want to delete the whole collection—not often desirable.</td><td>200 (OK). 404 (Not Found), if ID not found or invalid.</td>
</tr>


<tr>
<td></td><td></td><td></td><td></td>
</tr>
<table>


verbes : 

GET : recup un fichier
POST: envoie des données (qu'on met dans le corp) et le serv décide quoi faire avec les data
PUT: envoie les données et impose au serveur ce qu'on fait
DELETE : suppr une resource

format d'une requête : 

	verbe URI verion HTTP en-têtes corp

en-têtes : contient les info sur le client. Ex: date, langue, cookie (plutôt explorateur)
corps : souvent vide ou les info qu'on veut envoyer

format d'un réponse:

	version HTTP code HTTP En-têtes Corps

en-têtes: similaire à la requpete mais aura des info du serv également
corps: les données demandées (avec REST en JSON)


reminder codes HTTP :
100: continue (envoie le corp une fois le header reçu)
101 : switch protocol (le client a demandé au serv de changer de protocol et le serv  accepte)
200: okay
201: created (par exemple en retour d'un post)
202 : accepted ressource acceptée pour processing
300: redirection
301 : moved permanently
400 : pb de ressource Bad request
401 : Unauthorized (need authentification)
402 : payment required
403 : Forbiden (not enough privileges)
404 : Not found 
418 : I'm a teapot
500: internal server error
501 not implemented
502 bad gateway

Réalisation :
- WS
