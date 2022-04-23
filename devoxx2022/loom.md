# Loom nous Protègera-t-il du Braquage Temporel ?

Talk : https://cfp.devoxx.fr/2022/talk/IFY-4656/Loom_nous_Protegera-t-il_du_Braquage_Temporel_%3F

- Loom (jdk 19) : 100k thread

- Contre à peine 4k en threads parallèle

```
StartVirtualThread
OfVirtual avec builder
```

```
Continuation
Yield()
Run()
```

- Faire de la délégation quand on ne peut pas implements