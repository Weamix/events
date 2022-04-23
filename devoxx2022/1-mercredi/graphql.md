# Comprendre GraphQL
Présentation de GraphQL avec Kotlin et Spring

Talk : https://cfp.devoxx.fr/2022/talk/YFR-2007/Comprendre_GraphQL

- Init par Facebook en 2012
- Depuis 2018, Fondation Apollo GraphQL (OpenSource) sauf les outils de visualisation

https://www.graphql-java.com/tutorials/getting-started-with-spring-boot/

- Type Component Spring :
  - Query
  - Mutation
  - Subscription (streaming)


- Pas de Map dans les types primitifs : possible de faire une class avec valeur,clef pour contourner ça


- Thread :
```
Directive -> where @defer
@include if
@skipp if
```

- un bon moyen pour mettre fin aux BFF ? (Back for front)


- concate schémas de X équipes  à travers un Gateway pour obtenir 1 seul et unique graph


- GraphQL envoie toujours en POST
- Renvoie toujours des 200 en résultats (avec l'erreur dans la réponse) #CUBE
