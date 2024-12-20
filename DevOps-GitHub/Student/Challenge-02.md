# Reto 02 - Añadir una Funcionalidad a la Aplicación Existente

[< Reto Anterior](./Challenge-01.md) - **[Home](../README.md)** - [Siguiente reto >](./Challenge-03.md)

## Introducción

El refugio sabe que hay mucho trabajo por hacer en la aplicación. Debido a que están intentando mover las cosas en la dirección correcta, quieren hacer un cambio rápido para asegurarse de que sus procesos de DevOps funcionen correctamente. Para lograrlo, el refugio desea mostrar las horas en las que el refugio está abierto durante el día actual. El refugio abre de 10 a.m. a 4 p.m. de lunes a viernes, y de 9 a.m. a 8 p.m. los sábados y domingos. Les gustaría tener esto como un nuevo componente de React en el proyecto para que pueda ser utilizado en diferentes lugares de la aplicación.

## Descripción

Con el entorno de desarrollo creado y configurado, es hora de programar. Aunque el proyecto utiliza [Next.js](https://nextjs.org)/[React](https://reactjs.org), no todos somos expertos en esos frameworks. Incluso los expertos pueden tener dificultades a veces para recordar la sintaxis. Y ningún desarrollador disfruta de las tareas tediosas que a menudo surgen al escribir código. GitHub Copilot es un programador auxiliar de IA entrenado con miles de millones de líneas de código y texto públicamente disponibles, diseñado para ofrecer sugerencias de código que mejoren y agilicen tu proceso de desarrollo.

> **IMPORTANTE:** Como se destacó anteriormente, no se requiere experiencia en programación para este reto. Si necesitas la solución, sigue leyendo y encontrarás el código necesario. Intenta hacerlo por ti mismo y, si te atoras, como último recurso, revisa el código proporcionado más abajo.

Para este desafío, crearás un nuevo componente React llamado **Hours.js** en la carpeta **components**. Añadirás el código necesario para mostrar las horas del día actual de la semana. Después de crear el componente, actualizarás **index.js** en la carpeta **pages** para importar el componente recién creado y mostrarlo en la página.

> **IMPORTANTE: NO** hagas commit de los archivos en la rama main. En un desafío próximo crearás un pull request. Por ello, se recomienda que primero crees una nueva rama (branch) y en ella realices la siguiente implementación:

- Agrega el código del componente Hours (el archivo se llama **Hours.js** en la carpeta *components*).
    - Recuerda que te podemos proveer el archivo ya listo si tienes dudas.
- La sintaxis para importar el componente Hours en **index.js** es `import Hours from '../components/Hours';`, y se puede colocar debajo de la línea que dice `// TODO: Import Hours component`.
- La sintaxis para mostrar el componente `Hours` en **index.js** es `<Hours />`, y se puede añadir inmediatamente debajo de la línea que dice `{/* TODO: Display Hours component */}`.
- Para los propósitos de este desafío, puedes leer el día actual desde el navegador sin tener en cuenta la zona horaria del usuario.

## Criterios de Éxito

- Has creado un nuevo componente llamado Hours que muestra las horas del día actual.
- El componente `Hours` es llamado en **index.js**.
- El horario del día actual se muestra correctamente en el sitio.

## Recursos de Aprendizaje

- [Comenzando con React](https://es.react.dev/learn)
- [Introducción a GitHub Copilot](https://docs.github.com/es/copilot/using-github-copilot/getting-started-with-github-copilot)
- [Prueba Gratuita por 30 días de GitHub Copilot](https://github.com/github-copilot/signup)
- [Obtención de acceso gratuito a Copilot como estudiante, profesor o mantenedor de código abierto](https://docs.github.com/es/copilot/managing-copilot/managing-copilot-as-an-individual-subscriber/managing-your-copilot-subscription/getting-free-access-to-copilot-as-a-student-teacher-or-maintainer)

## Tips

- Todos los componentes de React necesitan `import React from 'react'; en la parte superior del archivo.
- GitHub Copilot ofrece sugerencias basadas tanto en código como en comentarios. Puedes describir en lenguaje natural la tarea que estás intentando realizar y Copilot ofrecerá sugerencias.
- Reescribir comentarios puede ayudar a que Copilot ofrezca diferentes sugerencias más cercanas a lo que estás buscando.
- No te preocupes si no tienes experiencia programando. Aquí puedes encontrar un [link para el archivo Hours.js](https://gist.github.com/luislogosmx/a0a73bec9098e3e23206eb6a085b240c).
- Puedes obtener una prueba gratuita de un mes de GitHub Copilot para ayudarte en este reto.

[<  Reto Anterior](./Challenge-01.md) - **[Home](../README.md)** - [Siguiente reto >](./Challenge-03.md)
