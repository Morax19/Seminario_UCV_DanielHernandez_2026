# Capítulo 4 (borrador) — Tecnologías y Herramientas de Implementación

> Sección trasladada desde el Capítulo 2 (Marco Teórico), a petición del autor:
> el Capítulo 2 conserva únicamente definiciones teóricas y los detalles de
> implementación corresponden al Capítulo 4 (Propuesta de Solución).
> Nota: al integrarla, renumerar las referencias [38]-[48] según su posición final.

**Tecnologías y Herramientas de Implementación**

La selección tecnológica del sistema obedece a tres restricciones derivadas del planteamiento del problema: el modelo de lenguaje debe poder ejecutarse localmente o consumirse mediante una API externa, la configuración debe quedar en manos del usuario, y todas las capas deben comunicarse mediante formatos abiertos para evitar el bloqueo tecnológico. A continuación se describe la pila propuesta, organizada por capa.

**Ejecución e Inferencia de Modelos**

Para el modo local se propone Ollama como capa de orquestación de modelos sobre llama.cpp, ambos de código abierto [38] [39]. llama.cpp permite ejecutar modelos en formato cuantizado GGUF sobre CPU y aceleradores, ajustando explícitamente la relación entre precisión y consumo de memoria mediante niveles de cuantización (por ejemplo, 4 bits, 8 bits), mientras Ollama expone un servicio local con gestión de modelos y una API REST. Cuando la inferencia requiere GPUs dedicadas y alto rendimiento concurrente, se recurre a vLLM, cuyo mecanismo PagedAttention optimiza la administración de la memoria caché de atención y mejora el rendimiento del servicio [40].

Para el modo remoto, el sistema consume un servicio compatible con la API de OpenAI, extremo común que permite alternar entre ejecución local y proveedores en la nube mediante un cambio de configuración. Los parámetros expuestos al usuario comprenden el identificador del modelo, la dirección base del servicio, la clave de acceso, la temperatura, el top-p, la longitud máxima de generación, la ventana de contexto y el nivel de cuantización.

**Orquestación de Agentes**

El código del sistema se implementa en Python y la coordinación del flujo de cuatro agentes se modela con LangGraph, una biblioteca que representa los flujos como grafos de estado con nodos que ejecutan agentes y aristas condicionales que determinan el camino, además de ofrecer persistencia del estado, reanudación desde puntos de control e intervención humana entre etapas [41]. Modelos de referencia como AutoGen documentan los patrones de conversación multiagente que este diseño adapta [22].

**Generación de Salidas Estructuradas**

Cada transición entre agentes se valida contra un JSON Schema [24] mediante Pydantic [25], y cuando el proveedor lo soporta se activa la decodificación restringida descrita con anterioridad [26] para garantizar la validez sintáctica en generación.

**Almacenamiento Vectorial**

Los fragmentos de los documentos fuente se indexan en Chroma, una base de datos vectorial embebible que se ejecuta en el mismo proceso de la aplicación y permite desplegar el sistema completo en una máquina local [42]. Para escenarios con requisitos de concurrencia superiores se contempla la extensión pgvector sobre PostgreSQL [43] [44].

**Almacenamiento de Grafos**

El grafo de conocimiento se persiste en Neo4j [32], en su edición de código abierto, consultado mediante Cypher; la ontología formal y sus restricciones se conservan en paralelo en los estándares W3C descritos con anterioridad [27] [28] [30].

**Almacenamiento Relacional y Analítico**

PostgreSQL [43] sostiene los datos operativos y los metadatos del sistema, mientras que DuckDB [45] ofrece un motor analítico embebido que consulta directamente archivos columnares Parquet, lo que permite realizar pruebas y análisis locales sin levantar un servidor de bases de datos.

**Transformación y Modelado de Datos**

La construcción del modelo dimensional se expresa como código con dbt, que transforma tablas en bruto mediante SQL versionado, materializa modelos, ejecuta pruebas de calidad y documenta el linaje de los datos [46]. La orquestación de los flujos de ejecución (incluida la extracción previa de texto de los documentos fuente) puede delegarse a un programador de tareas como Apache Airflow o Prefect.

**Visualización y Reportes de BI**

Los tableros finales se construyen sobre Apache Superset [47] o Metabase [48], ambos de código abierto, que consumen el almacén dimensional y publican los indicadores generados por el sistema.

La tabla siguiente resume la correspondencia entre los cuatro agentes del sistema y las tecnologías descritas:

| Agente | Responsabilidad | Tecnologías principales |
| --- | --- | --- |
| 1. Extracción | Lee documentos no estructurados y extrae entidades y clases candidatas | Modelo configurable (Ollama/llama.cpp, vLLM o API), extracción de texto, JSON Schema + Pydantic |
| 2. Estructuración | Construye la ontología y materializa la base de datos y el grafo de conocimiento | OWL/RDFS + SHACL, Neo4j (Cypher), DDL SQL, dbt |
| 3. Respuesta GraphRAG | Responde peticiones de usuario y genera salidas estructuradas en JSON | Neo4j, SPARQL/Cypher, Chroma (indexación documental), JSON Schema |
| 4. Inteligencia de negocios | Genera el modelo dimensional y responde preguntas de BI | dbt, PostgreSQL, DuckDB, NL2SQL, Superset/Metabase |
| Orquestación | Coordina el flujo, la configuración del modelo y la validación entre etapas | Python, LangGraph, Pydantic |

---

## Referencias asociadas (reenumerar al integrar)

[38] Ollama, "Ollama," 2026\. [En línea]. Disponible en: [https\://ollama.com](https://ollama.com)

[39] G. Gerganov et al., "llama.cpp," GitHub, 2026\. [En línea]. Disponible en: [https\://github.com/ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

[40] W. Kwon et al., "Efficient memory management for large language model serving with PagedAttention," en *Proc. 29th Symposium on Operating Systems Principles (SOSP)*, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2309.06180](https://arxiv.org/pdf/2309.06180)

[41] LangChain, "LangGraph," 2026\. [En línea]. Disponible en: [https\://langchain-ai.github.io/langgraph/](https://langchain-ai.github.io/langgraph/)

[42] Chroma, "Chroma," 2026\. [En línea]. Disponible en: [https\://www.trychroma.com](https://www.trychroma.com)

[43] PostgreSQL, "PostgreSQL," 2026\. [En línea]. Disponible en: [https\://www.postgresql.org](https://www.postgresql.org)

[44] pgvector, "pgvector," 2026\. [En línea]. Disponible en: [https\://github.com/pgvector/pgvector](https://github.com/pgvector/pgvector)

[45] DuckDB, "DuckDB," 2026\. [En línea]. Disponible en: [https\://duckdb.org](https://duckdb.org)

[46] dbt Labs, "dbt (data build tool)," 2026\. [En línea]. Disponible en: [https\://www.getdbt.com](https://www.getdbt.com)

[47] Apache Software Foundation, "Apache Superset," 2026\. [En línea]. Disponible en: [https\://superset.apache.org](https://superset.apache.org)

[48] Metabase, "Metabase," 2026\. [En línea]. Disponible en: [https\://www.metabase.com](https://www.metabase.com)
