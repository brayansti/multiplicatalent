# Reto Front End Developer Medium/Senior
Proyecto Reto para el cargo: Front End Developer Medium/Senior Realizado con Vue.js y utilizando html5 CSS(SASS) y Javascript(vanilaJS).

Este aplicativo consume un servicio REST para mostrar un listado de colores al usuario, que mediante un click podrá seleccionar un color y copiar al portapapeles su respectivo código en formato Hexadecimal.


## URL Repositorio (github)
[https://github.com/brayansti/multiplicatalent/](https://github.com/brayansti/multiplicatalent/).

## URL deploy (servidor netlify)
[https://eloquent-jepsen-549b72.netlify.com/](https://eloquent-jepsen-549b72.netlify.com/).

## Configuración del proyecto
```
npm install
```

### Compilar y live reload en desarrollo
```
npm run serve
```

### Compila y minifica para producción
```
npm run build
```

### Lints y fixes a los archivos
```
npm run lint
```

### Dependencias Utilizadas

| Plugin | Documentacíon |
| ------ | ------ |
| Vue-fontawesome |[Ver](https://github.com/FortAwesome/vue-fontawesome) |
| Animate.css |[Ver](https://github.com/daneden/animate.css) |
| Vue-axios |[Ver](https://www.npmjs.com/package/vue-axios) |

### Puntos Extras
Con el fin de cumplir con todos los objetivos, todos los puntos extra fueron realizados:

 - Utilizar algún framework de front end para el desarrollo de la aplicación --- (Vue.js)
 - Modularizar los componentes en forma ordenada y con su CSS correspondiente --- (Hay dos componentes, CardColor y ModalCopy cada uno con sus hojas de estilo SASS correspondientes)
 - Utilizar flexbox para el grid --- (Grilla sencilla que se encuentra en _flexgrid.scss)
 - Utilizar git como control de versiones --- El Proyecto se encuentra en gitHub: [https://github.com/brayansti/multiplicatalent](https://github.com/brayansti/multiplicatalent/)
 - Hacer deploy de tu aplicación a un servidor (Netlify, Heroku, Zeit Now) --- Proyecto desplegado en Netlify: [https://eloquent-jepsen-549b72.netlify.com/](https://eloquent-jepsen-549b72.netlify.com/)
 - Utilizar algún framework de CSS para decorar la aplicación --- Se utilizó  Animate.css para animaciones y FontAwesome para iconos. No utilizé bootstrap / foundation o alguno similar por que no lo consideré nesesario.

### Configuración personalizada
Ver [Configuration Reference](https://cli.vuejs.org/config/).