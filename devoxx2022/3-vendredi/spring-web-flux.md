# Migrer de Spring MVC à Spring Web Flux

Talk : https://cfp.devoxx.fr/2022/talk/RKZ-1909/Migrer_de_Spring_MVC_a_Spring_Web_Flux

- Spring MVC
  - 1 thread =  1 request
  - Parallelisation dépend du nombre de cores sur CPU

    
- Spring web flux 
  - Model reactive
  - Mono & flux
  - Pas de solution pour le OneToMany
  - Reecriture des SQL et du data mapping (pas d'ORM)
  - Cache : mal géré avec model reactive

Dans l'exemple, SpringWebFlux n'était pas la bonne solution au soucis.

Le PB était au niveau de la DB

Intérressant dans un seul cas : un aggregator de plusieurs services 

Si ces services ne tiennent pas la charge 


Warning  : Dans 2 ans, ça sera remplacé potentiellement par Loom?