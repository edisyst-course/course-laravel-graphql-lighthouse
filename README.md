# Install Lighthouse
`laravel new course-laravel-graphql-lighthouse --github="--public" --branch="main" --organization="edisyst-course"`

Popolo il DB degli utenti almeno `pa migrate:fresh --seed`

    composer require nuwave/lighthouse
    php artisan vendor:publish --tag=lighthouse-schema

Mi crea il file `graphql/schema.graphql` con lo **schema** di default

Potrei provare `php artisan lighthouse:ide-helper` 

Mi sono installato il plugin di PHPStorm
- Nell'elenco plugin di PHPStorm è il primo che trovo
- altrimenti lo trovo su https://plugins.jetbrains.com/plugin/8097-js-graphql

    composer require mll-lab/laravel-graphql-playground

Da adesso nella rotta `/graphql-playground` posso usare Lighthouse 


# Prima interrogazione
```angular2html
{
  users {
    id
    name
    # email
  }
}
```
La prima volta dà errore: basta sostituire `@paginate(defaultCount: 10)` con `@all` per farlo fungere

Se guardo Playgound, vedo che la chiamata è verso `http://127.0.0.1:8000/graphql`, la stessa che farei con Postman


# Configurazione Schema
In `vendor/nuwave/lighthouse/src/Schema/Types/Scalars/DateTime.php` ho la definizione di `DateTime`

In https://lighthouse-php.com/5/api-reference/directives.html trovo tutte le direttive


# Altre query
```angular2html
{
  tasks {
    id
    name
    user {
      name
    }
  }
}

{
  task(id: 1) {
    id
    name
    user {
      name
    }
  }
}
```


# Paginate
```angular2html
{
    users (first: 2, page: 2) {
        data {
            id
            name
            email
        }
        paginatorInfo {
            currentPage
            lastPage
            lastItem
        }
    }
}
```


# Mutations
## Create
```angular2html
mutation {
  createTask (user_id: 1, name: "Task due") {
    id
    name
    user {
      name
      email
    }
    created_at
  }
}
```

## Update
```angular2html
mutation {
  updateTask (id: 1, name: "Task uno modificato") {
    id
    name
    user {
      name
      email
    }
    created_at
    updated_at
  }
}
```

## Delete
```angular2html
mutation {
  deleteTask (id: 3) {
    id
    name
    user {
      name
      email
    }
    created_at
    updated_at
  }
}
```

## Create (con input separato)
```angular2html
mutation {
  createTask (input: {user_id: 1, name: "ta9"}) {
    id
    name
    user {
      name
      email
    }
    created_at
  }
}
```
