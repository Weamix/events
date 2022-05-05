# GraphQL & .Net Core
Par Clément Fasquel (TL .Net Core chez Eurotunnel)

```
Compatible avec du REST
Pensé par Facebook pour du mobile (dans l'idéee de limiter le nombre d'appels réseaux)

Un seul point d'entrée : website.fr/graphl
QueryLangage : avec body sur cet endpoint
HTTP POST 
Toujours des 200
```

Réponse aux problématiques de rigidité du REST
- Overfetching
- Underfetching : plus d'appels si on veut plus d'informations
  GraphQL gère l'imbrication et les jointures entre les tables

## - Query (http post) => récupérer

```
query{
    cars{
    id
    registration
    }
}
```

```
query{
    cars(id:1){
    id
    registration
        options{
            name
            cost
        }
    }
}
```

```
Permet d'éviter l'API Management avec le versionning
S'il y a un ajout d'une donnée, ex. une date de controle technique, il faut rajouter le champ dans la query
VS sur une api REST devoir rajouter le champ dans le retour à l'appel
```

Mappés à des modéles :
- Inputs (lié aux mutations)
- Types (lié aux Queriy, sécurité pour ne pas tout exposer)
- Payloads (partie d'un objet qui nous intéresse)

### Types

UserType
```
public class UserType : ObjetType<User>{

    protected ovveride void Configure(IObjectTypeDescription<User> descriptor){`
        base.configure(descriptor);
        descriptor.Description("User is someone using the app");
        descriptor.Field(p=>p.id).Description("This is the identifier of my user);
        descriptor.Field(p=>p.Birthdate).Ignore();
        
        //resolvers part
        descriptor.Field(p=>p.Events).
        ResolveWith<Resolvers>(p=>p.GetEvents(default!,default!))
        .UseDbContext<DatabaseContext>()
        .Description("Events of a user");
    }
    
}
```

### Resolvers (notion de jointures)

```
private class Resolvers{
    public IQueryable<Event> GetEvents([Parent] User user, [ScopedService] DatabaseContext context){
        return context.Events.Where(p => p.UserId == user.Id); 
    }    
}
```

```
query{
    users{
        id,
        name
    events{
        id,
        name
        }
    }
}
```

### Filters
Avec HotChocolate : [UseFiltering]
```
query{
    users(where:{id:{eq:2}}){
      name   
    }
}
```

### Sort
Avec HotChocolate : [UseSorting]
```
query{
    events(order:{name: DESC}){
      name   
    }
}
```

## - Mutation (http response) => modifier

```
public class Mutations{
  public async Task<AddUserPayload> AddUserAsync(AddUserInput input, DatabaseContext context)
  {
    var newUser = new User{
      Name = input.name,
      Email = input.email,
    };
    context.Users.Add(newUser);
    await context.SaveChangeAsync();
    
    return new AddUserPayload(newUser);
  }
}
```

```
public record AddUserInput(string name, string email);
```

```
public record AddUserPayload(User user);
```

```
mutation{
  addUser(input : {
    name:"Tommy",
    email:"tommy@pomme.com"
  })
  {
  user{
    id,
    name,
    email
  }
  }
}
```

## - Subscription (web sockets)

### REST vs GraphlQL
```
Non interractif (systeme/syteme)        |           Interacctif, temps réel
Microservices                           |           Application mobile
Objets simples                          |           Objets complexes
Requêtes repetees                       |           Requêtes complexes
```

### Démo avec .Net sur une application d'EDT

```
Avec HotChocolate ce qui permet de faire du GraphQL [ScopedService]

IQueryable permett de faire des requêtes sur le schéma

BananaCakePop (front fourni par HotChocolate) : outil de Query / visualisation : "test your graphQL" 
Sorte de Postman de GraphQL

GraphQL voyager : schéma entre les liens avec les objets graphQL
```

```
public IQueryable<User> GetUsers([ScopedService] DatabaseContext context){
    return context.users;
}
```

```
query{
    users{
    id,
    name
    }
}
```

Alias possible , la data avec l'objet alias au lieu de users

```
query{
    alias : users{
    id,
    name
    }
}
```

Questions :
- Comment limiter l'accès aux données?
  Tout le monde peut querry tout sur la table en gros avec les conditions qu'on veut
  Birthday / password : qu'on puisse pas l'appeller => Types