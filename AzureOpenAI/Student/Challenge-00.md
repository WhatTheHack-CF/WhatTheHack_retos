# Reto 00 - Prerrequisitos - En sus marcas, listos… ¡fuera!

**[Home](../README.md)** - [Siguiente reto >>](./Challenge-01.md)

## Introducción

Gracias por participar en el What The Hack Fundamentos de Azure OpenAI. Antes de que puedas comenzar a hackear, necesitarás configurar algunos prerrequisitos.

## Descripción
En este desafío, configurarás los prerrequisitos necesarios y el entorno para completar el resto del hack, incluyendo:

- Acceso a Azure OpenAI
- GitHub Codespaces
- Configurar Azure OpenAI

### Acceso a Azure OpenAI

Necesitarás una suscripción a Azure para completar este truco. Si no tienes una, obtén una prueba gratuita aquí...

- [Suscripción a Azure](https://azure.microsoft.com/es-mx/free/)

Es necesaria una suscripción a Azure para poder crear un recurso de Azure OpenAI y acceder a sus modelos.

### GitHub Codespaces

Para facilitar el desarrollo y evitar complicaciones con dependencias, utilizaremos **GitHub Codespaces**. Este es un entorno de desarrollo alojado en la nube, accesible desde tu navegador, que simplifica considerablemente la configuración inicial.

Debes tener una cuenta de GitHub para poder utilizar GitHub Codespaces. Si no tienes una cuenta de GitHub, puedes [Registrarte Aquí](https://github.com/signup).

Cada cuenta personal de GitHub incluye un plan gratuito que ofrece 120 horas núcleo (60 horas de tiempo real de ejecución en un Codespace de 2 núcleos) así como 15 GB de almacenamiento al mes para operar Codespaces, lo que te permite trabajar sin preocuparte por la configuración local de tu equipo. Puedes revisar el saldo de tus horas disponibles en la [página de facturación de GitHub](https://github.com/settings/billing/summary).

El GitHub Codespace para este hack albergará los archivos de Jupyter Notebook, los archivos de configuración y otros archivos de datos necesarios para este desafío. 

### Comencemos
Para comenzar, sigue estos pasos:

1. Inicia sesión con tu cuenta personal de GitHub. Por favor NO uses una cuenta gestionada por tu empresa.

2. Accede al [repositorio de Codespace de WTH Fundamentos de Azure OpenAI](https://github.com/WhatTheHack-CF/wth-oaifundamentals) que usaremos para el hack.

3. Verás que el repositorio es una plantilla. Utiliza esta plantilla para crear un repositorio público en tu cuenta personal. NO Hagas fork del proyecto, crea una copia del repositorio a partir de la plantilla. Puedes colocar el nombre `wth-aoai` al repositorio y el acceso público.

4. Dentro de tu nuevo repositorio, crea un Codespace seleccionando la opción "Code", luego "Codespaces" y luego "Crear codespace en main". 

Tu entorno de Codespace debería cargarse en una nueva pestaña del navegador. La primera vez que creas el Codespace, tardará aproximadamente entre 3 y 5 minutos en cargarse. Este entorno ya tiene preinstaladas todas las herramientas necesarias, permitiéndote concentrarte completamente en el desarrollo.

Cuando el Codespace termine de cargarse, deberías encontrar una instancia de Visual Studio Code ejecutándose en tu navegador con los archivos necesarios para este hackathon.

### Configuración de Azure OpenAI

Crea un recurso de Azure OpenAI en tu suscripción de Azure y realiza algunas configuraciones iniciales.

- [Crear un Recurso de Azure OpenAI](https://learn.microsoft.com/es-mx/azure/ai-services/openai/how-to/create-resource?pivots=web-portal)
- Implementa los siguientes modelos en tu recurso de Azure OpenAI:
  - `gpt-4`
  - `gpt-35-turbo`
  - `text-embedding-ada-002`

¡Ahora estás listo para configurar y ejecutar los archivos de Jupyter Notebook, muy bien!

#### Configuración del Archivo de Jupyter Notebooks

El código de los Jupyter Notebooks obtiene sus valores de configuración de variables de entorno configuradas en un archivo `.env`. Algunos de estos valores de configuración son secretos (por ejemplo, la clave para acceder a tu recurso de Azure OpenAI).

**NOTA:** Un archivo `.env` nunca debe almacenarse en un repositorio de Git. Por lo tanto, hemos proporcionado un archivo de muestra llamado `.env.sample` que contiene una lista de las variables de entorno requeridas por los Jupyter Notebooks.

Encontrarás el archivo `.env.sample` en la raíz del codespace. 

- Renombra el archivo `.env.sample` a `.env`.
- Añade las credenciales requeridas de los recursos de Azure en el archivo `.env`.

  **SUGERENCIA:** Puedes obtener estas credenciales a través del Portal de Azure dentro de tu recurso AOAI. Haz clic en `Resource Management` > `Keys and Endpoint` desde el menú desplegable en el lado izquierdo.

  **CONSEJO:** Aprende más sobre el uso de archivos `.env` [aquí](https://dev.to/edgar_montano/how-to-setup-env-in-python-4a83#:~:text=How%20to%20setup%20a%20.env%20file%201%201.To,file%20using%20the%20following%20format%3A%20...%20More%20items).
  
**NOTA:** Recursos adicionales de Azure como Azure Document Intelligence (también conocido como Azure Form Recognizer) y Azure AI Search (también conocido como Azure Cognitive Search) serán necesarios para desafíos posteriores. Puedes añadir estos valores al archivo `.env` más adelante a medida que avances en los desafíos.

**NOTA:** También hemos proporcionado un archivo `.gitignore` que debería evitar que accidentalmente hagas un commit de tu archivo `.env` renombrado a un repositorio de Git durante este desafío.


## Criterios de Éxito

Para completar este desafío con éxito, deberías poder:

- Verificar que tienes los siguientes archivos y carpetas disponibles en el Codespace:
    - `/data`
    - `/notebooks`
    - `.env` <= Renombrado a partir de `.env.sample`
    - `.gitignore`
    - `requirements.txt`
- Verificar que has creado el recurso de Azure OpenAI e implementado los 3 modelos necesarios en tu suscripción de Azure.

## Recursos de Aprendizaje

- [GitHub Codespaces Overview](https://docs.github.com/es/codespaces/overview)
- [Jupyter Notebooks en VS Code](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)
- [Jupyter Notebooks](https://jupyter.org/)
- [Proyecto Jupyter](https://es.wikipedia.org/wiki/Proyecto_Jupyter)
- [¿Cómo configurar el archivo .env en Python?](https://dev.to/edgar_montano/how-to-setup-env-in-python-4a83#:~:text=How%20to%20setup%20a%20.env%20file%201%201.To,file%20using%20the%20following%20format%3A%20...%20More%20items)

## Siguientes pasos
Ahora puedes proseguir con el [Siguiente reto >>](./Challenge-01.md)