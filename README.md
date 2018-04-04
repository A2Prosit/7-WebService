
## Mots Clés
- Client Web
- Module Symfony
- API Rest
- Requête HTTP
- Reponse HTTP
- Laravel
- PHP Web Service

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

    Etudes :
- REST
- API
- Laravel/Symfony -> Interaction avec REST
- Requêtes HTTP


Réalisation :
- WS

### Introduction au web services :

Une API (ou service Web) permet d'accéder à des données d'une application sur une autre application. Par exemple, si on a une API météo, on peut récupérer la température {...} de manière rapide, sur n'importe quelle plateforme, en passant par des technologies standardisées du Web (pas lié à un OS ou un langage).

Ces standards passent pas un langage lisible par un ordinateur (WSLD) :

Le langage **WSDL** (Web Service Definition Language) décrit l'interface au service, en utilisant XML, il fait passer ses entrées et les retours d'appel de service au Web. Il utilise les numéros de port pour définir la connexion au service web.

Il existe deux leader sur le marché : SOAP et REST, appuyés sur WSDL :

⇒ NB : **UDDI **(Universal Description Discovery and Integration Service) : Norme qui définit le mécanisme pour découvrir dynamiquement des services. Ce sont l'équivalent des pages jaunes des services.

![](https://benoitpiette.com/labo/img/arch-typique.png)


### API - REST :

REST a été crée en 2000 par Roy Fielding.

Rest est une architecture basée sur HTTP,  opposé à SOAP (protocole) :
- REST a l'opposé, utilise des standards, accessible par tout les clients. On peut utiliser du HTTP ou du FTP.
- Le client doit indiquer uniquement  que le point d'entrées ainsi que les données attendus.des standards, accessible par tout les clients. On peut utiliser du HTTP ou du FTP. 
-   Sans état ⇒ Serveur n'a aucune idée de l'état du client entre deux requêtes.
-   Cacheable (avec cache = mémoire) ⇒  Le client doit pouvoir conserver données en mémoire.
-   Orienté client-serveur
-   Avec une interface uniforme
-   Avec un système de couche
-   Un code à la demande (optionnel)
- REST peut délivrer en JSON, XML, CSV, RSS....

⇒ Restful = Application respectant pleinement REST.

![](https://s3-eu-west-1.amazonaws.com/sdz-upload/prod/upload/clients_servers2.png)



### 

API - SOAP

:
SOAP : Contrairement à REST, SOAP n'est pas quelque chose de structuré, 
mais protocolaire, il définit avec des règles stricte une méthode de 
communication entière. Un client développé avec SOAP ressemble à un 
logiciel d'ordinateur car il est liéeà un serveur. Si modification d'un 
côté ou de l'autre, ça plante. Il faudra faire des MAJ client. Il doit 
connaître tout les élements qu'il va utiliser.
 
Les appels depuis un client vers un Web Service, sont effectués via le protocole **SOAP** (Simple Object Access Protocol). **SOAP** offre le transport d'objets sérialisés et d'autres données en XML / appel de procédures distantes. SOAP est aussi une norme. SOAP est appelé 'L'enveloppe'.

