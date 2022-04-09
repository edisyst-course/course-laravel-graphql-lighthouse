# vue-apollo-client

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Branch del client
Ho creato due branch
- **main** (non c'è il paginatore - è indietro di 2 lezioni)
- **pagination** (c'è il paginatore e un validatore del form Add Task)

```
npm install --save axios
npm install -g @vue/cli
vue add vuex
vue add router
```

### Auth
https://laravel.com/docs/9.x/sanctum#mobile-application-authentication

Copio quella parte in routes/api.php

In Login.vue axios chiama http://127.0.0.1:8000/api/sanctum/token 
- se l'user esiste mi manda a Tasks.vue
- se non esiste restituisce un 422

