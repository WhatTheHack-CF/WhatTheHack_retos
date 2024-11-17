# Reto 03: Grounding, Chunking, y Embedding

[< Reto Anterior](./Challenge-02.md) - **[Home](../README.md)** - [Siguiente reto >](./Challenge-04.md)


## Prerrequisitos

* Recurso de Azure AI Search para la indexación y recuperación de información relevante.
* Servicio de Azure OpenAI para Modelos de IA Generativa y Modelos de Embeddings.
* Añade las credenciales necesarias de los recursos anteriores en el archivo `.env`.
* Instala las bibliotecas necesarias en el archivo requirements.txt mediante el comando `pip install -r requirements.txt` si aún no lo has hecho.

## Introducción

Al trabajar con Modelos de Lenguaje Grande (LLM), es importante entender cómo fundamentarlos con los datos correctos. Además, examinarás cómo manejar los límites de tokens cuando tienes muchos datos. Finalmente, experimentarás con embeddings. Este desafío te enseñará todos los conceptos fundamentales - Fundamentación, Segmentación, Incrustación - antes de verlos en acción en el Desafío 4. A continuación, se presentan breves introducciones a los conceptos que aprenderás.

La Fundamentación (Grounding) es una técnica utilizada cuando deseas que el modelo devuelva respuestas confiables a una pregunta dada.
La Segmentación (Chunking) es el proceso de desglosar un documento grande. Ayuda a limitar la cantidad de información que pasamos al modelo.
Una Incrustación (Embedding) es una representación densa de información del significado semántico de un texto.

## Descripción

### Preguntas que deberías poder responder al final del desafío:

- ¿Por qué es importante la fundamentación y cómo puedes fundamentar un modelo LLM?
- ¿Qué es un límite de tokens?
- ¿Cómo puedes manejar los límites de tokens? 
- ¿Cuáles son las técnicas de segmentación?
- ¿Qué ayudan a lograr los embeddings?

### Tareas a realizar
Ejecutarás los siguientes tres Jupyter Notebooks para este desafío:

* `CH-03-A-Grounding.ipynb`
* `CH-03-B-Chunking.ipynb`
* `CH-03-C-Embeddings.ipynb`

Estos archivos se pueden encontrar en tu Codespace bajo la carpeta `/notebooks`.


## Criterios de Éxito

Para completar este desafío con éxito, deberías ser capaz de:
- Verificar que puedes fundamentar un modelo a través del mensaje del sistema.
- Demostrar diversas técnicas de segmentación.
- Demostrar cómo crear embeddings.

## Recursos Adicionales

* [Fundamentar LLMs](https://techcommunity.microsoft.com/t5/fasttrack-for-azure/grounding-llms/ba-p/3843857)
* [Ejemplo de Embeddings](https://github.com/openai/openai-cookbook/blob/main/examples/Embedding_Wikipedia_articles_for_search.ipynb)
  
## Siguientes pasos
Ahora puedes proseguir con el [Siguiente reto >>](./Challenge-04.md)