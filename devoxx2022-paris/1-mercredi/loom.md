# Loom nous Protègera-t-il du Braquage Temporel ?

Talk : https://cfp.devoxx.fr/2022/talk/IFY-4656/Loom_nous_Protegera-t-il_du_Braquage_Temporel_%3F

- Loom (jdk 19) : 100k thread

- Contre à peine 4k en threads parallèle (thread, join, sémaphore (lock/unlock))

```
StartVirtualThread
OfVirtual avec builder
```

```
Continuation
Yield()
Run()
```

- Faire de la délégation quand on ne peut pas hériter (classe final notamment). Cela consiste à créer une classe qui a un attribut dans la classe cible que l'on veut surcharger, et à rerouter toutes les méthodes vers celles de l'attribut, sauf celles que l'on veut modifier/surcharger. Pattern "Decorator" ("Delegation" est plutôt le nom du mécanisme que le pattern lui-même).