![][image1]	![][image2]	![][image3]

UNIVERSIDAD CENTRAL DE VENEZUELA

FACULTAD DE CIENCIAS

ESCUELA DE COMPUTACIÓN

CENTRO DE INGENIERÍA DE SOFTWARE Y SISTEMAS – ISYS

**TÍTULO**

**Seminario presentado ante la Ilustre Universidad Central de Venezuela por:**

Br. Daniel A. Hernández F.

**Tutor:**

Prof. Iván Flores V.

**Ciudad Universitaria de Caracas, 2026**

**Resumen**

**Índice General**

**Capítulo 1**

**Problema de la Investigación**

**Planteamiento del Problema**

En la actualidad, las organizaciones han aumentado enormemente su volumen de información gracias a la digitalización. La gran mayoría de los datos generados a nivel corporativo, académico y gubernamental residen en formatos de texto libre o no estructurado, tales como documentos legales, historiales médicos, manuales técnicos, reportes de investigación y transcripciones de interacciones [14].

Resulta usual que la información crítica dentro de estos volúmenes masivos de información debe extraerse y estructurarse para que pueda procesarse de manera computacional, esto resulta útil cuando se buscan formar indicadores claves que den respuestas a métricas de negocio. Tradicionalmente, esta extracción requería de una revisión humana manual o de la implementación de algoritmos de procesamiento de lenguaje natural basados en reglas predefinidas y expresiones regulares, lo que resulta ineficiente dada la ambigüedad y la complejidad semántica de la que es capaz el lenguaje del lenguaje humano.

El rápido avance en el desarrollo y globalización de los Grandes Modelos de Lenguaje (LLMs) se observa como una solución definitiva a este desafío. Dada su arquitectura neuronal profunda, estos modelos demostraron una capacidad sin precedentes para comprender el contexto, resumir información y abstraer entidades a partir de texto libre. Sin embargo, la adopción directa de los LLMs para la extracción automatizada de información en entornos de producción presenta barreras tecnológicas e infraestructurales críticas.

En primer lugar, hacer uso de LLMs comerciales que suelen ejecutarse a través de servicios o APIs de terceros para procesar grandes volúmenes de documentos plantea graves riesgos de confidencialidad y a la privacidad de los datos, ya que puede transmitirse información interna de la organización hacia servidores externos en la nube.

Para dar solución a este problema se propone ejecutar estos modelos masivos de forma local y proveerles la totalidad de los documentos que se desean analizar directamente en las peticiones realizadas, esto que representa un costo altísimo en infraestructura de cómputo dada la naturaleza de la arquitectura detrás de estos modelos y la gran cantidad de información disponible, haciendo que esta alternativa sea prácticamente inviable para organizaciones relativamente pequeñas.

Aunado a esto, cuando a un modelo de lenguaje se le exige razonar sobre ventanas de texto excesivamente largas, disminuye su rendimiento omitiendo información crítica según su ubicación dentro del texto que se analiza o generando respuestas erróneas con total seguridad, esto último es lo que se conoce como alucinaciones, comprometiendo así la integridad de la extracción estructurada de datos.

En busca de mitigar estas limitaciones computacionales y semánticas, la industria adoptó inicialmente arquitecturas de Generación Aumentada por Recuperación (RAG), paradigma que busca evitar la inyección total de los documentos acoplando el LLM a un sistema de recuperación externo para obtener únicamente los fragmentos de información más relevantes antes de generar una respuesta. 

No obstante, el enfoque tradicional de RAG opera de manera secuencial, ya que, al recuperar información basándose en similitud matemática, el sistema no es capaz de razonar sobre la calidad del contexto recuperado, fallando frecuentemente ante instrucciones complejas que requieren agregar información de múltiples fuentes.

En respuesta a ello, el paradigma RAG ha evolucionado hacía alternativas arquitectónicamente más complejas. Entre ellos destacan el RAG Agéntico (que dota al modelo de autonomía para buscar información de forma iterativa), el GraphRAG (que estructura la recuperación apoyándose en grafos de conocimiento para garantizar relaciones lógicas) y el Aprendizaje por Refuerzo (buscando internalizar el conocimiento directamente en los pesos del modelo). Sin embargo, en entornos de ejecución local, donde se tienen recursos de infraestructura limitados, se plantea la duda respecto a cuál de estos enfoques ofrece el mejor equilibrio entre rendimiento y costo.

Por lo tanto, se plantea como propósito fundamental de esta investigación el implementar, evaluar y comparar de manera rigurosa los resultados, el rendimiento computacional y los costos operativos de las arquitecturas *Agentic RAG*, *GraphRAG* y *Aprendizaje por Refuerzo (RL)* aplicadas sobre un Gran Modelo de Lenguaje ejecutado de manera local. Con el fin de contrastar la viabilidad y eficiencia de cada paradigma en la tarea de extracción automatizada de conceptos a partir de diversas fuentes de información no estructurada, permitiendo así determinar la estrategia óptima para estructurar conocimiento garantizando la privacidad de los datos organizacionales.

**Objetivos del Seminario**

**Objetivo General**

Realizar una investigación comparativa sobre los resultados, rendimiento y costos al implementar un sistema/una arquitectura utilizando AgenticRAG, GraphRAG y Reinforcement Learning en un LLM ejecutado de manera local para la extracción de conceptos mediante el procesamiento de diversas fuentes.

**Objetivos Específicos**

* 

**Capítulo 2**

**Marco Teórico**

**Inteligencia Artificial**

Cuando se habla de Inteligencia Artificial, se hace referencia a una disciplina de las Ciencias de la Computación que busca diseñar sistemas capaces de realizar tareas que requieren de la intervención humana, por ejemplo, el reconocimiento de patrones, comprensión y tratamiento del lenguaje e incluso en la toma de decisiones. Inicialmente, los sistemas dependían de reglas explícitamente programadas, sin embargo, debido a la complejidad de los problemas reales surge un subcampo dentro de la inteligencia artificial conocido como Aprendizaje Automático. 

**Aprendizaje Automático**

El Aprendizaje Automático se enfoca en el desarrollo de algoritmos capaces de aprender y extraer características a partir de un conjunto de datos. En lugar de ejecutar instrucciones fijas y explícitamente programadas, un modelo de aprendizaje automático ajusta sus parámetros internos a medida que procesa la información durante su fase de entrenamiento, con el fin de identificar patrones estadísticos. El objetivo principal es conseguir un modelo cuyos resultados sean lo más precisos frente a la realidad; visto de otra forma, se busca minimizar la diferencia (o el error) entre el resultado generado por el modelo sobre datos nuevos y el resultado real esperado.

Dependiendo de la naturaleza de los datos y de la forma en que el algoritmo interactúa con ellos, este enfoque se divide fundamentalmente en tres categorías:

* **Aprendizaje Supervisado:** El modelo se entrena utilizando un conjunto de datos previamente etiquetados. Esto significa que a cada dato de entrada se le asocia de antemano la respuesta correcta o salida deseada. El objetivo del algoritmo es aprender la relación matemática que mapea las entradas con las salidas, permitiéndole generalizar y predecir los resultados correctos cuando se le presenten datos nuevos y desconocidos.  
* **Aprendizaje No Supervisado:** A diferencia del enfoque anterior, aquí se hace uso de datos sin etiquetar. El algoritmo no tiene un resultado "correcto" predefinido que deba imitar, por lo que su objetivo principal es explorar la información para descubrir estructuras ocultas, similitudes o patrones intrínsecos en los datos.  
* **Aprendizaje por Refuerzo:** Este enfoque se basa en la interacción continua de un agente con un entorno dinámico. El modelo no recibe instrucciones explícitas sobre qué acciones tomar, sino que descubre cuáles son las decisiones óptimas a través de un proceso de ensayo y error. Cada acción ejecutada genera un cambio en el entorno y le otorga al agente una recompensa (positiva o negativa). El objetivo del algoritmo es desarrollar una política de actuación que maximice la recompensa acumulativa a largo plazo.

**Algoritmos de optimización y funciones de pérdida**

Sin importar bajo que estrategia de aprendizaje se trabaje, el objetivo principal es que el modelo sea capaz de dar respuestas lo más parecidas posibles a las observadas en la realidad, para medir que tan distantes son estos resultados se emplean las funciones de pérdida, la cuales dependen del modelo y el tipo de problema a resolver [11]. 

Los algoritmos de optimización buscan minimizar no solo la función de pérdida sino el tiempo que toma el entrenamiento del modelo. La función de pérdida genera una superficie n-dimensional, de la cual se busca encontrar el punto mínimo ajustando los parámetros del modelo. Existen diversas funciones utilizadas según el tipo de problema que se quiera resolver, para los problemas de clasificación se usa la Entropía Cruzada.

**Entropía Cruzada**

Esta entropía mide la incertidumbre de una distribución de probabilidad y la Entropía Cruzada cuantifica la diferencia entre dos distribuciones de probabilidad: la distribución real (denotada como $y$) y la distribución de probabilidad estimada por el modelo (denotada como $yˆ$).

Para un único dato de entrenamiento en un problema con $C$ clases posibles, la Función de Pérdida se define matemáticamente como:

$${L}_{CE}=-\sum\limits_{i=1}^{C}{y}_{i}\log log\ \left({{yˆ}_{i}}\right){\ }$$

**Redes Neuronales**

Como se mencionó anteriormente, el mundo real se conforma de datos y problemas cuya complejidad supera la capacidad de procesamiento de algoritmos convencionales del aprendizaje automático, esta es la razón por la que surgen los modelos conocidos como redes neuronales, matemáticamente estos modelos constan de un conjunto de datos de entrada, un conjunto de pesos, un conjunto de sesgos y una función de activación. El proceso fundamental resulta en tomar cada uno de los datos del conjunto de entrada $({x}_{1},\ {x}_{2},\ ...,\ {x}_{n})$*,* multiplicarlo por un elemento del conjunto de pesos $({w}_{1},\ {w}_{2},\ ...,\ {w}_{n})$*,* el cual determina que tan importante es este dato en específico, sumarle un sesgo ${(b}_{1},\ {b}_{2},\ ...,\ {b}_{n})$*.* Finalmente, al resultado de esta operación se le aplica la función de activación $(f){\ }$generando así una salida $(y)$. De forma general el proceso es el siguiente:

$$y\ =\ f\ (\sum\limits_{i\ =\ 1}^{n}({w}_{i}\ ⋅\ {x}_{i})\ +\ {b}_{i})$$

Es importante mencionar que las redes neuronales se organizan en capas conocidas como:

* **Capa de entrada:** Recibe los datos sin procesar, como pueden ser valores numéricos que representan los píxeles de una imagen.  
* **Capas ocultas o capas intermedias:** Se encargan del procesamiento y la extracción de características de los datos, cuando una red neuronal posee más de una capa oculta, hablamos de una red neuronal profunda.  
* **Capa de salida:** Toma los datos después de ser procesados y los lleva al dominio necesario para el contexto del problema, por ejemplo, un valor numérico, una clasificación, los píxeles de una imagen generada.

	Dentro de todos los componentes que se mencionan, la función de activación es el más crítico, ya que, es gracias a la misma que se introduce la no linealidad, funciones como ReLU, Sigmoide o Tangente Hiperbólica permiten que las redes neuronales puedan ajustarse a funciones matemáticas complejas, de lo contrario solo podrían aproximar rectas.

**Funciones de Activación**

El objetivo de esta función es determinar si una neurona de la red debe activarse o no, dependiendo del resultado obtenido por la suma ponderada de los datos de entrada y así propagar este valor a las capaz siguientes. Como se mencionó anteriormente, la finalidad de la función de activación es romper con el comportamiento linear que tiene la multiplicación de las entradas por sus pesos, de lo contrario las redes neuronales funcionarían de la misma manera que una regresión linear simple, eliminando así su capacidad de aprender patrones complejos en los datos sin importar la cantidad de capas o de neuronas que se utilicen. Dentro de las arquitecturas modernas de redes neuronales, la función de activación más utilizada es la ReLU (abreviatura del inglés Rectified Linear Unit).

**Función ReLU**

Esta función se define tal que:

$$f(x)\ =\ max(0,\ x)$$

De manera que para cualquier valor de entrada negativo el resultado es 0, en caso contrario el resultado es el mismo valor de la entrada. Esta operación es suficiente para romper la linealidad de la suma ponderada sin cálculos complejos. Es este comportamiento el que permite entender el principal fundamento detrás de las redes neuronales: el Teorema de Aproximación Universal.

**Teorema de Aproximación Universal**

Establece que una red neuronal con 1 o más capas ocultas y una función de activación no lineal es capaz de aproximar cualquier función continua con cierto grado de precisión siempre que el número de neuronas sea suficiente. Puede verse de manera geométrica, a cada neurona con función de activación ReLU como un segmento de recta capaz de aproximarse a una sección específica de la función real del conjunto de datos, por lo tanto, cuando el número de neuronas aumenta, también lo hacen los segmentos de recta, generando así una aproximación linear por tramos precisa de la distribución de los datos reales.

**Función Softmax**

A diferencia de la función ReLU, que se utiliza en las capas ocultas para introducir no linealidad, la función Softmax es utilizada en la capa de salida de las redes neuronales diseñadas para problemas de clasificación.

Su propósito fundamental es tomar un vector de números reales arbitrarios generados por la última capa lineal de la red y transformarlos en una distribución de probabilidad. Dado un vector de entrada $z$ cuya dimensión $K$ (donde $K$ representa el número total de clases, la función Softmax calcula el valor para la clase $i$ mediante la siguiente ecuación:

$$Softmax{\left({z}\right)}_{i}=\frac{{e}^{{z}_{i}}}{\sum\limits_{j=1}^{K}{e}^{{z}_{j}}}$$

Al elevar el número base $e$ a la potencia de cada componente, se garantiza que todos los valores resultantes sean estrictamente positivos. Además, dada la naturaleza de la función exponencial, si una componente es ligeramente mayor que los demás resultará en un valor exponencial significativamente más grande, de esa forma la red tiende a destacar su predicción principal. 

Finalmente, al dividir cada valor exponencial por la suma de todos los valores exponenciales del vector, cada componente del vector resultante de salida estará dentro del el rango (0, 1\) y la sumatoria total de todas las componentes será exactamente igual a 1\. De este modo, la salida de la neurona se puede interpretar estadísticamente como la probabilidad de que la entrada pertenezca a una clase específica, cumpliendo con los axiomas de probabilidad.

**Descenso del gradiente**

El gradiente de una función es un vector cuyas componentes son las derivadas parciales respecto a cada una de sus variables, además indica en que dirección crece más rápidamente la función. En nuestro contexto, este vector consta de las derivadas parciales de la función de pérdida respecto a cada parámetro del modelo, es así como se define el descenso del gradiente como un algoritmo que actualiza los parámetros moviéndose deliberadamente en la dirección opuesta al gradiente. Visto de manera matemática, sea la función de pérdida $L$, sea θ un parámetro del modelo, se actualizará su valor luego de cada iteración del algoritmo siguiendo la regla:

$${\theta }_{t+1}\ \leftarrow \ {\theta }_{t}\ -\ α\frac{∂L}{\partial {\theta }_{t\ }}$$

Siendo el escalar α la tasa de aprendizaje, este determina la longitud o intensidad del ajuste del modelo en cada iteración, es gracias a este parámetro que el modelo es capaz de converger durante el entrenamiento sin un tiempo excesivo de cómputo. En arquitecturas actuales, que poseen millones o miles de millones de parámetros, calcular el gradiente para cada uno de ellos resulta inviable, para solucionarlo se utiliza el algoritmo conocido como Retropropagación (en inglés Backpropagation).

**Algoritmo de Backpropagation**

Este algoritmo aplica de manera eficiente la regla de la cadena del cálculo diferencial, dividiendo el proceso de aprendizaje de la red neuronal en dos fases:

* Propagación hacia adelante (Forward Pass): Se procesan los datos de entrada capa por capa, calculando las sumas ponderadas, aplicando las funciones de activación hasta generar una predicción final con la que luego se evalúa la función de pérdida.  
* Propagación hacia atrás (Backward Pass): El error calculado se propaga de regreso a las capas iniciales usando la regla de la cadena con el fin de calcular cuánto contribuyó cada parámetro individual del modelo al resultado obtenido.

	El objetivo principal es conocer qué tanto cambiará el resultado obtenido por la función de pérdida si modificamos el valor del peso ${w}_{i}$, de manera matemática esto se entiende como la derivada parcial de la función de pérdida con respecto a ${w}_{i}$ ($\frac{∂L}{\partial {w}_{i}}$). Sin embargo, el error obtenido no depende explícitamente de ${w}_{i}$ sino que viene dado por las operaciones realizadas en cada neurona:

* Suma ponderada: Se multiplica el peso por el dato de entrada para luego sumarle el sesgo, este resultado se puede expresar como:

$$z\ =\ w⋅x\ +\ b$$

* Función de activación: El resultado obtenido pasa por la respectiva función de activación, obteniendo así la salida del modelo:

$$y\ =\ f(z)$$

* Pérdida: Se hace uso de la función de activación para calcular que tan alejado está el resultado obtenido (*y*) de la realidad ($\hat{y}$):

$$L(y,\ \hat{y})$$

Es por esta dependencia que se utiliza la regla de la cadena, ya que la misma establece que la derivada parcial de la pérdida con respecto al peso se obtiene del producto entre las derivadas parciales de los pasos intermedios: 

$$\frac{∂L}{∂w}\ =\ \frac{∂L}{∂y}\cdot \frac{∂y}{∂z}\cdot \frac{∂z}{∂w}$$

El algoritmo de retropropagación busca calcular estas derivadas desde la capa de salida hacia la capa de entrada con el fin de reutilizar valores en capas anteriores, de esta forma se evita tener que calcular las derivadas desde cero para cada una de las neuronas de la red reduciendo considerablemente la complejidad del problema, es gracias a esto que las técnicas de aprendizaje modernas en campos como el aprendizaje profundo sean viables.

El descenso del gradiente tradicional presenta dos inconvenientes principales al trabajar con funciones muy complejas, el aprendizaje puede estancarse en mínimos locales o puntos de silla presentes en la función de pérdida, por esta razón existen variantes que buscan dar soluciones mediante técnicas estadísticas.

**Descenso del gradiente por lotes**

Se utiliza todo el conjunto de datos de entrenamiento para calcular el gradiente, este método garantiza encontrar el mínimo global de la función de pérdida si se inicializan los pesos con los valores correctos, en la práctica, los conjuntos de datos reales se ven representados por superficies muy complejas, por lo tanto, se utilizan algunas de las alternativas siguientes.

**Descenso del gradiente estocástico (SGD \-  Stochastic Gradient Descent)**

En esta vertiente, el gradiente se calcula sólo para un par aleatorio de los datos de entrenamiento elegido de manera aleatoria, de esa forma se introduce ruido al gradiente. Se conoce como época a la cantidad de iteraciones en las que el algoritmo ha utilizado todo el conjunto de datos de entrenamiento. El fundamento matemático detrás de este enfoque es el siguiente:

$${\theta }_{t+1}\ ←\ {\theta }_{t}\ -\ α⋅\ \sum\limits_{i∈Β}^{}\frac{\partial {l}_{i}[{\theta }_{t}]}{∂θ}$$

Siendo $Β$ el conjunto de índices para los pares de datos de entrada y salida actuales, ${l}_{i}$ representa la pérdida con respecto al parámetro $\theta$ y el escalar *α* es la tasa de aprendizaje que mencionamos anteriormente.

Dentro de las ventajas de este enfoque se destaca su reducción en cuanto a costo computacional, ya que se calculan los gradientes para conjuntos de datos de menor tamaño, el hecho de que las muestras se tomen de forma aleatoria introduce ruido al algoritmo, esto hace que su comportamiento no sea tan suave como el descenso del gradiente tradicional, sin embargo, se garantiza que cada iteración contribuya a disminuir la pérdida. 

Dado que las muestras se toman sin reemplazo del conjunto de datos de entrenamiento, cada uno de ellos contribuye de forma equitativa al aprendizaje del modelo. Este enfoque tiene un mejor comportamiento al optimizar funciones de pérdida complejas, ya que tiene la capacidad de “escapar” de mínimos locales dentro de la función, además es menos propenso a estancarse en los llamados puntos de silla (puntos en la función en el que el gradiente tiene valor 0). Dado a que el valor de *α* es fijo, el descenso del gradiente estocástico es incapaz de converger por lo que se suele incluir una rutina en las implementaciones que reduzca el valor de la tasa de aprendizaje a medida que aumenta el número de épocas.

**Descenso del gradiente por mini-lotes**

Este enfoque parte del descenso del gradiente estocástico, sin embargo, no itera sobre una sola muestra, en su lugar toma el conjunto de datos de entrenamiento y lo divide en subconjuntos de tamaño fijo, la principal ventaja es que el tamaño del lote se elige teniendo en cuenta la capacidad del hardware que poseen actualmente las GPUs (Unidades de procesamiento gráfico) para procesar datos de forma paralela. 

**Momentum**

Se introduce un término extra a la fórmula que representa una suma ponderada de los gradientes anteriores, este ajuste se refleja de la siguiente manera:

$${m}_{t+1}\ ←\ β⋅\ {m}_{t\ }\ +\ (1\ -\ β)\ ⋅\ \sum\limits_{i∈Β}^{}\frac{\partial {l}_{i}[{\theta }_{t}]}{∂θ}$$

$${\theta }_{t+1}\ ←\ {\theta }_{t\ }\ -\ α⋅\ {m}_{t+1}{\ }$$

Siendo ${m}_{t}$ el momento (o momentum) del algoritmo calculado de manera recursiva, este término busca almacenar información de gradientes pasados para aplicarse al actualizar el actual, el término *β* se conoce como coeficiente de momento. Esto implica que el gradiente final es una suma ponderada de todos los gradientes anteriores, si los mismos están alineados en el tiempo (es decir, corresponden al mismo mínimo dentro de la función de pérdida) la tasa de aprendizaje va disminuyendo al aumentar el tiempo, por el contrario, si el algoritmo se comporta de manera irregular al momento de calcular los gradientes la tasa de aprendizaje aumenta.

**Adam**

Este algoritmo fue presentado en el año 2014, en el artículo: *"Adam: A Method for Stochastic Optimization”* por Diederik P. Kingma y Jimmy Ba [8], es el estándar actual para el entrenamiento de modelos complejos. La principal limitante de los algoritmos anteriores es que aplican una valor estático y global para la tasa de aprendizaje *α* para actualizar los parámetros de la red, este enfoque aplica la lógica del Momentum junto a técnicas de escalado de gradientes para calcular tasas de aprendizaje adaptativas asociadas a cada peso sináptico.

Para ello, el algoritmo mantiene 2 momentos estadísticos de los gradientes ya calculados:

$${m}_{t+1}\ ←\ β⋅\ {m}_{t}\ +\ (1\ -\ β)\ ⋅\ \sum\limits_{i∈Β}^{}\frac{\partial {l}_{i}[{\theta }_{t}]}{∂θ}$$

$${v}_{t+1}\ =\ γ⋅\ {v}_{t}\ +\ (1\ -\ γ)\ ⋅\ {\sum\limits_{i∈Β}^{}\frac{\partial {l}_{i}[{\theta }_{t}]}{∂θ}}^{2}$$

Siendo *β* y *γ* ambos coeficientes de momento para los vectores ${m}_{t}$ y ${v}_{t}$. Dado que emplear el momento consta de una suma ponderada de los gradientes anteriores, en la primera iteración este valor inicia en 0 y va aumentando muy lentamente, esto da como resultado un comportamiento errático del algoritmo en las etapas iniciales, para mitigar esto, se realiza el siguiente ajuste:

$${\tilde{m}}_{t+1}\ ←\ \frac{{m}_{t+1}}{1\ -\ {\beta }^{t+1}}$$

$${\tilde{v}}_{t+1}\ ←\ \frac{{v}_{t+1}}{1\ -\ {\gamma }^{t+1}}$$

A medida que el número de iteraciones aumenta, el denominador acerca su valor a 1 por lo que el ajuste desaparece y se mantiene la lógica original. Finalmente, la regla de actualización de parámetros es la siguiente:

$${\theta }_{t+1}\ ←\ {\theta }_{t\ }\ -\ α⋅\ \frac{{\tilde{m}}_{t+1}}{\sqrt{{\tilde{v}}_{t+1}}\ +\ ε}$$

**Aprendizaje profundo**

Dado el aumento de la complejidad de los problemas computacionales, especialmente en áreas donde los datos no son estructurados, como la visión artificial y el procesamiento de lenguaje natural, las redes neuronales demostraron limitaciones claras. Es por ello, por el enorme aumento en capacidad de cómputo en los últimos años y finalmente por la disponibilidad de grandes cantidades de datos que surge dentro del Aprendizaje Automático lo que hoy día se conoce como Aprendizaje Profundo [6]. Esta área se caracteriza por el entrenamiento y uso de redes neuronales que poseen múltiples capas ocultas.

A diferencia del Aprendizaje Automático, la red neuronal procesa los datos crudos, como los valores RGB de los píxeles de una imagen o los vectores de palabras en un texto y descubre por sí misma qué características y relaciones son relevantes que minimicen la función de pérdida. Para conseguir esta capacidad, se emplea una arquitectura de aprendizaje jerárquico, a medida que la información fluye a través de las sucesivas capas ocultas de la red, los datos sufren transformaciones no lineales cada vez más abstractas:

* **Capas iniciales:** Tienen la función de detectar características matemáticas de bajo nivel.  
* **Capas intermedias:** Combinan las características halladas en las capas iniciales para formas representaciones más complejas.  
* **Capas finales:** Abstraen el conocimiento al más alto nivel, igualando las representaciones al contexto del usuario.

Esta capacidad del Aprendizaje Profundo para extraer y modelar jerarquías complejas a partir de datos no estructurados dió pie a lo que se conoce como Inteligencia Artificial Generativa y, posteriormente, para la evolución hacia arquitecturas especializadas en secuencias, como los Transformers.

**Modelos Generativos**

Gran parte de los avances tempranos en el Aprendizaje Profundo se centraron en modelos discriminativos cuyo objetivo principal es encontrar el límite de decisión que separa diferentes clases de datos, por ejemplo, clasificar si una imagen corresponde a un perro o a un gato. Estadísticamente, estos modelos aprenden la distribución de probabilidad condicional $P(Y|X)$, que estima la probabilidad de que un valor observado *X* pertenezca a una clase *Y* [10].

Por otro lado, dentro del aprendizaje no supervisado se busca estudiar y desarrollar modelos capaces de generar nuevos datos con características estadísticamente similares a los datos usados durante el entrenamiento, este tipo de modelos se conocen como modelos generativos. En lugar de centrarse en lo que diferencia a una clase de otra, los modelos generativos buscan comprender y modelar la distribución de probabilidad presente en el conjunto de datos completo.

Una característica de las redes neuronales profundas es que buscan mapear información de alta dimensionalidad hacia representaciones matemáticas más compactas, conocidas como el espacio latente. Este espacio codifica de manera comprimida las características fundamentales, la semántica y las variaciones estructurales de los datos de entrenamiento. Para la generación de nuevos puntos de datos se realiza un proceso de muestreo estadístico en el que el algoritmo selecciona un punto o vector del espacio latente y lo decodifica, generando instancias de datos nuevas pero que pertenecen a la misma distribución de probabilidad de los datos originales. 

**Aprendizaje Auto-supervisado**

Para modelar representaciones complejas como el lenguaje humano, los modelos generativos dependen fuertemente del aprendizaje auto-supervisado que, a diferencia del aprendizaje supervisado clásico, genera sus propias etiquetas partiendo de la estructura de los datos de entrada. Un comportamiento presente en estos modelos que procesan secuencias de datos relacionados entre sí es que el algoritmo oculta una parte de la información para forzar a la red neuronal a predecir la porción faltante basándose exclusivamente en el contexto restante.

El error matemático entre la predicción del modelo y el dato original realimenta el algoritmo de retropropagación para ajustar los pesos, de esta forma los modelos generativos pueden escalar de forma masiva.

**Modelos Transformers y fundamentos**

Originalmente, el modelo más utilizado en tareas de procesamiento de secuencias (como el Procesamiento de Lenguaje Natural) eran las Redes Neuronales Recurrentes (RNN) y sus variantes, como las redes de Memoria a Corto y Largo Plazo (LSTM) [7]. Estas arquitecturas procesaban la información de manera secuencial, es decir, para procesar el token en la posición $t$, era necesario haber calculado previamente el estado oculto de token en la posición $t-1$, lo que presenta dos problemas fundamentales: no es posible realizar el cómputo en paralelo y provoca la pérdida de información en dependencias a largo plazo debido al desvanecimiento del gradiente.

En el año 2017, se publica el artículo *"Attention Is All You Need"* por investigadores de Google [17], en el que se introduce la arquitectura Transformer. La característica principal de esta arquitectura es que prescinde totalmente de la recurrencia y la convolución, basándose de manera exclusiva en un mecanismo denominado autoatención, lo cual permite procesar todos los elementos de una secuencia de manera simultánea.

**El Mecanismo de Autoatención**

El mecanismo de autoatención permite a un modelo evaluar, durante el procesamiento de un *token* específico, la importancia y relación semántica que tienen todos los demás *tokens* de la secuencia de entrada respecto a él, sin importar la distancia física que los separe [1].

Para lograr esto computacionalmente, el modelo toma el vector numérico que representa a cada token (conocido como embedding) y lo proyecta geométricamente en tres subespacios distintos multiplicándolo por tres matrices de pesos diferentes (${W}^{Q},{W}^{K},{W}^{V}$), las cuales se ajustan dinámicamente durante el entrenamiento. Estas multiplicaciones generan tres nuevos vectores para cada token:

* **Vector Query ($Q$ \- Consulta):** Representa lo que el *token* actual está buscando en el resto de la secuencia para comprender su propio contexto.

* **Vector Key ($K$ \- Clave):** Representa el contenido del token, cumple la función de etiqueta de identificación o índice.

* **Vector Value ($V$ \- Valor):** Representa el contenido semántico o la representación real del token que será propagada hacia las siguientes capas de ser relevante.

Esta terminología viene dada de las bases de datos, donde se realiza una consulta (*Query*) y se compara contra las claves (*Keys*) almacenadas para extraer los valores (*Values*) asociados.

Para calcular qué tanta "atención" debe prestarle un token al resto, la arquitectura Transformer utiliza la Atención de Producto Punto Escalado (*Scaled Dot-Product Attention*), el cual es un proceso matemático definido tal que:

* Se calcula el producto punto entre la matriz de consultas $Q$ y la matriz transpuesta de claves ${K}^{T}$. Dado que el producto punto es una medida de similitud geométrica; si dos vectores apuntan en la misma dirección, el resultado es alto, lo que indica una fuerte relación semántica entre ambos tokens.

* Este resultado se divide entre la raíz cuadrada de la dimensión de los vectores clave $\sqrt{{D}_{k}}$. Este proceso busca evitar que los resultados crezcan excesivamente, lo cual empujaría a la función *softmax* hacia regiones con gradientes muy pequeños, ralentizando el aprendizaje.

* Se aplica la función *softmax* a lo largo de las filas para normalizar los puntajes, convirtiéndolos en una distribución de probabilidad.

* Finalmente, los pesos probabilísticos se multiplican por la matriz de valores $V$. Si una palabra no es relevante para el contexto actual, su peso será cercano a cero.

Matemáticamente, este mecanismo se condensa en la ecuación central del Transformer:

$$Sa\left({X}\right)=V⋅softmax\left({\frac{{K}^{T}Q}{\sqrt{{D}_{k}}}}\right)$$

Aplicar solo un mecanismo de atención presenta un problema: al calcular un único conjunto de pesos mediante la función softmax, el modelo se ve forzado a promediar diferentes tipos de relaciones (sintácticas, semánticas, estructurales), causando que información de contextos complejos se pierda. Como solución se introduce la Atención Multicabezal.

**Atención Multicabezal y Codificación Posicional**

En lugar de aplicar la función de atención una sola vez sobre los vectores originales de alta dimensionalidad, la arquitectura proyecta linealmente las Consultas $Q$, Claves $K$ y Valores $V$ en una cantidad finita de subespacios de representación independientes.

Sobre cada uno de estos subespacios, el modelo calcula la Atención, dándole al algoritmo la libertad de especializarse en abstraer diferentes dependencias. Habiendo generado sus respectivas matrices de atención, los vectores de dimensión resultantes se concatenan secuencialmente restaurando la matriz original. Finalmente, esta se multiplica por una matriz de pesos de salida, encargada de integrar las características descubiertas por los diferentes subespacios antes de propagar el resultado hacia la siguiente capa de la red neuronal.

Por otro lado, dado que el procesamiento de los Transformers se realiza de forma paralela, el modelo desconoce el orden secuencial de los tokens procesados. La solución consiste en añadir una Codificación Posicional antes de aplicar el mecanismo de atención. Se suma un vector con funciones matemáticas deterministas (senos y cosenos de distintas frecuencias) al *embedding* original de la entrada, otorgándole a cada *token* una marca única dentro de la secuencia.

**Grandes Modelos de Lenguaje**

Los Grandes Modelos de Lenguaje (siglas en inglés LLMs provenientes de Large Language Models) representan la evolución y escalamiento masivo de la arquitectura Transformer. A diferencia del modelo original, que se especializaba en la traducción de idiomas gracias a su estructura Codificador-Decodificador (*Encoder-Decoder*), los LLMs generativos modernos se construyen casi exclusivamente utilizando una arquitectura de solo decodificado [12].

Al eliminar el Codificador, el modelo centra exclusivamente en una tarea auto-supervisada: el modelado de lenguaje iterativo.

**Generación Autorregresiva y Atención Causal**

El núcleo operativo de un LLM consiste en la predicción del siguiente elemento en una secuencia. Para lograr la generación de texto coherente, los LLMs implementan una variante crítica en su arquitectura denominada Autoatención Enmascarada (*Masked Self-Attention*). Durante el entrenamiento, el modelo recibe secuencias completas de texto, por lo que, para obligarlo a predecir el token $t+1$ en lugar de simplemente fijarse en la respuesta, se aplica el mecanismo de atención causal, el cual aplica una máscara matemática sobre la matriz de atención antes de aplicar la función *softmax*.

Este mecanismo garantiza que, para procesar y predecir el *token* en la posición $t+1$, el modelo solo pueda calcular los pesos de atención sobre los *tokens* anteriores, bloqueando cualquier flujo de información proveniente de los *tokens* futuros. Matemáticamente, el modelo aprende y aproxima la siguiente distribución de probabilidad condicional:

$$P\left({{x}_{t+1}|{x}_{1},{x}_{2},…,{x}_{t}}\right)$$

Habiendo finalizado el entrenamiento, la tarea de generación de texto se vuelve un autorregresiva, ya que, cuando el LLM predice el siguiente *token*, este se concatena a la secuencia de entrada original, y todo el contexto actualizado vuelve a pasar por la red neuronal para predecir el subsiguiente elemento.

Durante su ciclo de vida, un LLM moderno pasa por el proceso de preentrenamiento en el cual el modelo procesa cuerpos de texto de gran tamaño extraídos de internet. Mediante algoritmos como Adam, se ajustan los miles de millones de parámetros para minimizar la pérdida de entropía cruzada en la predicción de *tokens*. Es así como el modelo extrae representaciones latentes profundas, internalizando la gramática, la lógica básica y un vasto conocimiento general del mundo.

**Modelos de Código Abierto y Ejecución Local**

En el contexto de los LLMs, suele confundirse el término “open-source” con “open-weights”, ya que en lugar de compartir el código fuente de la arquitectura del modelo, se liberan los pesos paramétricos resultantes del entrenamiento, de esta manera se facilita el acceso a LLMs altamente capaces, entre los cuales destacan familias de modelos como Llama de Meta o Phi de Microsoft [16].

Estos modelos abiertos permiten el despliegue y la ejecución local de la inferencia en hardware privado. La principal ventaja de esto consiste en eliminar la dependencia de APIs de terceros, además de otorgar al usuario control sobre latencias y, primordialmente, asegura la privacidad absoluta y la confidencialidad de los datos analizadas por el sistema.

**Ventana de contexto e inferencia local**

La cantidad de información que un LLM puede observar, recordar y procesar simultáneamente en una sola iteración de inferencia está estrictamente limitada por un parámetro arquitectónico conocido como Ventana de Contexto.

Esta se mide en tokens y dicta la capacidad de memoria a corto plazo del modelo, si alguna información queda fuera de esta ventana entonces no existe para el algoritmo en el momento de generar una respuesta. A medida que un modelo analiza un conjunto de documentos, surge la necesidad de incrementar la ventana de contexto. Sin embargo, procesar un gran número de tokens simultáneamente representa un aumento de complejidad cuadrática dada la naturaleza del mecanismo de autoatención.

Como se explicó en la sección referente a la arquitectura Transformer, el cálculo de atención requiere realizar el producto punto entre la matriz de Consultas y la matriz de Claves. Si una secuencia tiene una longitud de $N$ tokens, la matriz de pesos de atención tiene un tamaño de $N\times N$, causando que tanto el número de operaciones de punto flotante como el consumo de memoria crezcan de forma proporcional a $O\left({{N}^{2}}\right)$.

Esto es especialmente importante cuando se trata con modelos ejecutados de forma local en los que el hardware está restringido por la memoria de las GPUs disponibles. Intentar cargar miles de tokens en la ventana de contexto para analizar múltiples documentos agota rápidamente los recursos del sistema, provocando errores de desbordamiento de memoria o degradando el rendimiento de la inferencia.

Incluso si el hardware dispone de la capacidad para procesar ventanas de contexto amplias, los LLMs sufren de una degradación en su capacidad de recuperación de información conocida como el fenómeno "Perdido en el medio".

Recientes investigaciones sobre el comportamiento de atención en los LLMs han demostrado que los modelos exhiben un rendimiento sobresaliente al recuperar y razonar sobre información que se encuentra al principio de la secuencia o al final de esta [19]. Sin embargo, este rendimiento disminuye cuando el modelo intenta extraer hechos estructurados cuando la información relevante está sepultada en el medio de un texto extenso.

En el contexto de esta investigación, este comportamiento representa una barrera para la extracción de entidades y el llenado de esquemas a partir de documentos no estructurados. Introducir la información completa de un área sin importar la fuente, ya sea un libro, un manual técnico o una transcripción de audio en la ventana de contexto es computacionalmente costoso para entornos locales, además de que reduce la fiabilidad y precisión de los datos extraídos.

Para superar estas complicaciones, es necesario implementar arquitecturas que permitan filtrar y obtener el contexto necesario para generar una respuesta en lugar de intentar inyectar todo el contexto en cada petición al modelo. Este es el fundamento que motiva la adopción de arquitecturas de Generación Aumentada por Recuperación (RAG) y la Representación Estructurada del Conocimiento.

**Bases de Datos Relacionales y Bases de Datos Vectoriales**

Para comprender como el modelo recupera la información, debemos establecer la diferencia entre el almacenamiento de datos clásico y vectorial.

Una Base de Datos relacional almacena la información de manera tabular, estructurada en filas y columnas. Para recuperar datos en estos sistemas se utilizan búsquedas de coincidencia exacta. Esto quiere decir que, si se busca el término "automóvil", la base de datos relacional solo devolverá registros que contengan exactamente esa secuencia, ignorando por completo sinónimos o contextos semánticos.

Por otro lado, una Base de Datos Vectorial es un sistema de almacenamiento diseñado para manejar datos de alta dimensionalidad. En lugar de guardar tablas de texto plano, se almacenan arreglos continuos conocidos como Embeddings. A diferencia de las bases de datos tradicionales, estas permiten realizar búsquedas semánticas, en el que no se buscan términos exactos, sino que se buscan vectores en el espacio multidimensional, permitiendo comprender que términos como "automóvil" y "vehículo" apuntan al mismo concepto lógico.

**Mecanismos de generación aumentada por recuperación (RAG)**

El estándar actual para darle conocimiento externo, dinámico y verificable a un LLM es el proceso conocido como Generación Aumentada por Recuperación (RAG, por sus siglas en inglés: Retrieval-Augmented Generation).

El paradigma RAG fue introducido formalmente por Lewis et al. [9], el mismo no busca que el modelo memorice toda una base de conocimiento durante su preentrenamiento y así reflejarlo en sus pesos, ni intenta inyectar documentos completos en una única ventana de contexto dentro de cada petición. En su lugar, acopla el LLM con una base de datos vectorial para la recuperación de información.

El objetivo es recuperar únicamente los fragmentos de información relevantes para la consulta actual del usuario, y proveerlos al modelo como contexto temporal. Este proceso modular se divide tres fases:

* **Indexación y Representación Vectorial:** Antes de que el modelo pueda interactuar con el conocimiento externo, la información debe ser estructurada. Los documentos originales se dividen en fragmentos de texto más pequeños y manejables (conocidos en inglés como chunks), que luego se pasan a un modelo de incrustación (Embedding Model) que los transforma en un vector numérico denso de alta dimensionalidad que encapsula el significado semántico del texto. Finalmente, estos se almacenan en una base de datos vectorial.  
* **Recuperación:** Cuando el sistema recibe una consulta de entrada, esta se transforma utilizando el mismo modelo de embedding, generando un "vector de consulta". El sistema de recuperación calcula entonces la similitud geométrica entre el vector de consulta y todos los vectores almacenados en la base de datos. El algoritmo extrae y devuelve los fragmentos que tengan la mayor cercanía, lo que se traduce en la información semánticamente más relevante para resolver la tarea.  
* **Generación Aumentada:** Finalmente, los fragmentos de texto recuperados se concatenan estructuradamente junto con la petición original del usuario. Esta nueva petición se inyecta en la ventana de contexto del LLM que, al contar con la información precisa, filtrada y altamente relevante, utiliza su mecanismo de autoatención para analizar el contexto provisto y generar una respuesta fundamentada. Este proceso reduce la probabilidad de generar alucinaciones.

**Agentes**

El concepto de Agente en la Inteligencia Artificial moderna transforma al LLM de un simple generador de texto en un motor de razonamiento capaz de interactuar con su entorno. Un agente impulsado por un LLM se define formalmente como un sistema autónomo que utiliza el modelo de lenguaje como su unidad de control central para percibir el contexto, planificar una secuencia de acciones, ejecutar herramientas externas y evaluar los resultados para alcanzar un objetivo [18].

Desde el punto de vista de arquitectura, un agente está compuesto de tres pilares:

* Planificación y Razonamiento: Se entiende como la capacidad de descomponer una tarea compleja en subtareas más pequeñas. Para conseguirlo se implementan técnicas de razonamiento explícito como Chain-of-Thought [20] o ReAct [21], donde el modelo genera verbalmente sus pensamientos antes de tomar una decisión.

* Memoria: Está divido en memoria a corto plazo, que corresponde al contexto de la conversación actual manejado por la ventana de contexto y memoria a largo plazo, almacenamiento y recuperación de información histórica, generalmente implementado mediante bases de datos vectoriales.

* Uso de Herramientas (Tool-use o Function Calling): Es la característica que separa a un agente de un LLM tradicional, el modelo es entrenado para comprender firmas de funciones como APIs, intérpretes de código, motores de búsqueda. Cuando el modelo determina que carece de la información necesaria para responder, detiene la generación de texto, emite un comando estructurado para invocar una herramienta externa, espera el resultado de dicha ejecución y luego integra esa nueva información en su razonamiento.

**RAG Agéntico**

Si bien el proceso de Generación Aumentada por Recuperación es efectivo para mitigar alucinaciones y superar el límite de contexto, presenta una limitación estructural: es un proceso lineal y determinista que consta de recuperar, inyectar y generar. En el Naive RAG, el sistema siempre realiza una búsqueda vectorial en la base de datos, independientemente de si la consulta del usuario lo requiere, y el LLM está forzado a responder basándose en los fragmentos recuperados, incluso si estos resultan irrelevantes o insuficientes.

Se propone como mejora lo que se conoce como el RAG Agéntico. Esta arquitectura fusiona las capacidades de razonamiento y uso de herramientas de un agente autónomo con el sistema de recuperación de información.

En lugar de ejecutar una búsqueda vectorial de manera obligatoria y secuencial, el sistema provee al LLM de la base de datos vectorial como si fuera una herramienta a su disposición. El flujo operativo se convierte en:

* Evaluación de necesidad: Al recibir una consulta, el agente evalúa si puede responder con su conocimiento interno o si requiere información externa. Si decide que necesita contexto, formula una consulta optimizada específicamente a la base de datos.

* Evaluación de relevancia: Una vez que la base de datos devuelve los fragmentos de información, el agente actúa como un filtro, ya que, lee los fragmentos y determina si realmente contienen la respuesta a la pregunta.

* Iteración: Si el agente determina que la información recuperada es insuficiente o tangencial, es capaz de decidir de forma autónoma reformular su consulta de búsqueda y ejecutar la herramienta nuevamente, iterando este proceso hasta recopilar el contexto necesario o alcanzar un límite de intentos.

* Síntesis: Solo cuando el agente está satisfecho con la relevancia del contexto recuperado, procede a sintetizar la respuesta estructurada final.

Este comportamiento iterativo e introspectivo permite a las arquitecturas de RAG Agéntico resolver consultas complejas que requieren saltos lógicos o agregación de información dispersa en múltiples documentos [5]. Al proporcionarle al modelo la capacidad de evaluar la calidad de su propio contexto, se incrementa dramáticamente la precisión y la robustez de la extracción de información estructurada.

**Sistemas Multiagente y Orquestación**

Un sistema multiagente es una arquitectura en la que múltiples agentes autónomos colaboran, coordinándose mediante mensajes estructurados o un estado compartido, para alcanzar un objetivo colectivo que un único agente ejecutaría de manera menos eficiente. Cuando estos agentes están impulsados por LLMs, cada uno posee su propio conjunto de instrucciones, herramientas y parámetros de ejecución, de modo que la complejidad de una tarea global se distribuye entre especialistas más pequeños y gobernables [22] [23].

La literatura reconoce varios patrones de orquestación, entre los que destacan:

* **Patrón en cadena (pipeline secuencial):** la salida de un agente se convierte en la entrada del siguiente. Es el patrón natural cuando la tarea posee etapas bien definidas y ordenadas.

* **Patrón orquestador-trabajador (*supervisor*):** un agente coordinador recibe la petición, la descompone y delega subtareas en agentes especializados, integrando después sus resultados. Permite ramificar el flujo y reintentar etapas de forma selectiva.

* **Patrón de colaboración paralela:** varios agentes procesan la misma información de manera simultánea y un paso final sintetiza o contrasta sus salidas, útil para obtener múltiples interpretaciones de un mismo documento.

* **Estado compartido o tablero negro (*blackboard*):** todos los agentes leen y escriben sobre un almacén común de artefactos intermedios, lo que desacopla las etapas y deja un rastro auditable de todo el proceso.

La descomposición de una tarea compleja en agentes especializados responde a razones prácticas verificables:

* **Aislamiento de contexto:** cada agente solo recibe los insumos propios de su etapa, de manera que la ventana de contexto se destina íntegramente a la tarea en curso y no se degrada por acumulación de información ajena [19].

* **Especialización:** cada etapa admite instrucciones, ejemplos, herramientas e incluso modelos distintos, sin que las restricciones de una etapa contaminen a las demás.

* **Contención de fallos:** la validación ocurre entre etapas, por lo que un error se detecta y corrige localmente, reintentando únicamente la etapa afectada en lugar de reejecutar todo el proceso.

* **Control de costos y latencia:** el modelo más capaz y costoso se reserva para las etapas que lo requieren, mientras las tareas simples se ejecutan con modelos pequeños y rápidos.

* **Trazabilidad:** los artefactos intermedios de cada etapa quedan materializados, lo que permite auditar y reproducir cada transición del proceso.

La coordinación entre agentes exige un lenguaje común para intercambiar información, ya que las cadenas de texto libres no garantizan que un agente interprete correctamente la salida del anterior. Este problema se resuelve mediante salidas estructuradas.

**Salidas Estructuradas y Generación Restringida por Esquema (JSON)**

Un LLM es, en esencia, un generador de texto probabilístico: su salida no está garantizada a ser sintácticamente válida ni a poseer la forma que espera el siguiente eslabón de la cadena. En un pipeline automatizado, la extracción de entidades, la definición de la ontología, la respuesta a una consulta y el modelo dimensional deben viajar entre componentes con un formato determinista e interoperable.

El formato JSON se establece como el vehículo de intercambio por su naturaleza de texto plano, su adopción universal y su capacidad de representar estructuras anidadas. Sobre él, el JSON Schema permite definir de manera formal el contrato de datos de cada etapa: campos obligatorios, tipos, enumeraciones y restricciones [24]. Estos esquemas se implementan en lenguajes con verificación de tipos, como Pydantic, que fallan de forma explícita cuando la salida del modelo no cumple la estructura esperada [25].

La obtención de salidas válidas se persigue por tres vías complementarias:

* **Diseño de instrucciones:** se describe el esquema deseado y se proporcionan ejemplos de salida correcta dentro de la petición, aprovechando la capacidad de aprendizaje en contexto de los LLMs [2].

* **Llamada a funciones y modo de salida estructurada:** las APIs modernas permiten declarar un esquema y reservar espacio en la respuesta para que el modelo genere únicamente los campos requeridos.

* **Decodificación restringida:** en lugar de filtrar después, se restringe la distribución de probabilidad durante la generación a los tokens compatibles con una gramática o máquina de estados, garantizando validez sintáctica desde el primer token [26].

Una vez generada, la salida se valida automáticamente contra el esquema; si la validación falla, los mensajes de error se reintroducen en el modelo como retroalimentación para un nuevo intento, limitado por un número máximo de reintentos. Este ciclo de validación y corrección transforma la generación probabilística en un contrato confiable, condición indispensable para que los componentes de un sistema multiagente se comuniquen y para que la información final pueda persistirse en bases de datos relacionales o de grafos sin intervención humana.

**Representación de Conocimiento**

Para que la información recuperada e interpretada por un modelo autónomo posea utilidad computacional, no es suficiente generar respuestas en lenguaje natural. Cuando se realizan soluciones orientadas a la automatización de procesos, al llenado de bases de datos, generación de código o interconexión con otros sistemas, se deben estructurar los resultados bajo un formato determinista e interoperable.

La Representación del Conocimiento es una rama de la Inteligencia Artificial tradicional cuyo objetivo es diseñar formalismos que permitan a un sistema informático almacenar, procesar y razonar sobre información del mundo real [3]. A diferencia de las representaciones latentes y distribuidas que emplea una red neuronal, que son inescrutables para los sistemas informáticos convencionales, la representación del conocimiento exige que la información sea explícita, simbólica y estructurada [13].

**Ontologías Computacionales**

El estándar más riguroso para la estructuración de conocimiento es la Ontología. En el contexto de las ciencias de la computación, la misma se define como una "especificación explícita y formal de una conceptualización compartida" [15].

De manera práctica, una ontología proporciona un vocabulario controlado y una estructura lógica para un dominio específico, definiendo:

1. **Entidades:** Conceptos fundamentales que existen en un dominio.

2. **Propiedades:** Las características que describen a dichas entidades.

3. **Relaciones:** Las conexiones semánticas y jerárquicas entre las entidades.

4. **Restricciones lógicas:** Reglas de validación que gobiernan los datos.

Al incluir una ontología claramente definida en los ajustes del modelo, se delimita su espacio de razonamiento, de esa forma el agente deja de ser un generador de texto libre y asume el rol de un clasificador y extractor de entidades que debe mapear la información no estructurada para cumplir con las reglas definidas por la ontología.

**Lenguajes y Estándares para la Representación del Conocimiento: RDF, OWL y SPARQL**

La ontología descrita en la sección anterior es una especificación conceptual; para que una máquina pueda almacenarla, consultarla e inferir a partir de ella es necesario materializarla en lenguajes formales. En este campo, los estándares del World Wide Web Consortium (W3C) constituyen el marco de referencia para la Web Semántica y la Web de Datos Enlazados.

El **Resource Description Framework (RDF)** [27] es el modelo de datos fundamental. RDF representa toda la información como tripletas de la forma (sujeto, predicado, objeto), donde el sujeto y el predicado son identificadores internacionalizados de recurso (IRI) y el objeto puede ser otro IRI o un valor literal. El conjunto de tripletas de un dominio se interpreta como un grafo dirigido y etiquetado, lo que permite enlazar recursos entre sí sin necesidad de un esquema centralizado. RDF admite diversas serializaciones, entre las que destacan Turtle y JSON-LD, esta última especialmente indicada para intercambiar datos con sistemas basados en JSON.

Sobre RDF se define el **Resource Description Framework Schema (RDFS)**, que aporta el vocabulario mínimo para construir taxonomías: clases, propiedades, jerarquías de subclase y de subpropiedad, así como las restricciones de dominio y rango de cada propiedad.

El **Web Ontology Language (OWL)** [28] es el lenguaje estándar para escribir ontologías de forma formal. OWL se construye sobre RDF y RDFS y se apoya en lógicas descriptivas, lo que habilita un rol que ninguna base de datos convencional cumple: el razonamiento. Un motor de inferencia puede clasificar clases, detectar inconsistencias lógicas y deducir relaciones implícitas a partir de las explícitas. OWL define perfiles (OWL 2 EL, QL y RL) que restringen la expresividad en favor de la escalabilidad, una distinción relevante al decidir qué tan estricta puede ser la validación automatizada del esquema generado.

El **SPARQL Protocol and RDF Query Language (SPARQL)** [29] es el lenguaje de consulta de grafos RDF. Su sintaxis se basa en el emparejamiento de patrones de tripletas, de modo que una consulta describe la forma del subgrafo que se busca, y el motor resuelve dicho patrón con joins, filtros, uniones y agregaciones sobre el grafo completo. SPARQL es a un grafo de conocimiento lo que SQL es a una base de datos relacional: el puente mediante el cual una pregunta en lenguaje natural puede traducirse a una recuperación formal del conocimiento.

Complementariamente, el **Shapes Constraint Language (SHACL)** [30] permite validar la estructura de un grafo RDF frente a un esquema de formas que declara tipos de nodo, cardinalidades y rangos de propiedad. Mientras OWL valida la coherencia lógica, SHACL valida la forma concreta de los datos, una distinción práctica para comprobar que la salida de un agente cumple efectivamente con la ontología antes de persistirla.

En conjunto, estos estándares delimitan niveles bien definidos: la ontología establece el esquema (el denominado TBox), las instancias conforman los datos (el ABox), OWL aporta el razonamiento, SHACL la validación estructural y SPARQL la consulta, nivel sobre el cual se construyen las arquitecturas GraphRAG.

**Grafos de Conocimiento (*Knowledge Graphs*)**

Desde la perspectiva de las estructuras de datos, un Grafo de Conocimiento es una red semántica que representa topológicamente la información. Matemáticamente, se define como un grafo dirigido $G=\left({V,E}\right)$, en el que un conjunto de vértices $V$ representan a las entidades individuales definidas en la ontología y el conjunto de aristas $E$ representan las relaciones lógicas y semánticas que conectan a dichas entidades [4].

La unidad atómica de información dentro de un grafo de conocimiento se define como tripleta semántica y se define siguiendo la estructura: (Sujeto, Predicado, Objeto).

**Bases de Datos de Grafos**

Representar el conocimiento como un grafo exige un sistema de almacenamiento capaz de persistirlo y consultarlo de forma nativa. Las bases de datos de grafos se clasifican tradicionalmente en dos familias [31]: los almacenes triples, fieles al modelo RDF y orientados a la Web Semántica, y los grafos de propiedades (*property graphs*), que extienden el modelo clásico de grafos para dar soporte a aplicaciones transaccionales y analíticas.

En un grafo de propiedades, tanto los nodos como las aristas poseen etiquetas y pares clave-valor, lo que permite modelar atributos directamente sobre la topología. La unidad de almacenamiento deja de ser la fila aislada para convertirse en una estructura que conserva explícitamente sus conexiones. Sobre este modelo destaca Neo4j, una base de datos de grafos nativa cuyo lenguaje de consulta Cypher expresa patrones mediante notación visual de nodos y aristas, por ejemplo `(cliente)-[:REALIZO]->(compra)`, lo que hace legible incluso a las consultas multi-relacionales [32].

La diferencia práctica frente a una base de datos relacional aparece al recorrer relaciones. En un modelo relacional, responder una pregunta que salta varias relaciones (cliente → pedidos → productos → proveedor → regiones) obliga a encadenar joins entre tablas, cuyo costo crece rápidamente con la profundidad del recorrido y con el tamaño de las tablas intermedias. Una base de datos de grafos resuelve esa misma navegación siguiendo punteros entre nodos con coste proporcional al subgrafo realmente explorado, sin tocar el resto de la información. Para un sistema de GraphRAG, donde las consultas consisten precisamente en seguir caminos entre entidades, esta característica es determinante.

Además del rendimiento en recorridos, estas bases de datos ofrecen restricciones de integridad sobre nodos y aristas, índices sobre propiedades y, en algunas distribuciones, inferencia sobre la topología. En las arquitecturas de GraphRAG, la base de datos de grafos materializa el conocimiento extraído de los documentos y sirve como fuente de verdad que se consulta mediante lenguajes declarativos como Cypher o SPARQL.

**Sinergia entre Grafos de Conocimiento y LLMs (GraphRAG)**

En las arquitecturas RAG, el sistema recupera fragmentos de texto basándose en la similitud espacial. Sin embargo, cuando se presentan consultas que requieren conectar información de múltiples fuentes este enfoque tiende a disminuir su eficacia.

Una alternativa que busca dar solución a este comportamiento consiste en utilizar agentes basados en LLMs para construir y consultar Grafos de Conocimiento, dando lugar al paradigma GraphRAG (Generación Aumentada por Recuperación basada en Grafos). Ahora bien, la construcción de este grafo puede seguir dos enfoques principales:

* **Extracción Abierta:** Se le otorga al modelo libertad total para analizar el texto y definir desde las entidades hasta sus relaciones basándose en su interpretación probabilística. Este enfoque resulta útil para el análisis exploratorio de datos desconocidos o bien para generar un boceto inicial, sin embargo, resulta ineficiente para implementaciones funcionales, ya que, dependiendo del rendimiento del modelo puede generar grafos altamente ruidosos, con sinónimos para una misma clase y relaciones ambiguas, imposibilitando la interoperabilidad con bases de datos estructuradas.

* **Extracción Cerrada:** En este paradigma, se define la Ontología (clases, atributos y tipos de relaciones) antes de la ejecución del modelo. Esta estructura predefinida se inyecta en los requerimientos o ajustes del sistema, estableciendo límites en el razonamiento del LLM.

Bajo el paradigma de extracción cerrada, el modelo actúa estrictamente como un mapeador de funciones. Su tarea es identificar instancias reales en texto no estructurado y ajustarlas dentro de las estructuras lógicas ya definidas en lugar de descubrir cómo funciona el dominio.

De esta forma, la ontología actúa como un "molde", asegurando que el grafo de conocimiento resultante posea una estructura canónica, determinista y matemáticamente predecible [4].

Esto dota al LLM de un contexto estructurado y explícitamente definido, lo que incrementa su precisión al momento de generar una respuesta, además permite rastrear la procedencia exacta de cada afirmación.

**Inteligencia de Negocios**

La Inteligencia de Negocios (BI, por sus siglas en inglés) es la disciplina de la informática que agrupa técnicas de recolección, integración, análisis y presentación de datos con el propósito de sostener la toma de decisiones dentro de una organización. Su objetivo no es almacenar datos por sí mismo, sino convertir volúmenes dispersos de información en indicadores clave de rendimiento (KPI), reportes y tableros que un directivo pueda interpretar de manera inmediata.

El ciclo típico de BI parte de fuentes operativas y externas, las integra en un repositorio común, las somete a análisis y finalmente las comunica mediante visualizaciones. El componente analítico se apoya históricamente en el procesamiento analítico en línea (OLAP), modelo propuesto originalmente por Codd et al. [33], en el que los datos se organizan en hipercubos definidos por dimensiones (por ejemplo, tiempo, producto, región) y medidas (por ejemplo, ventas, unidades), y sobre los cuales el usuario puede ejecutar operaciones de *roll-up* (agregar), *drill-down* (desagregar), *slice* (rebanar) y *dice* (cruzar).

Dos debilidades persistentes limitan la efectividad de la BI tradicional. La primera es que los indicadores dependen de la calidad y integridad de los datos que alimentan el almacén, calidad que históricamente se asegura mediante procesos manuales costosos y lentos. La segunda es que una porción creciente del conocimiento corporativo reside en documentos no estructurados que el OLAP no puede representar.

**Almacenamiento de Datos y Almacenes de Datos (*Data Warehousing*)**

El repositorio sobre el que se apoya la BI es el almacén de datos (*data warehouse*), definido como una colección de datos orientada al tema, integrada, no volátil y histórica, diseñada para el análisis y no para la operación [34]. Su existencia responde a la diferencia fundamental entre dos tipos de sistemas:

* **Sistemas transaccionales (OLTP):** soportan el día a día de la organización (ventas, inventario, registros). Están normalizados para evitar redundancia, atienden consultas puntuales sobre registros individuales y actualizan datos constantemente.

* **Sistemas analíticos (OLAP):** agregan históricamente grandes volúmenes de datos provenientes de múltiples fuentes. Están desnormalizados para minimizar joins, se leen masivamente y rara vez se modifican una vez cargados.

La carga de información en el almacén se materializa mediante el patrón ETL (*Extract, Transform, Load*), en el que la transformación ocurre antes de persistir, o su variante moderna ELT (*Extract, Load, Transform*), en la que los datos se depositan en crudo y se transforman dentro del propio almacén, aprovechando su capacidad de cómputo.

En cuanto a la arquitectura del almacén conviven dos escuelas clásicas: la de William Inmon, que propone un almacén corporativo único normalizado en tercera forma y del cual derivan los data marts [34], y la de Ralph Kimball, que aboga por construir directamente almacenes de datos dimensionales interoperables mediante dimensiones conformadas [35]. La visión de Kimball es la más adoptada en los entornos de BI contemporáneos, ya que prioriza el consumo analítico sobre la integración transaccional.

**Modelado Dimensional**

El modelado dimensional es la técnica de diseño de esquemas orientada a consultas analíticas. Su unidad central es la **tabla de hechos**, que registra eventos o transacciones medibles (una venta, un envío, una atención) mediante un identificador compuesto por claves foráneas hacia sus dimensiones y una o más **medidas** numéricas. Las **tablas de dimensiones** aportan el contexto descriptivo con el que se filtra y agrupa: quién, qué, dónde, cuándo y cómo.

Para diseñar un esquema dimensional es obligatorio declarar el **grano**, es decir, el nivel de detalle exacto que representa cada fila de la tabla de hechos (por ejemplo: "una línea de factura por producto y día"). A partir del grano se derivan las decisiones estructurales [35]:

* **Esquema estrella:** una tabla de hechos rodeada de dimensiones desnormalizadas; es el esquema más simple y el más rápido para consultas.

* **Esquema copo (*snowflake*):** las dimensiones se normalizan en subtablas; reduce redundancia a costa de joins adicionales.

* **Dimensiones conformadas:** dimensiones compartidas entre múltiples tablas de hechos (por ejemplo, "Tiempo" y "Producto" comunes a ventas y a devoluciones), condición necesaria para cruzar información.

* **Dimensiones de cambio lento (SCD):** políticas para conservar el histórico de atributos que evolucionan; el tipo 1 sobrescribe el valor y el tipo 2 inserta una nueva fila con fechas de vigencia.

* **Tablas agregadas:** copias precalculadas a niveles superiores de granularidad que aceleran los reportes más consultados.

El modelo dimensional es deliberadamente simple para el usuario de negocio y, al mismo tiempo, predecible para el generador de consultas: esta doble conveniencia es la que permite automatizar su construcción y su posterior explotación.

**Consultas en Lenguaje Natural sobre Datos Estructurados (NL2SQL / Text-to-SQL)**

Las interfaces en lenguaje natural a bases de datos tienen como objetivo traducir una pregunta expresada en lenguaje ordinario a una consulta formal ejecutable, eliminando la barrera de conocer un lenguaje como SQL [36]. Con la llegada de los LLMs, esta traducción dejó de depender de gramáticas y reglas heurísticas para resolverse como una tarea de generación de código condicionada por el esquema de la base de datos.

El desafío no está resuelto. El benchmark BIRD, de gran escala, reportó que el mejor modelo de la época alcanzaba un 40,08% de precisión de ejecución frente al 92,96% de un humano, evidenciando que la comprensión del contenido real de las bases de datos, el conocimiento externo y la eficiencia del SQL generado siguen siendo problemas abiertos [37].

Un sistema NL2SQL típico opera recibiendo en contexto el esquema de la base de datos (tablas, columnas, tipos, granularidad y relaciones), traduciendo la pregunta a restricciones y agregaciones, y sometiendo el SQL resultante a una validación escalonada: análisis sintáctico, ejecución en modo de solo lectura sobre una base aislada y, de fallar, reintroducción del error en el modelo para su corrección. La capa semántica —las métricas de negocio definidas formalmente— actúa como ancla para que la interpretación de términos como "ingreso total" o "margen promedio" sea consistente entre consultas.

Ambas vías son complementarias: GraphRAG responde preguntas relacionales y cualitativas que exigen razonar sobre entidades y sus vínculos, mientras NL2SQL responde preguntas cuantitativas que exigen agregar medidas según dimensiones. Ambas convergen en la misma respuesta final para el usuario.

**Referencias**

[1] J. Alammar, "The Illustrated Transformer. Visualizing machine learning one concept at a time," 2018\. [En línea]. Disponible en: [http\://jalammar.github.io/illustrated-transformer/](http://jalammar.github.io/illustrated-transformer/)

[2] T. Brown et al., "Language models are few-shot learners," en *Advances in Neural Information Processing Systems*, vol. 33, pp. 1877-1901, 2020\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2005.14165](https://arxiv.org/pdf/2005.14165)

[3] R. Davis, H. Shrobe y P. Szolovits, "What is a Knowledge Representation?," *AI Magazine*, vol. 14, no. 1, pp. 17-33, 1993\. [En línea]. Disponible en: [https\://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/1029](https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/1029)

[4] L. Ehrlinger y W. Wöß, "Towards a definition of knowledge graphs," en *Proc. SEMANTiCS 2016 Posters and Demos Track*, 2016\. [En línea]. Disponible en: [https\://ceur-ws.org/Vol-1695/paper4.pdf](https://ceur-ws.org/Vol-1695/paper4.pdf)

[5] Y. Gao et al., "Retrieval-augmented generation for large language models: A survey," arXiv preprint arXiv:2312.10997, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2312.10997](https://arxiv.org/pdf/2312.10997)

[6] I. Goodfellow, Y. Bengio y A. Courville, *Deep Learning*. Cambridge, MA, EE. UU.: MIT Press, 2016\. [En línea]. Disponible en: [https\://www\.deeplearningbook.org/](https://www.deeplearningbook.org/)

[7] S. Hochreiter y J. Schmidhuber, "Long short-term memory," *Neural Computation*, vol. 9, no. 8, pp. 1735-1780, 1997\. [En línea]. Disponible en: [https\://www\.bioinf.jku.at/publications/older/2604.pdf](https://www.bioinf.jku.at/publications/older/2604.pdf)

[8] D. P. Kingma y J. Ba, "Adam: A method for stochastic optimization," en *Proc. 3rd Int. Conf. Learn. Represent. (ICLR)*, 2015\. [En línea]. Disponible en: [https\://arxiv.org/pdf/1412.6980](https://arxiv.org/pdf/1412.6980)

[9] P. Lewis et al., "Retrieval-augmented generation for knowledge-intensive NLP tasks," en *Advances in Neural Information Processing Systems*, vol. 33, pp. 9459-9474, 2020\. [En línea]. Disponible en: [https\://proceedings.neurips.cc/paper/2020/file/6b493230205f780e1bc26945df7481e5-Paper.pdf](https://proceedings.neurips.cc/paper/2020/file/6b493230205f780e1bc26945df7481e5-Paper.pdf)

[10] A. Y. Ng y M. I. Jordan, "On discriminative vs. generative classifiers: A comparison of logistic regression and naive bayes," en *Advances in Neural Information Processing Systems*, vol. 14, pp. 841-848, 2001\. [En línea]. Disponible en: [https\://ai.stanford.edu/\~ang/papers/nips01-discriminativegenerative.pdf](https://ai.stanford.edu/~ang/papers/nips01-discriminativegenerative.pdf)

[11] S. J. Prince, *Understanding Deep Learning*. Cambridge, MA, EE. UU.: MIT Press, 2023\. [En línea]. Disponible en: [https\://udlbook.github.io/udlbook/](https://udlbook.github.io/udlbook/)

[12] A. Radford, K. Narasimhan, T. Salimans y I. Sutskever, "Improving language understanding by generative pre-training," OpenAI, 2018\. [En línea]. Disponible en: [https\://cdn.openai.com/research-covers/language-unsupervised/language\_understanding\_paper.pdf](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)

[13] S. J. Russell y P. Norvig, *Artificial Intelligence: A Modern Approach*, 4a ed. Hoboken, NJ, EE. UU.: Pearson, 2020\. [En línea]. Disponible en: [http\://lib.ysu.am/disciplines\_bk/efdd4d1d4c2087fe1cbe03d9ced67f34.pdf](http://lib.ysu.am/disciplines_bk/efdd4d1d4c2087fe1cbe03d9ced67f34.pdf)

[14] A. Silberschatz, H. F. Korth y S. Sudarshan, *Database System Concepts*, 7a ed. Nueva York, NY, EE. UU.: McGraw-Hill Education, 2020\. [En línea]. Disponible en: [https\://www\.mpgcamb.com/wp-content/uploads/2024/12/Abraham-Silberschatz-Henry-F.-Korth-S.-Sudarshan-Database-System-Concepts-McGraw-Hill-Education-2019.pdf](https://www.mpgcamb.com/wp-content/uploads/2024/12/Abraham-Silberschatz-Henry-F.-Korth-S.-Sudarshan-Database-System-Concepts-McGraw-Hill-Education-2019.pdf)

[15] R. Studer, V. R. Benjamins y D. Fensel, "Knowledge engineering: Principles and methods," *Data & Knowledge Engineering*, vol. 25, no. 1-2, pp. 161-197, 1998\. [En línea]. Disponible en: [https\://www\.researchgate.net/publication/222305044\_Knowledge\_engineering\_principles\_and\_methods\_Data\_Knowl\_Eng\_251-2161-197/link/5a967c9baca27214056979b4/download?\_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6InB1YmxpY2F0aW9uIiwicGFnZSI6InB1YmxpY2F0aW9uIn19](https://www.researchgate.net/publication/222305044_Knowledge_engineering_principles_and_methods_Data_Knowl_Eng_251-2161-197/link/5a967c9baca27214056979b4/download?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6InB1YmxpY2F0aW9uIiwicGFnZSI6InB1YmxpY2F0aW9uIn19)

[16] H. Touvron et al., "Llama: Open and efficient foundation language models," arXiv preprint arXiv:2302.13971, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2302.13971](https://arxiv.org/pdf/2302.13971)

[17] A. Vaswani et al., "Attention is all you need," en *Advances in Neural Information Processing Systems*, vol. 30, pp. 5998-6008, 2017\. [En línea]. Disponible en: [https\://arxiv.org/pdf/1706.03762](https://arxiv.org/pdf/1706.03762)

[18] L. Wang et al., "A survey on large language model based autonomous agents," arXiv preprint arXiv:2308.11432, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2308.11432](https://arxiv.org/pdf/2308.11432)

[19] N. F. Liu et al., "Lost in the middle: How language models use long contexts," *Transactions of the Association for Computational Linguistics*, vol. 12, pp. 157-173, 2024\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2307.03172](https://arxiv.org/pdf/2307.03172)

[20] J. Wei et al., "Chain-of-thought prompting elicits reasoning in large language models," en *Advances in Neural Information Processing Systems*, vol. 35, 2022\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2201.11903](https://arxiv.org/pdf/2201.11903)

[21] S. Yao et al., "ReAct: Synergizing reasoning and acting in language models," en *Proc. International Conference on Learning Representations (ICLR)*, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2210.03629](https://arxiv.org/pdf/2210.03629)

[22] Q. Wu et al., "AutoGen: Enabling next-gen LLM applications via multi-agent conversation," arXiv preprint arXiv:2308.08155, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2308.08155](https://arxiv.org/pdf/2308.08155)

[23] Anthropic, "Building effective agents," 2024\. [En línea]. Disponible en: [https\://www.anthropic.com/research/building-effective-agents](https://www.anthropic.com/research/building-effective-agents)

[24] JSON Schema, "JSON Schema: A media type for describing JSON documents, draft 2020-12," 2020\. [En línea]. Disponible en: [https\://json-schema.org/draft/2020-12/json-schema-core](https://json-schema.org/draft/2020-12/json-schema-core)

[25] Pydantic, "Pydantic," 2026\. [En línea]. Disponible en: [https\://pydantic.dev](https://pydantic.dev)

[26] B. T. Willard y R. Louf, "Efficient guided generation for large language models," arXiv preprint arXiv:2307.09702, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2307.09702](https://arxiv.org/pdf/2307.09702)

[27] W3C, "RDF 1.1 Concepts and Abstract Syntax," 2014\. [En línea]. Disponible en: [https\://www.w3.org/TR/rdf11-concepts/](https://www.w3.org/TR/rdf11-concepts/)

[28] W3C, "OWL 2 Web Ontology Language Document Overview (Second Edition)," 2012\. [En línea]. Disponible en: [https\://www.w3.org/TR/owl2-overview/](https://www.w3.org/TR/owl2-overview/)

[29] W3C, "SPARQL 1.1 Query Language," 2013\. [En línea]. Disponible en: [https\://www.w3.org/TR/sparql11-query/](https://www.w3.org/TR/sparql11-query/)

[30] W3C, "Shapes Constraint Language (SHACL)," 2017\. [En línea]. Disponible en: [https\://www.w3.org/TR/shacl/](https://www.w3.org/TR/shacl/)

[31] R. Angles y C. Gutierrez, "Survey of graph database models," *ACM Computing Surveys*, vol. 40, no. 1, pp. 1-39, 2008\. doi: 10.1145/1322432.1322433.

[32] Neo4j, Inc., "Neo4j Graph Database," 2026\. [En línea]. Disponible en: [https\://neo4j.com/](https://neo4j.com/)

[33] E. F. Codd, S. B. Codd y C. T. Salley, "Providing OLAP (on-line analytical processing) to user-analysts," OLAP Council, 1993\.

[34] W. H. Inmon, *Building the Data Warehouse*, 4a ed. Indianapolis, IN, EE. UU.: Wiley, 2005\.

[35] R. Kimball y M. Ross, *The Data Warehouse Toolkit: The Definitive Guide to Dimensional Modeling*, 3a ed. Hoboken, NJ, EE. UU.: Wiley, 2013\.

[36] I. Androutsopoulos, G. D. Ritchie y M. Thanisch, "Natural language interfaces to databases – an introduction," *Natural Language Engineering*, vol. 1, no. 1, pp. 29-81, 1995\.

[37] J. Li et al., "Can LLM already serve as a database interface? A BIg bench for large-scale database grounded text-to-SQLs," en *Advances in Neural Information Processing Systems (NeurIPS)*, 2023\. [En línea]. Disponible en: [https\://arxiv.org/pdf/2305.03111](https://arxiv.org/pdf/2305.03111)

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,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>

[image3]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFgAAABqCAYAAAA4J5aSAAAnmUlEQVR4Xu19B3gc1bm2IUCAJBRbXVaX1XvXaqXVatV7r1axZMtVsnqXVr333rtkS5ZkSbZsGVeaMcZAIHRIMJDcJP9N7k3lErD9/t8ZbH4yF4ghtjC/9T7PPDu7M3Nm5pvvvN/7nTnn7IYN61jHOtbxw4JUKr1XKsW9/N/X8R2QlNNj4x4jrXYIK3tBz0t6xSSoDmb+9TALaISBZxksfPLfCNrVZMc/bh3fgLaZp2SdQ0sK9byKf2noX3bNNLgOVhGtsI3rhSCxF8LELtgnDMAiahjaXjXQdcm+kj24+DN+OevgQTpy9kFNx9T3jDzLYe7fCLPwdtgnjkKYPAZJ6ji80g7AL30WXplTcEubhMOOMVjG9kE3oAZmgWWH+eWtg9A0c/4hm4Cck/qSkiuG/h0wj+6FQ3I/JClD8E4fx/7mFdRNPInhY6+gfekN7G05Bf+iw/DInYfT3mlYJgxCP6QVyqICeO9oFPDLv6sRsLM+wcA153fGIR0wJW+1jR+Ey55xREsPIW/wFIaO/wKrL/4Wxy/9Goef/wAlB15GYOkRuOUtQESebLNzEiZxQ9AN6YSiSApheHUn/xx3JQYX31TSE6d/tMW9AkYh7bDeNgTJrkkEZUyhfe5FzD97GSfIsMcufojBlbdQOPQsYqoX4ZJ7CMKMeTjsn4HNnimYJIxBN6IP6n6tkHeSwjq4pot/rrsOCTnDxuqCoisGvp0wCu+FTdIg/DNGkNmxiqETr+H4S/+B+acuo2vu50hpPw3PHKKCjAU4pB2CYPck7JMnYLF9nIw7Ar2oAagHtEPFsx6b7PPhGNVkwz/fXYOGoQsGei7Zv9fwKoHh1l5YJg3Agzg2q/tJzD19GbNPfYjOxdcQU7lMFDAHUe7C556aPAWrpFGYE9fqRY9AI3QQmkFdUPdvh5JnI+RdqiEnlEJdUnqAf867BgDuVXUquqLtWQ3jsFYI9k4hsGAOjYdexOzTb6Nz9V3sbj2DgIIluOYskcfOwW7fAVjvmIBJ7AD0I7qwJbgDGv7dUPJqw2bPFii41UFOXIWNDsWQE+ReS06+dD//vHcF0irnFfXdct7W9K2DQUQ3bLaPYnvNCnqJWyeevIzGhZcQVrYAHzK4JHsB9nsPwpLkl3FcH+3fC62AVqh6N2CzRy2UyFtlHcug6FSOTQ4F2GSX9ZmsXdbrwtguEf+8dwWE4ZWdqk6l0PRphem2UTinTiGj+yyGz76L8snz2FqziKASCl4UuBxTZ2CeNAL9qF5oB7VBzbsequ51pA5KIeeQDxm7TKg6Fzyh6SZN0HTLN3JN7nuUf767Cvahxc3KThXX1Mm4BtE9cNo1hNz+p9G58jpS+k4joHwJfqXL8MydI6+dhlniEBm3B5p+RAGSeiiJqqAgyIeCXcafDQOqszZsCPsR/xx3LXJrZx9VFOZB1beFjDtIXDqAgp4T6Dz6FnImXuQM6128BEnOIgT7D8EknrIx0sEafg1QEpdBwaEE8na5v9NyLSzgl70OgqFr1vPqPi3QieyBRdIwBa85NC+/gUzSsyHVq/AsXoEki1TCvoPkuaMUwFqh5lUPFXEl5O2z/1tdnJuindL2Y365dz2WL+FhJfvcT1Xda0hS9cF6+yAlCEdQNvcGQmtOIqDyBHxKluGceYgMOwKjmAFo+7dyQUvGJvuqqU/tDn6Z6/gSTDzyXtjsXE5GayNaGIVv3kEUTr1MnPsM/MpW4C1dgWveEqmEERjE9JLsaoayaxXkBTnviiN6tfjlreNLSMxe/JmysACa3o0wjOyFOGUSaf0XsL//WYRS8uAtPQK3/GVKHg7BkDxX078Fym4VkHPM+9OGsNn1APavoCzI/LOqZxP0wnphnTiMXa1PIaFhFSHliwgsX4U4Zw5CysxM44fpIZBxxVJoukpL+OWs4yvgFl3RoexcBs3AdpjFj8Bl/wEy8FlEVCwjoOIY8e4xiNKJd7cNQYcyMkVRMfTcS6X8ctYKUunsA+E7O2Ps/cuPGbllviGKrJ4K3tEkpg133muowoajapsdc6+peNTDKLobdskjiCg7RssiQipW4FP2BEcN1klj0A/vhoZ3LbQ8S9v45awlNIS7PlKXlEHbsw5bSL0YkZw08qyEqUf2m/x9v3foigtPyYoqoOpTD8v4frgQ9ybUnaL0d4mSiWNwK1qBc9Y8jEiyafs1QtE577MNG3APv5y1gl2AdFjNvQI6IV0wi+2CXWIv7LaNwIZUj3lAHawC8kf5x3xvcAwo3cmSAhWvWhhEtEO0awKR5L0hJYcRXL4M35IjEJPetU4eI8+tg4qo6G+imP7N/HLWAn772jVUxLl/0fKpg/XWXjjTtXpmTCOoYAEBeXPwTDsIMdU+Pd8qmPmWDPGP/16g6ZD1ayUKVhoBDTChjM2DLjKkeBHBZGD/0iV4FByBMGUWplv7oOpaAtOguhh+GWuBmMwuazVx3l9VSRYaRnXAe884tpM+zx96DrFVR8gpjpKR5+G0kwwc2ABN57yPTdwafsIvZ82hZFeMzR6ke4ObYRU/CZ/sWS5rCyk/SoGNvDdzgWvP1Q9tg5Zb4UX+8WsB1n9CWZT3ly2UhhtGdECwcxR5JB/nnvkAU09+gMS6FURXriCg6DDEqdPQD2mBqrMUBq5SVX5Za4qdZZMByuJa8t5GmMR0wzF5Gn7MuGVHyMDEvXmLEOw5CNPoXmh7lYNudc0jdGj6sLGSU/7HuoGtsErqg3PKBLJ7nsWRFz/C9FO/QlbPOcTXryJIukyp+yHYJo9Cy78JyiIptvjkafLLW1OoOaT9bjNlYVoBbbCI64HLninOC0LJe4PJwC4U2Gx2TMAwpBU6HkXv8o+/3QjZ2+Os4VL8sbpfC6y29UOUOo6U7qcwdvoy+o+/hlQybkLzGXKIFXgWLMF+7xRM4wagRmn+JtvcT2xi2h7hl7lmmJn58CF56yyoelRR9e+hSDwEt7QpBJUsI5SCXGDpMeLegzCPHaSgUQOz4Kpofhm3E9LZ1x7QcM7/u7p3M/RIvYgzp7C382kMnHwPI2fewK72s4hrOYfwmpPwzFuGgK7VmBKgLUHtUBKVQVVcPMIvc03hmdCdqOAghbZPE8zoBlgHELeMGc4bgiqOwrv4COx3HoBRWAdpTekf1pIeWL8104Di45q+rTCK6YUNBa6MrlV0n3gbfad/iZzhJxHfQp5bfQY+xcfJEQ7ANGEEmkHd5DCN2GiR8qHJ1u85wKkL099RdKqALtGDVewAHIkevHLmEVpxnAx8DJ6Fy7CkrE0/sBHCuLZQ/vG3C+HpvWJ1p4JP1H3bYL59EOKUcaT1kuee+wiV868iufMU4lpPIahqFR75S3DYNw3D6C5oBtRDSSKFrEP2+/wy1xy1fZce3SxI/5uSuBL6lPZaJQxxPWy88ha44OZXugLX3MMw39pDWVIZwtaoISdqf4eHuqSEOLcBeuS5IpKMad3Poffk258bt+s0Yhjn1p+hzPIwhPsmYR4/CE1fMi5JSHlh1ruWUY0y/HLXHDHZExYbbdPpoqphENYNm8QRiIjDvOiigyqPw7fsOJwz52Aa2QEDH+mr/ONvBxgtaAjzPlX3boFxXC9sd49REGPGfRcDp98izz2D6OZTCKk9CY+S4xDsO0BZXC/0gtqgKCq5Jmub/htRfMtj/HK/F5h6lDfIOhZDyaMWRlF0M8S/orRZeBdRalyxAo/CoxCmzkA/qB6SXYPm/ONvNUJ2d7mriQs+0wnthkXiIFxSJ5HRdx5D595D1cIL2N71FMIbTyOAHr5nAfPcKRhHdkGLPHczS5LcCjP4ZX6vMHIrPS7jJIWyZx2MYwZglzwB5/RDXGD73MDLsKU01CCwhgLc7X3tE7K30VdDVPiPLcS5ZtuHIEmfRHr/8+g+9R5q5y8hueNphLc9A7+qJ+BesEgBbQoW5LlavnVQdCmFgkPuO/wyv3dsdir4pbywDGoUcY1jhmCzawpOGYe4txX+pIHdKdmw3zkNA//aP9Hut61RRwrcq+JcekXDuxMmsT2kYiZQ0LOKvid+ha7THyGx80mihTMIrn+CAhp7/zcNMybFKDCrOJdck7FKvSxIHLzz+hQr2GX8SUFUDjXSmCZbh4nvDnxhYD/K6V3zZmGznRIM/9pf8I+9VTh7FvcZuhc9px3YAOPYTjiRiknrewo9J99Hz6kPkTb4LLY2n0ZE/Wl4SY8S5zKdOwSt4DZsdq+GrCD9sjC6+3F+uXcE5G0zP1NwroIqBRSj2GHy4Gmuq5NXyVFOQUhyZ2C7fRw2ka2z/GNvBUJ2tgWoOhZ/ph1YD4vtI3BNO4Dc/mcx8uRllC68TmrhLGfcwIoTnzc2pR7kOgmyLgSKknLIO2a/zS/zVsDYM2NGxyX79wr2mZ9scc350Nw/p6ut7di3p0g5u2zIi8jAPtcNvHsaosx5MvAKfKXXPThpDLZRLQ38Y/9dRKf1uW5xKr2q6dkB062dcEs/iKz+C+g79RbqDr3M0UIMJRFhdac44zqQujFLGIYaGVfWmXSufdYHoj2dP+WX++/CRJx+XtGxjFNWm73qoOVXD32/OmiIcv8enz+ix9//GyFrl8t1ulNhmVLcKBl45nMDFzMNfIw08Bxsk8ZhF9V6SzuN9F26dL+aMBe69GBNtnZRcjOJ7IHn0H/2HfScfpsC2jnOuJGNlKFJmRQ7CFOiBZ0QSn+dS7FJkPW+Z8zELW9fsPLNPiovyIO6RzV0/NuhH9ILC6oxJiHkgP5V0HPJ+jP/mG+ErG0uNokqoUwcbEAcbLWLcfDcFwZ2z5uH3Y4JyuDab9k7t9Dk7jANx4Kr+qHtsErugyRtDBnDz2L4qfdRfeglbO84g6CWc5yKcaPz21P6qxdFqS8lHQquFSTFirbyy7wVcAmt2S9nX4xNbvXQDO3hetvb7RyFE9Uc59Q5WMSPUrBvw878CQP+sV8LBTKwDDOwTxMMYwZhvXMKjvtnud46vmXsBg+TdBuDIKb1lrx3C9jdHqgqKr6m5dVC1NNPtDCFgsET6DvzHnHuq0jq/pwWgipPUIZ2CIKUaQpoI1D3bYKCczEUnHJuC+cybHEsfE5WWMF1pdWPGoJL2iRCig/DI+sw3DMW4bhrFGbhnbANrbz5oQ3yVtmfyDpVEtc0wiCqH1akGFhi4VF4BH6UKrvnk97cPQH7mNZ5/rHfFpcu4X5N52xs8a2FeXQfPPZPIWv4Oa7RpvPkr5DUeRJb204jvP4k92AdyHNNKHXXDumEkqQCcg6Zb5lkjt+2hhs1QdYv5ZwqoOLTDNO4fuztOY/8yVcQUES2KFiGJHUMVlv7oCZKvfmHrGiT9d+yVKiyZyP0IlhP9XEumLjnL3MG9ipahuPeCViF1V3gH/tt0Ld86WEDt8zXNDzqYRDRCYcdA8jpew495Lltpz5ACsmymOaTCCOd603BlV2DSdwYtgSzVrEGKDsWviyKH3mQX+6thLow77cK4mpuGINVYi9n3MyR5xFctoyA4iW47ic7xPZDwznz5tvD1ZxyXpEVlkKReEeX0lPzhBEI9k5TcFukROMYfEqPQpw+A7PQhr9812ZK99jqCGWH7Guqbg0wjOqBPT3EpLon0PPEGyg/cBFxbecQ1XSaHugK1yWAtS3o08NW92omSqBoLiy4bRr8BqQjzyso2udeUZDUQDOgg6PFrfXnEFS6jJDKVQQSZbpRjbKM6YN5UHU///ivxRbXgkNyDiVQkNRCO4jkUuwg7HZPQpI9D/8yCnSUzbnSull4Izy/Qw/JgKSmaCW7dCg7V0PDq43KZ0FtDrmjrxA9PI3YuuOIaDyN4JpTEBMtsIBmEjcIDR8KaE5FUHTIfvV2ey6De3ybp4KwAIruNdgS0kMJ1xTcc5fhQ/QQXLUKv6KjkOw9CHMKtk7xbcn8478WOq7FeZvsCiHvUsO9LjJivSjp6Tmnz3KJhm/ZEbjlzlPVaEdIzqgh//h/hY1mez6TcSyGCske7YBWqiFj8CRlEN98FgHlqwioPgXf8uOQFCzCeh8byjUA7eBWKIopiXDKeTEsbPYBfpm3A0aS3EoFdp3eDdAL74dt6ixpb7r/UvLeyhV4U3ou2jkO47A2+O3pv3k7+O1pNpQVFFCEroUaKQndiC6YJw5xbwa8WaAjivAqXIbd9gGYh1U+yz/+m5BYOOq+UUAJgaSMdGUrpbY9MCKpY7VrCsK0Waoli3DJWiLVMkfqZZJujAKIRxNUJZUw9K3045d3O6HtmP/B5y99GyjhmoATXZNX0QrV4OPkCCtwz54jahuGQVDLt3vhK5W+9oCCXd5fWPRkwYSN/jHa2k80MQEP4mGWzflKj8GJvluE14G11fLL+DqYe6SWPS6shqwbJTLe7dAI6oNezBCME0juJI9zDUtWyRMwTxqFfnQXpeu1UJaUUkDLfZlf1u2GiiAHau6NFIe6YJE4wT181hYeQPTgzboskHQ1pwCnQ1qcf+y/hKJ9xityDqVQcSeB7d8KvchuWO0YhVvWPHyKiYdKKNDtPwTb2C4E7hry4h//dTB1SSl/XFiLja41UPLqgKp/N7TJS3WiB2EQN0yZI3lEzAD0w3qhwZocRURVgswXRVLpffyybidYbFEmvtfwa4IR6V/BrnG4Fy7BmzzXjwzsSTVZuGcKRmQXNUn5P/jH/0toOe6vkxMUkdakKuLXBt2wblhuG+aeGmvUZgZmT1SQNAKbsPqbponQXS3+jwvKscmllhsPp+zbDrXALmhQlrSFDK0VQuvE+1vod0VKf5WE2Rdvd5vzVyEusz90M2WI2sEtlK1NwDGFam/JMnwrj8On6jics+a4FxF6lKZruxW/yD/+piBrlwV5Eelh5sUkU4yi+uBAasI1Yx6+pIW9ipY4gzMvdoxtDuAf/3WQt82ErCOpFNKXLENSpgxus3crfTZBib4riilzEhaTcXNf4B+7Fmhre+fHSrZZdM9NMInuIe+dhkvOHAXeY2Rg8t4S9kbnAHlvFzS9q69pued58su4Kag6578q51QOZdLDar5EE+EkVYgmJPtm4Z17mMT/AsmWw1wnO/uI+pt+N7fFJXd4o00WGAXJOpMycK0lSVgHedKbco7k3fYFrFXsgkh6dk1p4QasvHJ72QsHlvzYJgxTejxD9HAU/hWr8CEOdqcMjvUQMgglp5BI/8vtu3YBiMyctpURSqFAfKnm1QBd/y6YbuunNJl58SzJlSXuPZ04bRr2CV3fIpJK79UR54/KWqVhoy0Z06kKG4WV2CgoxUabHCjYZ5+0TO77XobNVvYeV9wszPi7OmWXprFDcNgzzSkmHwrsgZVPkIEXIcmZ4XIDLS9SWR7FR/hlfCtstM/HRqqySiS2tX3aoR/TA2uSJqIUduJFCniL8Mw9BPG+MfinjHyrnpV+27vtZK32vCljnXXlUcvMK7L2uZ9quRTs4++3ljDyzj2kStzL3kazbmHueUcouSLdS/Tgz3nvDBxSx2EYSkHYvRKOCV3/3gQhm4WZb8k4kayi6qviSV4c3EW81M+ljSybY/2DmeBmnVIE8d3w3tMfzi/jh4Jd0nE5FYoL2oGdMIjqpGC+gPC6k/AvPYIgogfWBuNEdGG5bRTq7nVQd85f4JfxrWHgWRK2ybaQax9W9KDMzrcDBmGUe8cPQbR/Bm45C/AhyeJL1chpzxgsIur/nFBxQIVfzg8BWuL8NzQDWmBIktFm5xhiW84iqHKZ68kUyDLL7EOwSZ4kbu7HZlI4t+zNyWZB1mVZIn05SRVUvSj7Yk+YTmJHwU2cMQePPBLgxStwzTlEyccg7CNrX+eXcafDPrBqRF1SwXWzsiH55Uuad2vjKYRUHCHjrnBdFoREi2Zxg9wYQTVx4Sl+Gd8Z8dLDjynY5l/dRIpC0bOOe1fHjGwWNwRbEuCsz4R73hLHye45hyEiWSNJbB7kl3Mnoqnp/ENG3iUXlT0roRXWQZJsDFE1x7Gv7wWElh1FcCnr+krpO6XFrNZqB7WTciiDKF56axubbENrC1kLmzxxj5JXI9ToKepH9sEsYQx2e2a4nu6+xcfgTXLGjfjYjlSFOK65jF/OnQYzn7LTap610A5j0zH0c8bNGruE2IYnEEK0wFrM3CnWOOydgAHdryoFNlXnnJtv+/02kLFO+z8bReWQI12s5NUMzeBO6EUNwmzbBDfJBmvK8yogTy5eIBlHdEEXLIlvKOWXc6cgt2bSiWVrhpH9pIwG4Z4+icKDr2Fn5xkElx+hbHWFePcwpcTTMI/rh6p3I5Qcc64K47st+WXdEtiGVJlsEpZAxqUeCh7NUKEUWiu0GwYxQ7DYTnycPk9GXoAnMzBRhXjvDIQJvXBLbBvml/V9w3N7Q5Kae8Fn+pG9sEwcgk/uAWQOP4+U/ucRXEGalxZX9mosdRYWiZQS030qOJdBx6Xo5hvWvwvUhHnLcg5llObWEx9TiuvXAs3QDq7jh/X2g3BIIU1MwY7l7Z5FR8jQC3Ci4GAd3fZuROHoHTEYXMet4K/6we0wjhkkJxjDvu6nUb34FnInLyGAeNdHugoJZWs2+6ZhQpmcVmAHVCiF1/Fco2HBj5ps/1ROUABF1yYoejdBNZCCHglv47gJWO0gI++fhUs+eXPJYfLmw+QJC7DdPQ6r6PoroSm9Kfzy1gpZ1Qv2Gk55n+gFt8E6YQCS3cMoHX8JHavvEzW8QoqBZWzH4Ja/AkHaHDfkQIcCH+NoWfv8K/zybhtSpMcekbXa+7GsYw0U3Jqg5ENGDuiANkk3g9gRmG+fhlP6HPcW2J30sWcxVTeiDnHKAdgnDsJ1R1d9cu7sms3Hk5Q/LW8bULVo4F0F04gWOOwY4aYbyxt4Bn3H30fB6EUy7hL3/k9C1CZMPQTLHVPYEtoDFcpglZwLrun7Vmbzy72tMAibfUDWLvvq404V2ORKQc+7FSr+HVAP7oZOxDDx1iQFvgNkZDZYcZGC3yK8ixa5XkEO+2jb9gFYxrT/0SO2rZRf9q2CX3J7sLlv8etmYU2wiO6FkPSt+/5xVEy/iIFzl9F16leIrTyKoKIlLji7sBGrbCrHbcPQIFpQcqlijU7/MImo1uGXvSawCa2L3SQsuLbJuRKynJEp8JF806B0mgU+NuOJLXsLUvB5oxDTyd5F5NV55M2kMtjcarZkaJb9ee3syN9wi7rCxmUP+ht7l1+1DG+/ZhbTA0HyEFwoAUqqXkbb4dcx/fT7aF5+BXF1lESQrPRgATntAGlgkmLRA9AM6YIKUZ+cIO+aWVC5Kb/8NYVJQEXS47aZV2VEFZBjU3R510PZr5FEeyc35Yxx3DAskybgU3QM4TVnEFR6jLQlZX6FC/DKpWCYOQmXvZOwix+AbVwPrCJrn3FP6ckSJlWZ7KmfVfimWbDZUC5p0+pG/8QWXZ/4lmZLn+J3TYPrYRzZwY2bc2BdsFJGkFR7BM1zL+PgU+9j5tmPkD/0NCJKSbfnzkOSzqYbO0ixYxhGsb3QJs9VdGXzt5Vd03UvE/PP+b3A0L888nG7rE9lnaspna6nZKSRUxfqQR0UJPpgGDMMq+1jXON8RPUpJDSdRSQ3tHWeawr0IBphr6LEaTNwIC+y3T4C6/g+mEd1XLWOafmNQ1zbLxxim591jms9KY5pPem8tfUpx8iWn9uGNv3BLLDhU4uQFlhHtUKQ0A/7pCFK10fgSw8uoWoZ1RPPYe78h1i4+Gv0rL6O1O7TXA999xz2Tu0QbHdOkI4fhH50N6kFytJc6yDvKIWKuOCOm6v4HhmbrH/I25dBSVxLRm6GMuNlX9Z20QH98D6YEG1YbRuFE3lsqPQIUnufR9HIJaR1n0Vi4xGEV8zDJ5+UB2vMz52BZ9YBuGbOQJQ6CWHKBBz2jFLWOALB7lEupXXdPw23fVPwogcXmDeH3fWraJi4hMnVd7D60kdYeeUypp75JdJ7zyCghLw1jxbKMsV0fofkMViQktBjU40FtEKN0n8FpyooCnIvm94pg2X4CJPOPqBkl/6CjF0OZJxrKONrpISkgeMz1nbBujyxRiJzkj+WpCYc6UZ98o8itf8Cig9eQtXcS6iYuoSiITYP0DnsbH8CMfVHEVl9BBGVi4isWER02RHEVhzBjroV5PWfQc2BC+g6+ipmzv8Ghy/9B5Z+/hvMv/AhOo6+hezeC4igjIxxvnPGHFHBHPExoyNWO7qgF9YGdZ86KEuIEkSV2Gid+UeR6Pt5i3LzCJv9kYpLVgXr+yAjqoasSx333k3Fu4W8pB2aAezGeimY9HOd6ayTuiDaQxydOU+GW0XR+HnULVxE55HX0E+eOHT6fQxTtB87+S6mT7+HA+fexaFnLmOBqv3SxY+w/MKvsXjxAxw89zY6ll5C4fgFxDacgCfpcNa86JxxkFLdSTiSOrCNH4EFyUidMDZfJtO37P0fpf4OUvLcwnNuW7vl+Ldzx8LSMvl+NUnBEzL2eZARssyPNLOkBork1SqkNtiEy1qBbdxbZP3IfqKPQa61ypo8244CjiNRgHjfONxSJ+CbNY2QwllESecRVjyP0KIF+OXMwD1jBi5sko3UGfLOaW6EERsI47BnihsZxaa4sSQaMI6mc1DQ1QnqhBZR1mY3ojBRORQo7ddwl/ZuCPsBT+loE1HnqGCf/o4sebScIykN5yrOoxVJcWz2aoCqbx15UzM3kZJ+WDeMo3phSsY22TpOHDlJBp+GffIMbHdMk+EPwJqqONOqNrtofecMrGixSGYqgLyTApxF4hA9KGbUPhiE90A3pI2bzpHNOriZ1IEiUQFrFZQV5P5JXVxQzL/eHyzUnAsnZGwy/0dWUAgZSk5kSDvLuZBXu1Zhs0c9VL2auFFNLCBqk6fphHZBJ7yb06X6MQMkoYZgFDfEdRQ0o4XNsMJ9xrAH0stNgsem1tULp+NCqAy/Nm5qMRUPRgOVUBCVQt6hELK2OVCXSButAzs28a/xBw82TniLu7R1E93kJrti8qQKyDNpR1ytKGmAvKQOSp7kaT71UPeug7pvA0X4JlqaoRnYCu3gdugGdUM3kAwZ2AXdAHoQlD1uYcb0b6eH1MyNpmfj+5TFVVzgkiV+lWFvrm2zsdkx5xljr3Jj/nX9f4n4+JEHTfzLMpTts9+Wtcm4KmefTx5WAhlBMfFjGdc/Qp48XZEoRcmZtQfQwvE4eaPr54ucpAyyklLIuEjJQ5kx2YBvbrZsMmjmpwq2Ge+pCHMa+ee+6+CZNGCiJsrfre5UeErGKv9jGZs8bGLB0SGfjEbeJyRaoU+2yNMDUBAUcYsc0Y2sPf1ul4+NbOCObdZ/yjlkP6lon5EXsPOAOv886yCwN7WWvlJVff9yc2M/aYKuZ9GsqlPOOUVBxitytplvKthlvKYkSL+oKsg5ruVa1KbrVbJNy0VqYRIklVvrDoLrWMc61rGOdaxjHd8zioqKAu+5555rtMoGe/zT4ufnN8n2mZ+fV5ybmwtZXl62/9Kh34h33nlnzYcG3HF45plnfvbQQw/95d577+UM6urqur+5udmivr7epKGhwYiMqsb2S01NlbBP9p9Gubm52UNDQ6FJSUm7R0ZGAtPT07mR8J2dnQo7duzw6enpCaqsrLSSSqXaw8PDwbR925dOeXeBPFLmgQce+HjDdY/19fW14O/DQIZzF4vFlrt27TKKiopqp4fgFxIS0sS20fdq9lleXm5I+xysrq7237dvX0JFRYVWTU1NwO7du0v/qbC7CVT15cjA/7PhuoGDgoK+0sDXPfiLt8L9/f2h9DD+6e/JmIF9fHy4OSPPnj37YEtLi25fX59MY2Oj75f3W0tQzbxC9HeVqO6WTM3wrbG0tCRPBv5kw7/wYDLYfW+99ZYM8eoj58+f3/jqq6/K0+dDL7/88mOMay9duvQo7cN1WL5w4cIjs7Ofzxb49NNPP/7hhx8+9M+l3Rzoup598MEHP5GVlf3OU3c98sgjY7RMhIWFxfO3rQmYge+//3420A70pL/SwOTVoYyj5eTkPjQyMjpNnM1RCjO0lpbWU2xdX19/lba/w8rQ09O7qK2tfZEdQ8unNjY2zKu5B2hiYnKKDHeVrQcGBu6Tl5dno5dgaGg4xc513333cQ/bzs5O+tOf/vT3bJ3K+IzOe4Jigl90dPQOY2Pjs7ScUVVVfYVtDw8Pb2hra5Ol+/gfdn7adoItwcHBzGu5c3l7ew88+uijv71+rufoGs+w61NQUHiXjP/Aj370Iy7IGxgYPKGmpsZdE9Xamx8A/nU4ceKEHF3YJzeC3FcZmKpXLtu2f/9+7m90yHjslTfIS800NTWfZOvsd11d3RBWDgU7JxY86Sfuoi0tLVnvS7YP+76BjMomt4CpqelBGRmZGwbm1MoNA9ONptDDYD0d8bOf/ewjto0hLy9Ph/g9m24+z9zc/MT1cv/q7Oxse+Mebux7HazPGciIZ9l2ppbGx8d/Qvf5MPudyv4bMzBbp9ryV3aAvb29NXtQW7ZsufRPJX0XTE1NyZCBP2YFsoU49H/1jfX39y9k29LS0raz7zo6OmwmFBw+fJgZ+BxbZ7+TkULYOvGzy+Ii9yfUnIGdnJxW2ed1KbiBqvzb7GbpgczcMDAZdIJtu0FX5LGp9NsgeRaoiv+GbSPcQwbhvJq2t1pYWAyz66J9/ubg4GB34x6u73sDNwz8KfukhTNwcnLyw2zfhx9++K/MwGydzs0ZWCAQWLHvdP5/38AMVLU5L7zhAeRF12i5wj7p4j+mp72HbSOPWyK62E77v0nbcPToUTV6ymfZMawc8ijOwB0dHR6Mj68bFEQRzHjczVG13U2e8l/Xf29XUlJ6kt3M448//mZsbGwEOy/bxgxMRmtm5yFK+ltOTo4PPThDMsgf2Xail/1WVlbt12no76RudK+fA5GRkTtI4ewgOclG73MU4eXlVctqKjsX3U86OU0q+/0nP/nJH8nYbMweO88XBmbfqabespGo95AMy1JRUXlSQ0PjPHnW82S4F+jzJeJYZvx76KRT9P0iW8iDn6ML5v6eVyKRtNA+z7N1+s2BcS/zbKYiqIznyMMvkiFGr3sWaN8XaLlobW29xMql5V7G31Tmefp8jj7P0TWcJQOyAej3UHUdo3LOM2+KiYkpTElJMacyL9D3FxMTE/cTl166TlMbmDRk1ZpdN/32c09Pz3Fav0C/vUj3tz8jI0OFrdM5Xqbl51TjXsrOzmZ6/T5WDn1n8WRDRESEPjufu7t7L2edOx1kYDZghhmYedM6bjUCAgL2kMeskPcwr10TkAfmEkfvv/GdaiAXPxiIepIogBbTIiU6iWe/kdeq0DVKb+xD3q5HSdL/ikfruA6KHf8gWcb4mgNxPfcfR8TjGkRXV2n5w//b+wswGXmMrWzatOkHNxZwTUEG/uSxxx773Y3vpHe52QJIQWjQx7WvMvCPf/xjpqY+Y+sUZFnwXsfX4boH/+eN74qKipyBh4aGNJm6+SoD00N4lhTJterqam8KkEL+9nV8CZSNPcOUCxn672y5LicZ7iFP/T2jCaafyfBfUMHq6urGDdfl5I3f1rGOdazj38T/Ba53EvCF4vyvAAAAAElFTkSuQmCC>