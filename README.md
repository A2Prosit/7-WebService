
Team
Animateur : Gillyyyyyyyyy
Secrétaire : Fantou
Scribe : Flo
Gestionnaire : Yugo

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

Une API permet d'accéder à des données d'une application sur une autre application. Par exemple, si on a une API météo, on peut utiliser la température {...} de manière rapide, sur n'importe quelle plateforme, en passant par des technologies des standards du Web (pas lié à un OS ou un langage).



Ce sont des systèmes logiciels, permettant à deux systèmes logiciels de communiquer sur un réseau informatique. Ils passent par un langage lisible par un ordinateur (WSLD), ou en utilisant sa description (SOAP).
Généralement, on l'utilise avec XML pour sérialiser les messages HTTP comme protocoles réseau.

Web service = **Architecture orienté services**, fonctionne au niveau macro :

-   Le fonctionnement d'un service est défini par un contrat
-   Le langage informatique d'implémentation du service n'importe pas
-   L'échange d'information entre services doit être standardisé
-   La manière d'utiliser le service est définie par une interface
-   Le service ne laisse pas transparaître la manière dont il est implémenté dans son interface
-   Le service doit pouvoir se décrire aux autres agents
-   Le service doit pouvoir être découvert par un mécanisme
-   Transactions, sécurité, etc.


⇒ **UDDI **(Universal Description Discovery and Integration Service) : Norme qui définit le mécanisme pour découvrir dynamiquement des services. Ce sont l'équivalent des pages jaunes des services.

Les appels depuis un client vers un Web Service, sont effectués via le protocole **SOAP** (Simple Object Access Protocol). **SOAP** offre le transport d'objets sérialisés et d'autres données en XML / appel de procédures distantes. SOAP est aussi une norme. SOAP est appelé 'L'enveloppe'.

![](https://benoitpiette.com/labo/img/arch-typique.png)

Le langage **WSDL** (Web Service Definition Language) décrit l'interface au service, en utilisant XML, il fait passer ses entrées et les retours d'appel de service au Web. Il utilise les numéros de port pour définir la connexion au service web.

On y retrouve :

-   la balise types : définie les type de données utilisés par le service en utilisant généralement xml schema
-   les balises message : une abstraction plus haut niveau des paramètres (messages) pour les appels possibles au service Web
-   le balise portType : contient des abstractions haut niveau des opérations possibles du service Web.
-   la balise binding : défini les liens entres les opérations du service Web et le protocole de communication utilisé (généralement SOAP). C'est ici qu'on défini comment on utilise SOAP, les paramètres d'entrées et de sorties.
-   les balises service et port : la balise service contient contient les points limites (port). Le port est défini par les binding du protocole réseau et une addresse réseau.


### API - REST :

REST a été crée en 2000 par Roy Fielding.

Rest est basée sur HTTP,  c'est un style d'architecture opposé à SOAP (protocole)

-   Sans état ⇒ Serveur n'a aucune idée de l'état du client entre deux requêtes.
-   Cacheable (avec cache = mémoire) ⇒  Le client doit pouvoir conserver données en mémoire.
-   Orienté client-serveur
-   Avec une interface uniforme
-   Avec un système de couche
-   Un code à la demande (optionnel)
![](https://s3-eu-west-1.amazonaws.com/sdz-upload/prod/upload/clients_servers2.png)

REST peut délivrer en JSON, XML, CSV, RSS....


SOAP : Contrairement à REST, SOAP n'est pas quelque chose de structuré, mais protocolaire, il définit avec des règles stricte une méthode de communication entière. Un client développé avec SOAP ressemble à un logiciel d'ordinateur car il est liéeà un serveur. Si modification d'un côté ou de l'autre, ça plante. Il faudra faire des MAJ client. Il doit connaître tout les élements qu'il va utiliser.

REST a l'pposé, utilise des standards, accéssible par tout les clients. On peut utiliser du HTTP ou du FTP. 
Le client doit iniduqer uniquement  que le point d'entrées ainsi que les données attendus.
⇒ Restful = Application respectant pleinement REST.


