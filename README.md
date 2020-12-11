# qualite_air_app

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

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
Ajouter dans le dossier `src\config` un fichier `config.js` dans lequel on ajoutera le token de https://aqicn.org/data-platform/token/#/ :
```js
export const config = {
    token: "xxxxxxxxxxxxxxxxxxxx"
}
```