<div align="center">

**UNIVERSIDAD CENTRAL DE VENEZUELA**
**FACULTAD DE CIENCIAS**
**ESCUELA DE COMPUTACIÓN**
**CENTRO DE INGENIERÍA DE SOFTWARE Y SISTEMAS – ISYS**

<br>

**TÍTULO**

<br>

Seminario presentado ante la Ilustre Universidad Central de Venezuela por:
**Br. Daniel A. Hernández F.**

**Tutor:**
Prof. Iván Flores V.

Ciudad Universitaria de Caracas, 2026

</div>

---

## Resumen
*(Pendiente)*

## Índice General
*(Pendiente)*

## Capítulo 1
### Planteamiento del Problema
*(Pendiente)*

## Capítulo 2
### Marco Teórico

#### Inteligencia Artificial
Cuando hablamos de Inteligencia Artificial, nos referimos a una disciplina de las Ciencias de la Computación que busca diseñar sistemas capaces de realizar tareas que requieren de la intervención humana, por ejemplo, el reconocimiento de patrones, comprensión y tratamiento del lenguaje e incluso en la toma de decisiones. Inicialmente, los sistemas dependían de reglas explícitamente programadas, sin embargo, debido a la complejidad de los problemas reales surge un subcampo dentro de la inteligencia artificial conocido como Aprendizaje Automático. 

#### Aprendizaje Automático
El Aprendizaje Automático se enfoca en el desarrollo de algoritmos capaces de aprender y extraer características a partir de un conjunto de datos. En lugar de ejecutar instrucciones fijas y explícitamente programadas, un modelo de aprendizaje automático ajusta sus parámetros internos a medida que procesa la información durante su fase de entrenamiento, con el fin de identificar patrones estadísticos. El objetivo principal es conseguir un modelo cuyos resultados sean lo más precisas posible frente a la realidad; visto de otra forma, se busca minimizar la diferencia (o el error) entre el resultado generado por el modelo sobre datos nuevos y el resultado real esperado.

Dependiendo de la naturaleza de los datos y de la forma en que el algoritmo interactúa con ellos, este enfoque se divide fundamentalmente en tres categorías:

*   **Aprendizaje Supervisado:** El modelo se entrena utilizando un conjunto de datos previamente etiquetados. Esto significa que a cada dato de entrada se le asocia de antemano la respuesta correcta o salida deseada. El objetivo del algoritmo es aprender la relación matemática que mapea las entradas con las salidas, permitiéndole generalizar y predecir los resultados correctos cuando se le presenten datos nuevos y desconocidos.
*   **Aprendizaje No Supervisado:** A diferencia del enfoque anterior, aquí se hace uso de datos sin etiquetar. El algoritmo no tiene un resultado "correcto" predefinido que deba imitar, por lo que su objetivo principal es explorar la información para descubrir estructuras ocultas, similitudes o patrones intrínsecos en los datos.
*   **Aprendizaje por Refuerzo:** Este modelo de aprendizaje se basa en la interacción continua de un agente con un entorno dinámico. El modelo no recibe instrucciones explícitas sobre qué acciones tomar, sino que descubre cuáles son las decisiones óptimas a través de un proceso de ensayo y error. Cada acción ejecutada genera un cambio en el entorno y le otorga al agente una recompensa (positiva o negativa). El objetivo del algoritmo es desarrollar una política de actuación que maximice la recompensa acumulativa a largo plazo.

#### Algoritmos de optimización y funciones de pérdida
Sin importar bajo que estrategia de aprendizaje se trabaje, el objetivo principal es que el modelo sea capaz de dar respuestas lo más parecidas posibles a las observadas en la realidad, para medir que tan distantes son estos resultados se emplean las funciones de pérdida, la cuales dependen del modelo y el tipo de problema a resolver. 

Los algoritmos de optimización buscan minimizar no solo la función de pérdida sino el tiempo que toma el entrenamiento del modelo. La función de pérdida genera una superficie n-dimensional, de la cual se busca encontrar el punto mínimo ajustando los parámetros del modelo.

#### Redes Neuronales
Como se mencionó anteriormente, el mundo real se conforma de datos y problemas cuya complejidad supera la capacidad de procesamiento de algoritmos convencionales del aprendizaje automático, esta es la razón por la que surgen los modelos conocidos como redes neuronales, matemáticamente estos modelos constan de un conjunto de datos de entrada, un conjunto de pesos, un conjunto de sesgos y una función de activación. El proceso fundamental resulta en tomar cada uno de los datos del conjunto de entrada (x1, x2, ..., xn), multiplicarlo por un elemento del conjunto de pesos (w1, w2, ..., wn), el cual determina que tan importante es este dato en específico, sumarle un sesgo (b1, b2, ..., bn). Finalmente, al resultado de esta operación se le aplica la función de activación (f) generando así una salida (y). De forma general el proceso es el siguiente:

$$y = f \left(\sum_{i=1}^{n} (w_i \cdot x_i) + b_i\right)$$

Dentro de todos los componentes que mencionamos, la función de activación es el más crítico, ya que, es gracias a la misma que se introduce la no linealidad, funciones como ReLU, Sigmoide o Tangente Hiperbólica permiten que las redes neuronales puedan ajustarse a funciones matemáticas complejas, de lo contrario las redes neuronales solo podrían aproximar rectas. Las redes neuronales se organizan en capas conocidas como:

*   **Capa de entrada:** Recibe los datos sin procesar, como pueden ser valores numéricos que representan los píxeles de una imagen.
*   **Capas ocultas o capas intermedias:** Se encargan del procesamiento y la extracción de características de los datos, cuando una red neuronal posee más de una capa oculta, hablamos de una red neuronal profunda.
*   **Capa de salida:** Toma los datos después de ser procesados y se los lleva al dominio necesario para el contexto del problema, por ejemplo, un valor numérico, una clasificación, los píxeles de una imagen generada.

#### Funciones de Activación
El objetivo de esta función es determinar si una neurona de la red debe activarse o no, dependiendo del resultado obtenido por la suma ponderada de los datos de entrada y así propagar este valor a las capaz siguientes. Como se mencionó anteriormente, la finalidad de la función de activación es romper con el comportamiento linear que tiene la multiplicación de las entradas por sus pesos, de lo contrario las redes neuronales funcionarían de la misma manera que una regresión linear simple, eliminando así su capacidad de aprender patrones complejos en los datos sin importar la cantidad de capas o de neuronas que se utilicen. Dentro de las arquitecturas modernas de redes neuronales, la función de activación más utilizada es la ReLU (abreviatura del inglés Rectified Linear Unit).

#### Función ReLU
Esta función se define tal que:

$$f(x) = \max(0, x)$$

De manera que para cualquier valor de entrada negativo el resultado es 0, en caso contrario el resultado es el mismo valor de la entrada. Esta operación es suficiente para romper la linealidad de la suma ponderada sin cálculos complejos. Es este comportamiento el que permite entender el principal fundamento detrás de las redes neuronales: el Teorema de Aproximación Universal. 

#### Teorema de Aproximación Universal
Establece que una red neuronal con 1 o más capas ocultas y una función de activación no lineal es capaz de aproximar cualquier función continua con cierto grado de precisión siempre que el número de neuronas sea suficiente. Puede verse de manera geométrica, a cada neurona con función de activación ReLU como un segmento de recta capaz de aproximarse a una sección específica de la función real del conjunto de datos, por lo tanto, cuando el número de neuronas aumenta, también lo hacen los segmentos de recta, generando así una aproximación linear por tramos precisa de la distribución de los datos reales.

#### Descenso del gradiente
El gradiente de una función es un vector cuyas componentes son las derivadas parciales respecto a cada una de sus variables e indica en que dirección crece más rápido la función. En nuestro contexto, este vector consta de las derivadas parciales de la función de pérdida respecto a cada parámetro del modelo. En nuestro contexto, el descenso del gradiente es un algoritmo que actualiza los parámetros moviéndose deliberadamente en la dirección opuesta al gradiente. Visto de manera matemática, sea la función de pérdida L, sea θ un parámetro del modelo, se actualizará su valor luego de cada iteración del algoritmo siguiendo la regla:

$$\theta = \theta - \alpha \frac{\partial L}{\partial \theta}$$

Siendo el escalar α la tasa de aprendizaje, este determina la longitud o intensidad del ajuste del modelo en cada iteración, es gracias a este parámetro que el modelo es capaz de converger durante el entrenamiento sin un tiempo excesivo de cómputo. En arquitecturas actuales, que poseen millones o miles de millones de parámetros, calcular el gradiente para cada uno de ellos resulta inviable, para solucionarlo se utiliza el algoritmo conocido como Retropropagación (en inglés Backpropagation).

#### Algoritmo de Backpropagation
Este algoritmo aplica de manera eficiente la regla de la cadena del cálculo diferencial, dividiendo el proceso de aprendizaje de la red neuronal en dos fases:

*   **Propagación hacia adelante (Forward Pass):** Se procesan los datos de entrada capa por capa, calculando las sumas ponderadas, aplicando las funciones de activación hasta generar una predicción final con la que luego se evalúa la función de pérdida.
*   **Propagación hacia atrás (Backward Pass):** El error calculado se propaga de regreso a las capas iniciales usando la regla de la cadena con el fin de calcular cuando contribuyó cada parámetro individual del modelo al resultado obtenido.

El objetivo principal es conocer que tanto cambiará el resultado obtenido por la función de pérdida si modificamos el valor del peso $w_i$, de manera matemática esto se entiende como la derivada parcial de la función de pérdida con respecto a $w_i$ ($\frac{\partial L}{\partial w_i}$). Sin embargo, el error obtenido no depende explícitamente de $w_i$ sino que viene dado por las operaciones realizadas en cada neurona:

*   **Suma ponderada:** Se multiplica el peso por el dato de entrada para luego sumarle el sesgo, este resultado se puede expresar como:
    $$z = w \cdot x + b$$
*   **Función de activación:** El resultado obtenido pasa por la respectiva función de activación, obteniendo así la salida del modelo:
    $$y = f(z)$$
*   **Pérdida:** Se hace uso de la función de activación para calcular que tan alejado está el resultado obtenido ($y$) de la realidad ($\hat{y}$):
    $$L(y, \hat{y})$$

Es por esta dependencia que se utiliza la regla de la cadena, ya que la misma establece que la derivada parcial de la pérdida con respecto al peso se obtiene del producto entre las derivadas parciales de los pasos intermedios: 

$$\frac{\partial L}{\partial w} = \frac{\partial L}{\partial y} \cdot \frac{\partial y}{\partial z} \cdot \frac{\partial z}{\partial w}$$

El algoritmo de retropropagación calcula estas derivadas desde la capa de salida hacia la capa de entrada con el fin de reutilizar valores en capas anteriores, de esta forma se evita tener que calcular las derivadas desde cero para cada una de las neuronas de la red reduciendo considerablemente la complejidad del problema, es gracias a esto que las técnicas de aprendizaje modernas en campos como el aprendizaje profundo sean viables.

El descenso del gradiente tradicional presenta 2 inconvenientes principales al trabajar con funciones muy complejas, el aprendizaje puede estancarse en mínimos locales o puntos de silla presentes en la función de pérdida, por esta razón existen variantes que buscan dar soluciones mediante técnicas estadísticas.

#### Descenso del gradiente por lotes
Se utiliza todo el conjunto de datos de entrenamiento para calcular el gradiente, este método garantiza encontrar el mínimo global de la función de perdida si se inicializan los pesos con los valores correctos, en la práctica, los conjuntos de datos reales se ven representados por superficies muy complejas, por lo tanto, se utilizan algunas de las alternativas siguientes.

#### Descenso del gradiente estocástico (SGD - Stochastic Gradient Descent)
En esta vertiente, el gradiente se calcula solo para un par aleatorio de los datos de entrenamiento elegido de manera aleatoria, de esa forma se introduce ruido al gradiente. Se conoce como época a la cantidad de iteraciones en las que el algoritmo ha utilizado todo el conjunto de datos de entrenamiento. El fundamento matemático detrás de este enfoque es el siguiente:

$$\theta_{t + 1} = \theta_t - \alpha \cdot \sum_{i \in \text{B}} \frac{\partial l_i(\theta_t)}{\partial \theta}$$

Siendo $\text{B}$ el conjunto de índices para los pares de datos de entrada y salida actuales, $l_i$ representa la pérdida con respecto al parámetro $\theta$ y el escalar $\alpha$ es la tasa de aprendizaje que mencionamos anteriormente.

Dentro de las ventajas de este enfoque se destaca su reducción en cuanto a costo computacional, ya que se calculan los gradientes para conjuntos de datos de menor tamaño, el hecho de que las muestras se tomen de forma aleatoria introduce lo que conocemos como ruido al algoritmo, esto hace que su comportamiento no sea tan suave como el descenso del gradiente tradicional, sin embargo, cada iteración contribuye disminuir la pérdida. 

Dado que las muestras se toman sin reemplazo del conjunto de datos de entrenamiento, cada uno de ellos contribuye de forma equitativa al aprendizaje del modelo. Este enfoque tiene un mejor comportamiento al optimizar funciones de pérdida complejas, ya que tiene la capacidad de “escapar” de mínimos locales dentro de la función, además es menos propenso a estancarse en los llamados puntos de silla (puntos en la función en el que el gradiente tiene valor 0). Dado a que el valor de $\alpha$ es fijo, el descenso del gradiente estocástico es incapaz de converger por lo que se suele incluir una rutina en las implementaciones que reduzca el valor de la tasa de aprendizaje a medida que aumenta el número de épocas.

#### Descenso del gradiente por mini-lotes
Este enfoque parte del descenso del gradiente estocástico, sin embargo, no itera sobre 1 sola muestra, en su lugar toma el conjunto de datos de entrenamiento y lo divide en subconjuntos de tamaño fijo, la principal ventaja es que el tamaño del lote se elige teniendo en cuenta la capacidad del hardware que poseen actualmente las GPUs (Unidades de procesamiento gráfico) para procesar datos de forma paralela. 

#### Momentum
Se introduce un término extra a la fórmula que representa una suma ponderada de los gradientes anteriores, este ajuste se refleja de la siguiente manera:

$$m_{t + 1} = \beta \cdot m_t + (1 - \beta) \cdot \sum_{i \in \text{B}} \frac{\partial l_i(\theta_t)}{\partial \theta}$$
$$\theta_{t + 1} = \theta_t - \alpha \cdot m_{t + 1}$$

Siendo $m_t$ el momento (o momentum) del algoritmo calculado de manera recursiva, este término busca almacenar información de gradientes pasados al momento de actualizar el actual, el término $\beta$ se conoce como coeficiente de momento. Esto implica que el gradiente final es una suma ponderada de todos los gradientes anteriores, si los mismos están alineados en el tiempo (es decir, corresponden al mismo mínimo dentro de la función de pérdida) la tasa de aprendizaje va disminuyendo al aumentar el tiempo, por el contrario, si el algoritmo se comporta de manera irregular al momento de calcular los gradientes la tasa de aprendizaje aumenta.

#### Adam
Este enfoque busca solucionar problemas asociados a tener una tasa de aprendizaje estática y global, aquellos parámetros asociados con gradientes elevados sufren un ajuste mayor (lo que puede traer un comportamiento errático o no tan suave como se desea) y viceversa, parámetros que están asociados a gradientes de menor tamaño sufren ajustes no tan significativos.

---

#### Temas Pendientes por Desarrollar:
*   Aprendizaje profundo
*   Modelos Transformers y fundamentos
*   Modelos Generativos
*   Grandes Modelos de Lenguaje
*   Niveles de contexto
*   Agentes
*   Ontologías
*   Mecanismos de generación aumentada por recuperación (RAG)
*   Tecnologías a utilizar