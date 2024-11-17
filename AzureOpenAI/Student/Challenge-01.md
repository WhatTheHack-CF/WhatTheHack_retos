# Reto 01: Prompt Engineering

[< Reto Anterior](./Challenge-00.md) -  **[Home](../README.md)** - [Siguiente reto >](./Challenge-02.md)

## Prerrequisitos

* Implementa tus propios modelos AOAI en el [portal de Azure OpenAI Studio](https://oai.azure.com/portal/).
* Actualiza el archivo `.env.sample` (y guárdalo como `.env`) con los nombres de tus modelos implementados si aún no lo has hecho.

## Introducción

A medida que los Modelos de Lenguaje Grande (LLMs) crecen en popularidad y uso en todo el mundo, la necesidad de gestionar y monitorear sus resultados se vuelve cada vez más importante. En este desafío, aprenderás a usar técnicas de 'Prompt Engineering' para generar los resultados deseados al usar un LLM.

## Descripción
Despliegue de modelos para el desafío:
- Implementa los siguientes modelos en tu recurso de Azure OpenAI:
  - `gpt-4`
  - `gpt-35-turbo`

**NOTA:** Para las familias de modelos actualmente disponibles, por favor consulta este enlace para más información: [Modelos del Servicio Azure OpenAI](https://learn.microsoft.com/es-mx/azure/ai-services/openai/concepts/models).

- Añade las credenciales requeridas de los recursos de Azure en el archivo ``.env``. Siéntete libre de hacer cualquier modificación necesaria y luego renombra el archivo `.env-sample` a `.env`.

### Preguntas que deberías ser capaz de responder al final de este desafío:
- ¿Qué es el principio de prompting iterativo?
- ¿Qué hiperparámetros podrías ajustar para hacer que la respuesta sea más diversa en términos de lenguaje?
- ¿Qué técnica de 'prompt engineering' podrías usar para ayudar al modelo a completar tareas difíciles como problemas matemáticos?

### Tareas a realizar
Ejecuta el siguiente Jupyter Notebook para completar las tareas de este desafío:
- `CH-01-PromptEngineering.ipynb`

El archivo se puede encontrar en tu Codespace bajo la carpeta `/notebooks`.

### Secciones en este Desafío:
1. Experimentación con Parámetros
2. Ingeniería del Mensaje de Sistema (System Message)
3. Principios de Prompting Iterativo:

   3.1 Escribe instrucciones claras y específicas
   
   3.2 Dale al modelo tiempo para "pensar"

## Criterios de Éxito
Para completar este desafío con éxito:

- Haz que todas las celdas de código del Jupyter Notebook indicado se ejecuten correctamente.

Al ejecutar las celdas podrás:
- Comprender los tipos de tareas que pueden realizar los modelos de Azure OpenAI.
- Comprender los diferentes hiperparámetros en los modelos de Azure OpenAI.
- Comprender los diferentes escenarios de uso de las técnicas de Prompt Engineering.
- Realizar prácticas de Prompting Iterativo en el ejercicio


## Recursos Adicionales
- [Técnicas de Prompt engineering](https://learn.microsoft.com/es-mx/azure/cognitive-services/openai/concepts/prompt-engineering)
- [Diseño de Mensajes de Sistema](https://learn.microsoft.com/es-mx/azure/cognitive-services/openai/concepts/advanced-prompt-engineering?pivots=programming-language-chat-completions)
- [Seguridad en el Mensaje de Sistema](https://learn.microsoft.com/es-mx/azure/cognitive-services/openai/concepts/system-message)
- [Introducción al Azure AI Studio](https://learn.microsoft.com/es-mx/training/modules/introduction-to-azure-ai-studio/)
- [¿Cuándo usar el Ajuste Preciso (Fine-Tuning) de Azure OpenAI?](https://learn.microsoft.com/es-mx/azure/cognitive-services/openai/how-to/prepare-dataset)
- [Personalizar un modelo con Ajuste Preciso (Fine-Tuning)](https://learn.microsoft.com/es-mx/azure/cognitive-services/openai/how-to/fine-tuning?pivots=programming-language-studio)

## Siguientes pasos
Ahora puedes proseguir con el [Siguiente reto >>](./Challenge-02.md)