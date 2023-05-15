# Comment permettre 100 millions de logins sans interruption de service ? Betclic raconte son Euro 2020 de football

Talk : https://cfp.devoxx.fr/2022/talk/HZR-6262/Comment_permettre_100_millions_de_logins_sans_interruption_de_service_%3F_Betclic_raconte_son_Euro_2020_de_football

- Ils ont risqué une faillite avant 2017
- Restructuration : Paris vers Bordeaux (turn over important)


- Legacy sans passation et de doc
- Beaucoup de war rooms les soirs de matches (Euro 2020)


- Tests de perfs en PROD....
- Preprod n'était pas ISO


- APP dynamics pour avoir une visu globale
- Datadog (vs Dynatrace au final chez nous)


- Belle démo de Gatling


- Améliorations :
```
Quick win sur la BD et des corrections pendant les WarRoom

Puis :
Event bus (Amazon SQS)
Varnish (Cache front)
Api gateway : Kong

Transition cloud depuis 2020

```


Stats Euro 2020 :  
- 1 million d'utilisateurs (peu?)
- 100 millions de logins 
- Winamax 6 millions d'users