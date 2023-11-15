<img width="332" alt="Capture d’écran 2023-11-15 à 08 33 11" src="https://github.com/Weamix/events/assets/25066854/c34353d7-21cb-4832-b158-15bd390fca02">
<img width="349" alt="Capture d’écran 2023-11-15 à 08 33 34" src="https://github.com/Weamix/events/assets/25066854/40503538-269e-4a1a-b89b-a094a8454a57"> (coucou Onepay)
<img width="339" alt="Capture d’écran 2023-11-15 à 08 33 52" src="https://github.com/Weamix/events/assets/25066854/ad9012fe-3e53-4056-827c-34d783ea866c">

* plus besoin d'écrire tout le main
  
Java veut se montrer comme un langage scripting et être simple pour faire un petit script (essayer de concurencer python)

* Records (= cree la classe avec les attributs et le constructeur par défaut)

Interface sealed avec les "permits"

Data Oriented Programm (sealed)

Switch case avec les records
Case when

Sealed => risque de bridage par Oracle dans le futur??

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
Avec le code en C de netty entre les JVMs , impossible de déplacer en mode copie virtual threads car la partie de code en C a des pointeurs avec addresses
Lors de la copie, ça créée un décalage.

Faut-il implémenter les virtual threads? Oui si nouveau projet partant de zéro ou si vous avez une app avec plus de 10k calls par seconde.

* integrity platform (more for dev ops)

TLDR : des arguments jvm à couper sinon ça va faire mal.
Dynamoc agents to be disallow

* Q&A :
  
  - 2 records dans le switch case possible 
  - il conseille java 21 à un étudiant (pas apprenti) pourtant le marché?
