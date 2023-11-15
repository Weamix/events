* plus besoin d'écrire tout le main
Java veut se montrer comme un langage scripting et être simple pour faire un petit script (essayer de concurencer python)

* Records (= cree la classe avec les attributs et le constructeur par défaut)

Interface sealed avec les "permits"

Data Oriented Programm (sealed)

Switch case avec les records
Case when

* STR = String Template Processor avec anti slash

Format Processor (rapide)

String Template Processor (pas rapide, ne peut pas remplacer les loggers actuellement)
Oracle ne veut pas car risquent que les gens fassents des macros s'ils le rendaient rapides 
Et c'est comme ça que Scala est lent lors de macros.

* Sequenced collection

getFirst() et getLast() sur les list avec java 21 

reversed()

Des collections que personne n'utilisera ? Sûrement très inutiles
SequencedCollection
SequencedSet
SequencedMap

* virtual threads

Virtual threads utiles si plus de 10k calls par seconde
Sur spring juste un param.

Helidon? (nouveau) Versus quarkus

Netty (serv web) n'est pas capable de gérer les virtual threads.

Faut-il implémenter les virtual threads? Oui si nouveau projet partant de zéro ou si vous avez une app avec plus de 10k calls par seconde.

* integrity platform (more for dev ops)

TLDR : des arguments jvm à couper sinon ça va faire mal.
Dynamoc agents to be disallow

* Q&A : 
- 2 records dans le switch case possible 
- il conseille java 21 à un étudiant (pas apprenti) pourtant le marché?