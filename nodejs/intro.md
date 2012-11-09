#NodeJS

##Ressources utiles pour démarrer:

###Tutoriels :

* [Site officiel - NodeJS.org](http://nodejs.org/)<br/>
* [Node Manual](http://nodemanual.org/latest/)
* [Node Packaged Modules](https://npmjs.org/)
* [NodeTuts](http://nodetuts.com/)
* [How to Node](http://howtonode.org/)
* [Blog rolling with mongoDB, express and Node.js](http://howtonode.org/express-mongodb)
* [NodeBits](http://www.nodebits.org/)

###Screencasts :

* [Introduction to Node.js with Ryan Dahl](http://www.youtube.com/watch?v=jo_B4LTHi3I)
* [Google Tech Talk - Node.js: JavaScript on the Server](http://www.youtube.com/watch?v=F6k8lTrAE2g)
* [Server-side JavaScript with Node, Connect & Express](http://vimeo.com/18077379)
* [Nodecasts](http://nodecasts.net/)
* [NodeTuts](http://nodetuts.com/)


###Divers :

* [Bonnes pratiques sur les dépendances](http://blog.nodejitsu.com/package-dependencies-done-right)
* [Useful Node.js Tools, Tutorials And Resources](http://coding.smashingmagazine.com/2011/09/16/useful-node-js-tools-tutorials-and-resources/)
* [faciliter le debug de nodejs avec inspect](http://docs.nodejitsu.com/articles/getting-started/how-to-use-util-inspect)
* ["Callbacks are the modern goto"](http://elm-lang.org/learn/Escape-from-Callback-Hell.elm)

##Javascript:

* [Google Tech Talk - Javascript : The good parts](http://www.youtube.com/watch?v=hQVTIJBZook)
* [Crockford on Javascript](http://yuiblog.com/crockford/)
* [Eloquent Javascript](http://eloquentjavascript.net/)
* [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/JavaScript)

###JSON:

http://fr.wikipedia.org/wiki/JavaScript_Object_Notation

##Exercices :

### Exercice A :
En utilisant node.js, écrire une application web de chat à l'aide Socket.io



### Exercice B :  

En utilisant Mojolicious:

1) Faire une requete HTTP sur l'api de recherche de twitter en cherchant le terme 'node'

voir https://dev.twitter.com/docs/api/1/get/search 
et http://mojolicio.us/perldoc/Mojo/UserAgent

2) Mesurer le temps passé entre l'envoi de la requête et la fin de cette requête (en ms).

voir http://search.cpan.org/~zefram/Time-HiRes-1.9725/HiRes.pm


### Exercice C :

En utilisant node.js:

1) idem 1) de l'exercice B

voir http://nodejs.org/api/http.html

2) idem 2) de l'exercice B

voir http://www.w3schools.com/jsref/jsref_obj_date.asp

  



##Latence

(cf http://fr.wikipedia.org/wiki/Latence)

Examples de latence: 

* le délai entre une requête à un médium de stockage de données et le début du transfert de l'information demandée. Les latences les plus importantes sont causées par des déplacements mécaniques, par exemple sur un disque dur par le positionnement de la tête de lecture et la rotation du disque ;
* le délai entre une requête d'un client et la réponse du serveur ;

Globalement on peut avoir une latence importante dès lors qu'on effectue des entrées/sorties: http://fr.wikipedia.org/wiki/Entr%C3%A9es-sorties Car les temps d'accès aux disques et au réseaux sont importants.


## bloquant/non-bloquant

mode définissant comment le système accède à un péripherique.

* en mode bloquant une opération d'entrée/sortie ne retournera à l'application qu'une fois l'opération terminée.
* en mode non-bloquant une opération d'entrée/sortie retournera immédiatement à l'application mais sans le resultat de cette opération mais avec éventuellement un code de statut de l'opération ou une erreur. Plusieurs appels peuvent ensuite être requis pour surveiller l'état de cette opération.


## synchrone/asynchrone

type d'appel définissant le comportement du flot d'exécution d'un programme lors d'une opération d'entrée/sortie.

* Une opération d'entrée/sortie est dite synchrone si elle bloque le flot d'exécution jusqu'à ce que l'opération soit terminée.

* Une opération d'entrée/sortie est dite asynchrone si elle libère immédiatement le flot d'exécution, généralement avant que l'opération ne soit terminée.


## opération d'entrée/sortie synchrone et bloquante

Mode d'opération le plus commun, au niveau d'une application, une opération d'entrée/sortie ne nécessite qu'un seul appel et bloque l'application jusqu'à ce que l'opération soit terminée. Pendant ce temps de blocage l'application n'utilise pas d'unité processeur, le système d'exploitation peut donc passer la main à une autre application.


## opération d'entrée/sortie synchrone et non-bloquante

Plusieurs appels souvent nécessaire avant que l'opération ne soit terminée (polling)

## opération d'entrée/sortie asynchrone et bloquante

Permet de passer plusieurs descripteurs de fichier d'entrée/sortie lors d'un appel d'opération.

Des fonctions systèmes peuvent ensuite utiliser ces descripteurs pour suivre l'état d'une opération d'entrée/sortie  (exemple: select, poll, epoll and kqueue) dans ce cas ce sont ces appels de fonctions qui sont bloquants.

## opération d'entrée/sortie asynchrone et non-bloquante

Lors d'une opération d'entrée/sortie le flot d'exécution est immédiatement libéré. Une fois l'opération terminée un événement est émis ou une fonction de callback est executée. L'avantage de ce mode d'opération est d'éviter le blocage de l'application lors d'une opération d'entrée/sortie, l'application peut alors conserver la main sur l'unité de processeur alors que l'opération est toujours en cours. 


Ces 3 derniers modes d'opérations sont dit basé sur des événements (event-based)


##event-loop  

node.js utilisé une boucle d'évenement (event-loop).

Elle est basé sur libuv depuis la version 0.6

Cette boucle tourne tout au long d'un programme.

Pour résumer son action on pourrait l'écrire en pseudocode de la manière suivante:

```
while there are still events to process:  

    e = get the next event  
    
    if there is a callback associated with e:  
    
        call the callback```

http://nikhilm.github.com/uvbook/basics.html




