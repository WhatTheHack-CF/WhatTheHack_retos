# Reto 04 - Crear un Entorno de Despliegue

[< Reto Anterior](./Challenge-03.md) - **[Home](../README.md)** - [Siguiente reto >](./Challenge-05.md)

## Introducción

Con la aplicación actualizada, ¡el refugio está listo para comenzar a configurar el despliegue! Han elegido usar Azure para alojar la aplicación. El sitio web se alojará en [Azure Container Apps](https://learn.microsoft.com/es-es/azure/container-apps/overview) y la base de datos en [Azure Cosmos DB para MongoDB](https://learn.microsoft.com/es-es/azure/cosmos-db/mongodb/introduction).

El primer paso será crear y configurar el entorno en Azure. En un reto posterior, configurarás el despliegue continuo para el proyecto.

## Descripción

Para este reto, crearás un [GitHub workflow](https://docs.github.com/es/actions/learn-github-actions/understanding-github-actions) que utiliza un archivo [Azure Bicep](https://learn.microsoft.com/es-es/azure/azure-resource-manager/bicep/overview?tabs=bicep) para configurar los recursos necesarios en Azure. Antes de ello, crearás un grupo de recursos para alojar los recursos de Azure, configurarás una identidad de servicio para otorgar los permisos necesarios a la Action, crearás la Action y la ejecutarás para crear los recursos.

La Configuración como Código (CaC), o configuración como código, es un enfoque para gestionar la configuración del sistema que implica definir los ajustes de configuración en archivos o scripts legibles por máquinas. Esto permite una gestión más eficiente, automatizada y consistente de la configuración del sistema, ya que los cambios pueden realizarse y desplegarse más fácilmente y con mayor control. Con la configuración como código, los ajustes de configuración se almacenan en archivos controlados por versiones, utilizando a menudo una sintaxis declarativa como YAML, JSON o HCL. Estos archivos pueden almacenarse junto con el código de la aplicación, facilitando la gestión de todo el ciclo de vida del desarrollo del software.

Este desafío utiliza [Azure Bicep](https://learn.microsoft.com/es-es/azure/azure-resource-manager/bicep/overview?tabs=bicep), que es un lenguaje específico de dominio para definir la infraestructura de Azure. Ya se ha creado un archivo Bicep para que lo uses (se localiza en la carpeta `config` de tu repositorio). El archivo Bicep:

- Crea una instancia serverless de Azure Cosmos DB para MongoDB.
- Crea los recursos para soportar una Azure Container App.
- Crea la Azure Container App con una imagen predeterminada.
- Configura la Azure Container App con la cadena de conexión para Azure Cosmos DB para MongoDB.

El archivo Bicep requiere un parámetro llamado `namePrefix`, que debe configurarse con 5 caracteres alfanuméricos aleatorios en minúsculas. Es importante mencionar que utilices 5 letras que te ayuden a identificar rápidamente los recursos, como por ejemplo las iniciales de tu nombre. Esto asegurará que todos los recursos tengan un nombre único.

## Tips

**Tip 1.** Debes crear un grupo de recursos en tu suscripción de Azure. Como el nombre lo sugiere, un grupo de recursos sirve para agrupar recursos relacionados en un solo lugar. Puedes crearlo directamente desde el Portal de Azure o utilizar [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/what-is-azure-cli) en una Terminal de tu GitHub Codespace. A continuación, se muestran los pasos para hacerlo desde la Terminal:

1. Inicia sesión en Azure introduciendo el siguiente comando:

    ```bash
    az login --use-device-code
    ```

2. Sigue las instrucciones en pantalla para completar el proceso de autenticación introduciendo el código indicado.

3. Crea un grupo de recursos denominado **pets-workshop** en la región West US ingresando el siguiente comando:

    ```bash
    az group create -n pets-workshop -l westus
    ```

    Puedes utilizar otro nombre para el grupo de recursos y otra región para la ubicación. Sin embargo, se recomienda usar estos valores dado que, por ejemplo, actualmente algunas regiones de Azure presentan problemas de limitación de servicio (como East US) ocasionando que algunos recursos no puedan ser creados, en especial CosmosDB.

4. Registra los proveedores necesarios para los recursos que vas a crear, ejecutando los siguientes comandos uno por uno:

    ```bash
    az provider register --namespace Microsoft.OperationalInsights
    az provider register --namespace Microsoft.ContainerRegistry
    az provider register --namespace Microsoft.DocumentDB
    az provider register --namespace Microsoft.App
    ```

**Tip 2.** Debes crear un service principal, el cual es una identidad de seguridad que utilizan las aplicaciones, los servicios y las herramientas de automatización creados por el usuario para acceder a recursos específicos de Azure. Puedes hacerlo desde el [Portal de Azure](https://jiasli.github.io/azure-notes/aad/Service-Principal-portal.html) o en una Terminal de tu GitHub Codespace. A continuación, se muestran los pasos para hacerlo desde la Terminal:

1. Obtén el ID de tu suscripción de Azure ingresando el siguiente comando (copia el valor devuelto y pégalo en un bloc de notas para utilizarlo en el siguiente paso):

    ```bash
    az account show --query id -o tsv
    ```

2. Crea el service principal que se usará para administrar el grupo de recursos introduciendo el siguiente comando, reemplazando **SUBSCRIPTION_ID** con el ID de suscripción obtenido en el paso anterior (además, observa que se usa el grupo de recursos `pets-workshop`, modifica dicho valor en el comando si utilizaste un nombre distinto al crear el grupo):

    ```bash
    az ad sp create-for-rbac --name pets-workshop-app --role contributor --scopes /subscriptions/SUBSCRIPTION_ID/resourceGroups/pets-workshop --sdk-auth
    ```

    Este comando devuelve un objeto [JSON](https://en.wikipedia.org/wiki/JSON) que sirve como credenciales utilizadas para crear los recursos en Azure e implementar la aplicación.

3. Copia la cadena JSON en un bloc de notas. Utilizarás este valor para registrarlo en un secreto en el paso siguiente.

**Tip 3.** Debes agregar en el repositorio los secretos y variables requeridos en la sección de Actions.

### Secretos a agregar:
1. **AZURE_CREDENTIALS**: Este es un JSON que contiene las credenciales para administrar los recursos de Azure en el workflow.
2. **AZURE_SUBSCRIPTION**: Una cadena que representa el ID de tu suscripción a Azure.

### Variables a agregar:
1. **AZURE_RG**: El nombre del grupo de recursos en Azure, por ejemplo, `pets-workshop`.
2. **AZURE_PREFIX**: Recuerda usar tus iniciales o una combinación de 5 caracteres alfanuméricos en minúsculas que te identifiquen para poder diferenciar tu proyecto.

Para agregar los secretos y variables:
1. Ve a la sección de "Secrets and Variables" en tu repositorio de GitHub.
2. Selecciona "New repository secret" o "New variable" según corresponda.
3. Introduce los valores necesarios y guarda los cambios.

**Tip 4.**
Ahora sí, debes crear el workflow (GitHub Action) para desplegar los recursos en Azure a partir del archivo Bicep existente en combinación con los secretos y variables configurados. Este workflow debe correr bajo demanda (manualmente). Consulta los Recursos de Aprendizaje de este reto para determinar el código a escribir en el archivo .yml. Además, no olvides que el archivo Bicep existente en el repositorio requiere un parámetro `namePrefix`.

### Tip adicional:
- Si estás saturado, aquí puedes encontrar un [ejemplo del archivo](https://gist.github.com/luislogosmx/ad8c3a1d3bc6659fa445541ca2851248) que puedes usar como referencia. Te pedimos que intentes hacerlo por ti mismo antes de utilizar el ejemplo.

### Notas adicionales:
- Este archivo debe guardarse en la ruta `.github/workflows`.
- Este achivo debe existir en la rama `main`, por lo que si estás trabajando en una rama, deberás hacer un pull-request, confirmarlo y hacer merge.
- Para ejecutar manualmente el workflow, debes dar clic en la pestaña **Actions** de tu repositorio, luego en el menú del lado izquierdo busca un workflow llamado **Create Azure resources** (o el nombre que hayas asignado en el archivo), a continuación del lado derecho da clic en el botón **Run workflow** y da clic en el botón verde **Run workflow**. 
- Una vez ejecutado con éxito tu workflow, accede al Portal de Azure para obtener la URL de tu aplicación. Dicha URL se encuentra en Inicio > Navegar > Grupos de recursos > pets-workshop > Busca tu recurso de tipo Aplicación contenedora > Información general > Dirección URL de la aplicación.

## Criterios de Éxito

- Demuestra que has creado un grupo de recursos en Azure para los recursos en la nube a utilizar por la aplicación.
- Demuestra que has almacenado correctamente los valores necesarios para el flujo de trabajo en el repositorio, cifrando los valores que son sensibles.
- Demuestra que has creado un nuevo GitHub workflow llamado **create-azure-resources.yml** con las siguientes opciones:
  - El GitHub workflow puede ser ejecutado manualmente.
  - Lee el prefijo y otros parámetros desde secretos y variables.
- Demuestra que al navegar a la URL de la Aplicación Contenedor de Azure se muestra una pantalla con el mensaje **Welcome to Azure Container Apps**.

> **IMPORTANTE**: La imagen predeterminada en el archivo Bicep incluye todos los recursos necesarios para desplegar la aplicación predeterminada. NO actualices el código del archivo Bicep en este reto 04. 

## Recursos de Aprendizaje

- [¿Qué es la infraestructura como código (IaC)?](https://learn.microsoft.com/es-es/devops/deliver/what-is-infrastructure-as-code)
- [Entender las GitHub Actions](https://docs.github.com/es/actions/learn-github-actions/understanding-github-actions)
- [Guía de inicio rápido: implementación de archivos de Bicep mediante Acciones de GitHub](https://learn.microsoft.com/es-es/azure/azure-resource-manager/bicep/deploy-github-actions?tabs=CLI%2Cuserlevel)
- [Ejecutar un flujo de trabajo manualmente](https://docs.github.com/es/actions/using-workflows/manually-running-a-workflow)
- [Contextos de GitHub Actions](https://docs.github.com/es/actions/learn-github-actions/contexts)
- [Uso de secretos en Acciones de GitHub](https://docs.github.com/es/actions/security-guides/using-secrets-in-github-actions)
- [Variables de GitHub Actions](https://docs.github.com/es/actions/learn-github-actions/variables)
- [Crear secretos de Actions usando GitHub CLI](https://cli.github.com/manual/gh_secret_set)



[< Reto Anterior](./Challenge-03.md) - **[Home](../README.md)** - [Siguiente reto >](./Challenge-05.md)