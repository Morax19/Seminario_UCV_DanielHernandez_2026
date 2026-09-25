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

#### Entropía Cruzada
En tareas de clasificación dentro del aprendizaje automático, la medida de error estándar es la Entropía Cruzada. Esta entropía mide la incertidumbre de una distribución de probabilidad y la Entropía Cruzada cuantifica la diferencia entre dos distribuciones de probabilidad: la distribución real (denotada como $y$) y la distribución de probabilidad estimada por el modelo (denotada como $\hat{y}$).

Para un único dato de entrenamiento en un problema con $C$ clases posibles, la Función de Pérdida de Entropía Cruzada se define matemáticamente como:

$$L_{CE} = - \sum_{i=1}^{C} y_i \log(\hat{y}_i)$$

#### Redes Neuronales
Como se mencionó anteriormente, el mundo real se conforma de datos y problemas cuya complejidad supera la capacidad de procesamiento de algoritmos convencionales del aprendizaje automático, esta es la razón por la que surgen los modelos conocidos como redes neuronales, matemáticamente estos modelos constan de un conjunto de datos de entrada, un conjunto de pesos, un conjunto de sesgos y una función de activación. El proceso fundamental resulta en tomar cada uno de los datos del conjunto de entrada ($x_1, x_2, \dots, x_n$), multiplicarlo por un elemento del conjunto de pesos ($w_1, w_2, \dots, w_n$), el cual determina que tan importante es este dato en específico, sumarle un sesgo ($b_1, b_2, \dots, b_n$). Finalmente, al resultado de esta operación se le aplica la función de activación ($f$) generando así una salida ($y$). De forma general el proceso es el siguiente:

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

#### Función Softmax
A diferencia de la función ReLU, que se utiliza en las capas ocultas para introducir no linealidad, la función Softmax es utilizada en la capa de salida de las redes neuronales diseñadas para problemas de clasificación.

Su propósito fundamental es tomar un vector de números reales arbitrarios generados por la última capa lineal de la red y transformarlos en una distribución de probabilidad. Dado un vector de entrada $z$ cuya dimensión $K$ (donde $K$ representa el número total de clases), la función Softmax calcula el valor para la clase $i$ mediante la siguiente ecuación:

$$\text{Softmax}(z)_i = \frac{e^{z_i}}{\sum_{j=1}^{K} e^{z_j}}$$

Al elevar el número base $e$ a la potencia de cada componente, se garantiza que todos los valores resultantes sean estrictamente positivos. Además, dada la naturaleza de la función exponencial, si una componente es ligeramente mayor que los demás resultará en un valor exponencial significativamente más grande, de esa forma la red tiende a destacar su predicción principal. 

Finalmente, al dividir cada valor exponencial por la suma de todos los valores exponenciales del vector, cada componente del vector resultante de salida estará dentro del el rango $(0, 1)$ y la sumatoria total de todas las componentes será exactamente igual a $1$. De este modo, la salida de la neurona se puede interpretar estadísticamente como la probabilidad de que la entrada pertenezca a una clase específica, cumpliendo con los axiomas de probabilidad.

#### Descenso del gradiente
El gradiente de una función es un vector cuyas componentes son las derivadas parciales respecto a cada una de sus variables e indica en que dirección crece más rápido la función. En nuestro contexto, este vector consta de las derivadas parciales de la función de pérdida respecto a cada parámetro del modelo. En nuestro contexto, el descenso del gradiente es un algoritmo que actualiza los parámetros moviéndose deliberadamente en la dirección opuesta al gradiente. Visto de manera matemática, sea la función de pérdida $L$, sea $\theta$ un parámetro del modelo, se actualizará su valor luego de cada iteración del algoritmo siguiendo la regla:

$$\theta_{t+1} \leftarrow \theta_t - \alpha \frac{\partial L}{\partial \theta_t}$$

Siendo el escalar $\alpha$ la tasa de aprendizaje, este determina la longitud o intensidad del ajuste del modelo en cada iteración, es gracias a este parámetro que el modelo es capaz de converger durante el entrenamiento sin un tiempo excesivo de cómputo. En arquitecturas actuales, que poseen millones o miles de millones de parámetros, calcular el gradiente para cada uno de ellos resulta inviable, para solucionarlo se utiliza el algoritmo conocido como Retropropagación (en inglés Backpropagation).

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

$$\theta_{t+1} \leftarrow \theta_t - \alpha \cdot \sum_{i \in B} \frac{\partial l_i(\theta_t)}{\partial \theta}$$

Siendo $B$ el conjunto de índices para los pares de datos de entrada y salida actuales, $l_i$ representa la pérdida con respecto al parámetro $\theta$ y el escalar $\alpha$ es la tasa de aprendizaje que mencionamos anteriormente.

Dentro de las ventajas de este enfoque se destaca su reducción en cuanto a costo computacional, ya que se calculan los gradientes para conjuntos de datos de menor tamaño, el hecho de que las muestras se tomen de forma aleatoria introduce lo que conocemos como ruido al algoritmo, esto hace que su comportamiento no sea tan suave como el descenso del gradiente tradicional, sin embargo, cada iteración contribuye disminuir la pérdida. 

Dado que las muestras se toman sin reemplazo del conjunto de datos de entrenamiento, cada uno de ellos contribuye de forma equitativa al aprendizaje del modelo. Este enfoque tiene un mejor comportamiento al optimizar funciones de pérdida complejas, ya que tiene la capacidad de “escapar” de mínimos locales dentro de la función, además es menos propenso a estancarse en los llamados puntos de silla (puntos en la función en el que el gradiente tiene valor 0). Dado a que el valor de $\alpha$ es fijo, el descenso del gradiente estocástico es incapaz de converger por lo que se suele incluir una rutina en las implementaciones que reduzca el valor de la tasa de aprendizaje a medida que aumenta el número de épocas.

#### Descenso del gradiente por mini-lotes
Este enfoque parte del descenso del gradiente estocástico, sin embargo, no itera sobre 1 sola muestra, en su lugar toma el conjunto de datos de entrenamiento y lo divide en subconjuntos de tamaño fijo, la principal ventaja es que el tamaño del lote se elige teniendo en cuenta la capacidad del hardware que poseen actualmente las GPUs (Unidades de procesamiento gráfico) para procesar datos de forma paralela. 

#### Momentum
Se introduce un término extra a la fórmula que representa una suma ponderada de los gradientes anteriores, este ajuste se refleja de la siguiente manera:

$$m_{t+1} \leftarrow \beta \cdot m_t  + (1 - \beta) \cdot \sum_{i \in B} \frac{\partial l_i(\theta_t)}{\partial \theta}$$
$$\theta_{t+1} \leftarrow \theta_t  - \alpha \cdot m_{t+1}$$

Siendo $m_t$ el momento (o momentum) del algoritmo calculado de manera recursiva, este término busca almacenar información de gradientes pasados al momento de actualizar el actual, el término $\beta$ se conoce como coeficiente de momento. Esto implica que el gradiente final es una suma ponderada de todos los gradientes anteriores, si los mismos están alineados en el tiempo (es decir, corresponden al mismo mínimo dentro de la función de pérdida) la tasa de aprendizaje va disminuyendo al aumentar el tiempo, por el contrario, si el algoritmo se comporta de manera irregular al momento de calcular los gradientes la tasa de aprendizaje aumenta.

#### Adam
Este algoritmo fue presentado en el año 2014, en el artículo: "Adam: A Method for Stochastic Optimization” por Diederik P. Kingma y Jimmy Ba, es el estándar actual para el entrenamiento de modelos complejos. La principal limitante de los algoritmos anteriores es que aplican una valor estático y global para la tasa de aprendizaje $\alpha$ para actualizar los parámetros de la red, este enfoque aplica la lógica del Momentum junto a técnicas de escalado de gradientes para calcular tasas de aprendizaje adaptativas asociadas a cada peso sináptico.

Para ello, el algoritmo mantiene 2 momentos estadísticos de los gradientes ya calculados:

$$m_{t+1} \leftarrow \beta \cdot m_t + (1 - \beta) \cdot \sum_{i \in B} \frac{\partial l_i(\theta_t)}{\partial \theta}$$
$$v_{t+1} = \gamma \cdot v_t + (1 - \gamma) \cdot \sum_{i \in B} \left(\frac{\partial l_i(\theta_t)}{\partial \theta}\right)^2$$

Siendo $\beta$ y $\gamma$ ambos coeficientes de momento para los vectores $m_t$ y $v_t$. Dado que emplear el momento consta de una suma ponderada de los gradientes anteriores, en la primera iteración este valor inicia en 0 y va aumentando muy lentamente, esto da como resultado un comportamiento errático del algoritmo en las etapas iniciales, para mitigar esto, se realiza el siguiente ajuste:

$$\hat{m}_{t+1} \leftarrow \frac{m_{t+1}}{1 - \beta^{t+1}}$$
$$\hat{v}_{t+1} \leftarrow \frac{v_{t+1}}{1 - \gamma^{t+1}}$$

A medida que aumenta el número de iteraciones aumenta, el denominador acerca su valor a 1 por lo que el ajuste desaparece y se mantiene la lógica original. Finalmente, la regla de actualización de parámetros es la siguiente:

$$\theta_{t+1} \leftarrow \theta_t  - \alpha \cdot \frac{\hat{m}_{t+1}}{\sqrt{\hat{v}_{t+1}} + \epsilon}$$

#### Aprendizaje profundo
Dado el aumento de la complejidad de los problemas computacionales, especialmente en áreas donde los datos no son estructurados, como la visión artificial y el procesamiento de lenguaje natural, las redes neuronales demostraron limitaciones claras. Es por ello, por el enorme aumento en capacidad de cómputo en los últimos años y finalmente por la disponibilidad de grandes cantidades de datos que surge dentro del Aprendizaje Automático lo que hoy día llamamos Aprendizaje Profundo. Esta área se caracteriza por el entrenamiento y uso de redes neuronales que poseen múltiples capas ocultas.

A diferencia del Aprendizaje Automático, la red neuronal procesa los datos crudos, como los valores RGB de los píxeles de una imagen o los vectores de palabras en un texto y descubre por sí misma qué características y relaciones son relevantes que minimicen la función de pérdida. Para conseguir esta capacidad, se emplea una arquitectura de aprendizaje jerárquico, a medida que la información fluye a través de las sucesivas capas ocultas de la red, los datos sufren transformaciones no lineales cada vez más abstractas:

*   **Capas iniciales:** Tienen la función de detectar características matemáticas de bajo nivel.
*   **Capas intermedias:** Combinan las características halladas en las capas iniciales para formas representaciones más complejas.
*   **Capas finales:** Abstraen el conocimiento al más alto nivel, igualando las representaciones al contexto del usuario.

Esta capacidad del Aprendizaje Profundo para extraer y modelar jerarquías complejas a partir de datos no estructurados dio pie a lo que se conoce como Inteligencia Artificial Generativa y, posteriormente, para la evolución hacia arquitecturas especializadas en secuencias, como los Transformers.

#### Modelos Generativos
Gran parte de los avances tempranos en el Aprendizaje Profundo se centraron en modelos discriminativos cuyo objetivo principal es encontrar el límite de decisión que separa diferentes clases de datos, por ejemplo, clasificar si una imagen corresponde a un perro o a un gato. Estadísticamente, estos modelos aprenden la distribución de probabilidad condicional $P(Y|X)$, que estima la probabilidad de que un valor observado $X$ pertenezca a una clase $Y$. 

Por otro lado, dentro del aprendizaje no supervisado se busca estudiar y desarrollar modelos capaces de generar nuevos datos con características estadísticamente similares a los datos usados durante el entrenamiento, este tipo de modelos se conocen como modelos generativos. En lugar de centrarse en lo que diferencia a una clase de otra, los modelos generativos buscan comprender y modelar la distribución de probabilidad presente en el conjunto de datos completo.

Una característica de las redes neuronales profundas es que buscan mapear información de alta dimensionalidad hacia representaciones matemáticas más compactas, conocidas como el espacio latente. Este espacio codifica de manera comprimida las características fundamentales, la semántica y las variaciones estructurales de los datos de entrenamiento. Para la generación de nuevos puntos de datos se realiza un proceso de muestreo estadístico en el que el algoritmo selecciona un punto o vector del espacio latente y lo decodifica, generando instancias de datos nuevas pero que pertenecen a la misma distribución de probabilidad de los datos originales. 

#### Aprendizaje Auto-supervisado
Para modelar representaciones complejas como el lenguaje humano, los modelos generativos dependen fuertemente del aprendizaje auto-supervisado que, a diferencia del aprendizaje supervisado clásico, genera sus propias etiquetas partiendo de la estructura de los datos de entrada. Un comportamiento presente en estos modelos que procesan secuencias de datos relacionados entre sí es que el algoritmo oculta una parte de la información para forzar a la red neuronal a predecir la porción faltante basándose exclusivamente en el contexto restante.

El error matemático entre la predicción del modelo y el dato original realimenta el algoritmo de retropropagación para ajustar los pesos, de esta forma los modelos generativos pueden escalar de forma masiva.

#### Modelos Transformers y fundamentos
Originalmente, el modelo más utilizado en tareas de procesamiento de secuencias (como el Procesamiento de Lenguaje Natural) eran las Redes Neuronales Recurrentes (RNN) y sus variantes, como las redes de Memoria a Corto y Largo Plazo (LSTM). Estas arquitecturas procesaban la información de manera secuencial, es decir, para procesar el token en la posición $t$, era necesario haber calculado previamente el estado oculto de token en la posición $t-1$, lo que presenta dos problemas fundamentales: no es posible realizar el cómputo en paralelo y provoca la pérdida de información en dependencias a largo plazo debido al desvanecimiento del gradiente.

En el año 2017, se publica el artículo "Attention Is All You Need" por investigadores de Google (Vaswani et al., 2017), en el que se introduce la arquitectura Transformer. La característica principal de esta arquitectura es que prescinde totalmente de la recurrencia y la convolución, basándose de manera exclusiva en un mecanismo denominado autoatención, lo cual permite procesar todos los elementos de una secuencia de manera simultánea.

**El Mecanismo de Autoatención**
El mecanismo de autoatención permite a un modelo evaluar, durante el procesamiento de un token específico, la importancia y relación semántica que tienen todos los demás tokens de la secuencia de entrada respecto a él, sin importar la distancia física que los separe.

Para lograr esto computacionalmente, el modelo toma el vector numérico que representa a cada token (conocido como embedding) y lo proyecta geométricamente en tres subespacios distintos multiplicándolo por tres matrices de pesos diferentes ($W^Q, W^K, W^V$), las cuales se ajustan dinámicamente durante el entrenamiento. Estas multiplicaciones generan tres nuevos vectores para cada token:

*   **Vector Query (Q - Consulta):** Representa lo que el token actual está buscando en el resto de la secuencia para comprender su propio contexto.
*   **Vector Key (K - Clave):** Representa el contenido del token, cumple la función de etiqueta de identificación o índice.
*   **Vector Value (V - Valor):** Representa el contenido semántico o la representación real del token que será propagada hacia las siguientes capas de ser relevante.

Esta terminología viene dada de las bases de datos, donde se realiza una consulta (Query) y se compara contra las claves (Keys) almacenadas para extraer los valores (Values) asociados.

Para calcular qué tanta "atención" debe prestarle un token al resto, la arquitectura Transformer utiliza la Atención de Producto Punto Escalado (Scaled Dot-Product Attention), el cual es un proceso matemático definido tal que:

1.  Se calcula el producto punto entre la matriz de consultas $Q$ y la matriz transpuesta de claves $K^T$. Dado que el producto punto es una medida de similitud geométrica; si dos vectores apuntan en la misma dirección, el resultado es alto, lo que indica una fuerte relación semántica entre ambos tokens.
2.  Este resultado se divide entre la raíz cuadrada de la dimensión de los vectores clave $D_k$. Este proceso busca evitar que los resultados crezcan excesivamente, lo cual empujaría a la función softmax hacia regiones con gradientes muy pequeños, ralentizando el aprendizaje.
3.  Se aplica la función softmax a lo largo de las filas para normalizar los puntajes, convirtiéndolos en una distribución de probabilidad.
4.  Finalmente, los pesos probabilísticos se multiplican por la matriz de valores $V$. Si una palabra no es relevante para el contexto actual, su peso será cercano a cero.

Matemáticamente, este mecanismo se condensa en la ecuación central del Transformer:

$$SelfAttention(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{D_k}}\right)V$$

**Atención Multicabezal y Codificación Posicional**
Aplicar solo un mecanismo de atención presenta un problema: al calcular un único conjunto de pesos mediante la función softmax, el modelo se ve forzado a promediar diferentes tipos de relaciones (sintácticas, semánticas, estructurales), causando que información de contextos complejos se pierda. Como solución se introduce la Atención Multicabezal.

En lugar de aplicar la función de atención una sola vez sobre los vectores originales de alta dimensionalidad, la arquitectura proyecta linealmente las Consultas $Q$, Claves $K$ y Valores $V$ en una cantidad finita de subespacios de representación independientes.

Sobre cada uno de estos subespacios, el modelo calcula la Atención, dándole al algoritmo la libertad de especializarse en abstraer diferentes dependencias. Habiendo generado sus respectivas matrices de atención, los vectores de dimensión resultantes se concatenan secuencialmente restaurando la matriz original. Finalmente, esta se multiplica por una matriz de pesos de salida, encargada de integrar las características descubiertas por los diferentes subespacios antes de propagar el resultado hacia la siguiente capa de la red neuronal.

Por otro lado, dado que el procesamiento de los Transformers se realiza de forma paralela, el modelo desconoce el orden secuencial de los tokens procesados. La solución consiste en añadir una Codificación Posicional antes de aplicar el mecanismo de atención. Se suma un vector con funciones matemáticas deterministas (senos y cosenos de distintas frecuencias) al embedding original de la entrada, otorgándole a cada token una marca única dentro de la secuencia.

#### Grandes Modelos de Lenguaje
Los Grandes Modelos de Lenguaje (siglas en inglés LLMs provenientes de Large Language Models) representan la evolución y escalamiento masivo de la arquitectura Transformer. A diferencia del modelo original, que se especializaba en la traducción de idiomas gracias a su estructura Codificador-Decodificador (Encoder-Decoder), los LLMs generativos modernos se construyen casi exclusivamente utilizando una arquitectura de solo decodificado.

Al eliminar el Codificador, el modelo centra exclusivamente en una tarea auto-supervisada: el modelado de lenguaje iterativo.

**Generación Autorregresiva y Atención Causal**
El núcleo operativo de un LLM consiste en la predicción del siguiente elemento en una secuencia. Para lograr la generación de texto coherente, los LLMs implementan una variante crítica en su arquitectura denominada Autoatención Enmascarada (Masked Self-Attention). Durante el entrenamiento, el modelo recibe secuencias completas de texto, por lo que, para obligarlo a predecir el token $t+1$ en lugar de simplemente fijarse en la respuesta, se aplica el mecanismo de atención causal, el cual aplica una máscara matemática sobre la matriz de atención antes de aplicar la función softmax.

Este mecanismo garantiza que, para procesar y predecir el token en la posición $t+1$, el modelo solo pueda calcular los pesos de atención sobre los tokens anteriores, bloqueando cualquier flujo de información proveniente de los tokens futuros. Matemáticamente, el modelo aprende y aproxima la siguiente distribución de probabilidad condicional:

$$P(x_{t+1} | x_1, x_2, \dots, x_t)$$

Habiendo finalizado el entrenamiento, la tarea de generación de texto se vuelve un autorregresiva, ya que, cuando el LLM predice el siguiente token, este se concatena a la secuencia de entrada original, y todo el contexto actualizado vuelve a pasar por la red neuronal para predecir el subsiguiente elemento.

Durante su ciclo de vida, un LLM moderno pasa por el proceso de preentrenamiento en el cual el modelo procesa cuerpos de texto de gran tamaño extraídos de internet. Mediante algoritmos como Adam, se ajustan los miles de millones de parámetros para minimizar la pérdida de entropía cruzada en la predicción de tokens. Es así como el modelo extrae representaciones latentes profundas, internalizando la gramática, la lógica básica y un vasto conocimiento general del mundo.

**Modelos de Código Abierto y Ejecución Local**
En el contexto de los LLMs, suele confundirse el término “open-source” con “open-weights”, ya que en lugar de compartir el código fuente de la arquitectura del modelo, se liberan los pesos paramétricos resultantes del entrenamiento, de esta manera se facilita el acceso a LLMs altamente capaces, entre los cuales destacan familias de modelos como Llama de Meta o Phi de Microsoft (Touvron et al., 2023).

Estos modelos abiertos permiten el despliegue y la ejecución local de la inferencia en hardware privado. La principal ventaja de esto consiste en eliminar la dependencia de APIs de terceros, además de otorgar al usuario control sobre latencias y, primordialmente, asegura la privacidad absoluta y la confidencialidad de los datos analizados por el sistema.

#### Ventana de contexto e inferencia local
La cantidad de información que un LLM puede observar, recordar y procesar simultáneamente en una sola iteración de inferencia está estrictamente limitada por un parámetro arquitectónico conocido como Ventana de Contexto.

Esta se mide en tokens y dicta la capacidad de memoria a corto plazo del modelo, si alguna información queda fuera de esta ventana entonces no existe para el algoritmo en el momento de generar una respuesta. A medida que un modelo analiza un conjunto de documentos, surge la necesidad de incrementar la ventana de contexto. Sin embargo, procesar un gran número de tokens simultáneamente representa un aumento de complejidad cuadrática dada la naturaleza del mecanismo de autoatención.

Como se explicó en la sección donde se explica la arquitectura Transformer, el cálculo de atención requiere realizar el producto punto entre la matriz de Consultas y la matriz de Claves. Si una secuencia tiene una longitud de $N$ tokens, la matriz de pesos de atención tiene un tamaño de $N \times N$, causando que tanto el número de operaciones de punto flotante como el consumo de memoria crezcan de forma proporcional a $\mathcal{O}(N^2)$.

Esto es especialmente importante cuando tratamos con modelos ejecutados de forma local en los que el hardware está restringido por la memoria de las GPUs disponibles. Intentar cargar miles de tokens en la ventana de contexto para analizar múltiples documentos agota rápidamente los recursos del sistema, provocando errores de desbordamiento de memoria o degradando el rendimiento de la inferencia.

Incluso si el hardware dispone de la capacidad para procesar ventanas de contexto amplias, los LLMs sufren de una degradación en su capacidad de recuperación de información conocida como el fenómeno "Perdido en el medio".

Recientes investigaciones sobre el comportamiento de atención en los LLMs han demostrado que los modelos exhiben un rendimiento sobresaliente al recuperar y razonar sobre información que se encuentra al principio de la secuencia o al final de esta. Sin embargo, este rendimiento disminuye cuando el modelo intenta extraer hechos estructurados cuando la información relevante está sepultada en el medio de un texto extenso.

En el contexto de esta investigación, este comportamiento representa una barrera para la extracción de entidades y el llenado de esquemas a partir de documentos no estructurados. Introducir la información completa de un área sin importar la fuente, ya sea un libro, un manual técnico o una transcripción de audio en la ventana de contexto es computacionalmente costoso para entornos locales, además de que reduce la fiabilidad y precisión de los datos extraídos.

Para superar estas complicaciones, es necesario implementar arquitecturas que permitan filtrar y obtener el contexto necesario para generar una respuesta en lugar de intentar inyectar todo el contexto en cada petición al modelo. Este es el fundamento que motiva la adopción de arquitecturas de Generación Aumentada por Recuperación (RAG) y la Representación Estructurada del Conocimiento.

#### Bases de Datos Relacionales y Bases de Datos Vectoriales
Para comprender como el modelo recupera la información, debemos establecer la diferencia entre el almacenamiento de datos clásico y vectorial.

Una Base de Datos relacional almacena la información de manera tabular, estructurada en filas y columnas. Para recuperar datos en estos sistemas se utilizan búsquedas de coincidencia exacta. Esto quiere decir que, si se busca el término "automóvil", la base de datos relacional solo devolverá registros que contengan exactamente esa secuencia, ignorando por completo sinónimos o contextos semánticos.

Por otro lado, una Base de Datos Vectorial es un sistema de almacenamiento diseñado para manejar datos de alta dimensionalidad. En lugar de guardar tablas de texto plano, se almacenan arreglos continuos conocidos como Embeddings. A diferencia de las bases de datos tradicionales, estas permiten realizar búsquedas semánticas, en el que no se buscan términos exactos sino que se buscan vectores en el espacio multidimensional, permitiendo comprender que términos como "automóvil" y "vehículo" apuntan al mismo concepto lógico.

#### Mecanismos de generación aumentada por recuperación (RAG)
El estándar actual para darle conocimiento externo, dinámico y verificable a un LLM es el proceso conocido como Generación Aumentada por Recuperación (RAG, por sus siglas en inglés: Retrieval-Augmented Generation).

El paradigma RAG fue introducido formalmente por Lewis et al. (2020), el mismo no busca que el modelo memorice toda una base de conocimiento durante su preentrenamiento y así reflejarlo en sus pesos, ni intenta inyectar documentos completos en una única ventana de contexto dentro de cada petición. En su lugar, acopla el LLM con una base de datos vectorial para la recuperación de información.

El objetivo es recuperar únicamente los fragmentos de información relevantes para la consulta actual del usuario, y proveerlos al modelo como contexto temporal. Este proceso modular se divide tres fases:

1.  **Indexación y Representación Vectorial:** Antes de que el modelo pueda interactuar con el conocimiento externo, la información debe ser estructurada. Los documentos originales se dividen en fragmentos de texto más pequeños y manejables (conocidos en inglés como chunks), que luego se pasan a un modelo de incrustación (Embedding Model) que los transforma en un vector numérico denso de alta dimensionalidad que encapsula el significado semántico del texto. Finalmente, estos se almacenan en una base de datos vectorial.
2.  **Recuperación:** Cuando el sistema recibe una consulta de entrada, esta se transforma utilizando el mismo modelo de embedding, generando un "vector de consulta". El sistema de recuperación calcula entonces la similitud geométrica entre el vector de consulta y todos los vectores almacenados en la base de datos. El algoritmo extrae y devuelve los fragmentos que tengan la mayor cercanía, lo que se traduce en la información semánticamente más relevante para resolver la tarea.
3.  **Generación Aumentada:** Finalmente, los fragmentos de texto recuperados se concatenan estructuradamente junto con la petición original del usuario. Esta nueva petición se inyecta en la ventana de contexto del LLM que, al contar con la información precisa, filtrada y altamente relevante, utiliza su mecanismo de autoatención para analizar el contexto provisto y generar una respuesta fundamentada. Este proceso reduce la probabilidad de generar alucinaciones.

#### Agentes
El concepto de Agente en la Inteligencia Artificial moderna transforma al LLM de un simple generador de texto en un motor de razonamiento capaz de interactuar con su entorno. Un agente impulsado por un LLM se define formalmente como un sistema autónomo que utiliza el modelo de lenguaje como su unidad de control central para percibir el contexto, planificar una secuencia de acciones, ejecutar herramientas externas y evaluar los resultados para alcanzar un objetivo (Wang et al., 2023).

Desde el punto de vista de arquitectura, un agente está compuesto de tres pilares:
1.  **Planificación y Razonamiento:** Se entiende como la capacidad de descomponer una tarea compleja en subtareas más pequeñas. Para conseguirlo se implementan técnicas de razonamiento explícito como Chain-of-Thought o ReAct, donde el modelo genera verbalmente sus pensamientos antes de tomar una decisión.
2.  **Memoria:** Está divido en memoria a corto plazo, que corresponde al contexto de la conversación actual manejado por la ventana de contexto y memoria a largo plazo, almacenamiento y recuperación de información histórica, generalmente implementado mediante bases de datos vectoriales.
3.  **Uso de Herramientas (Tool-use o Function Calling):** Es la característica que separa a un agente de un LLM tradicional, el modelo es entrenado para comprender firmas de funciones como APIs, intérpretes de código, motores de búsqueda. Cuando el modelo determina que carece de la información necesaria para responder, detiene la generación de texto, emite un comando estructurado para invocar una herramienta externa, espera el resultado de dicha ejecución y luego integra esa nueva información en su razonamiento.

#### RAG Agéntico
Si bien el proceso de Generación Aumentada por Recuperación es efectivo para mitigar alucinaciones y superar el límite de contexto, presenta una limitación estructural: es un proceso lineal y determinista que consta de recuperar, inyectar y generar. En el Naive RAG, el sistema siempre realiza una búsqueda vectorial en la base de datos, independientemente de si la consulta del usuario lo requiere, y el LLM está forzado a responder basándose en los fragmentos recuperados, incluso si estos resultan irrelevantes o insuficientes.

Se propone como mejora lo que se conoce como el RAG Agéntico. Esta arquitectura fusiona las capacidades de razonamiento y uso de herramientas de un agente autónomo con el sistema de recuperación de información.

En lugar de ejecutar una búsqueda vectorial de manera obligatoria y secuencial, el sistema provee al LLM de la base de datos vectorial como si fuera una herramienta a su disposición. El flujo operativo se convierte en:

1.  **Evaluación de necesidad:** Al recibir una consulta, el agente evalúa si puede responder con su conocimiento interno o si requiere información externa. Si decide que necesita contexto, formula una consulta optimizada específicamente a la base de datos.
2.  **Evaluación de relevancia:** Una vez que la base de datos devuelve los fragmentos de información, el agente actúa como un filtro, ya que, lee los fragmentos y determina si realmente contienen la respuesta a la pregunta.
3.  **Iteración:** Si el agente determina que la información recuperada es insuficiente o tangencial, es capaz de decidir de forma autónoma reformular su consulta de búsqueda y ejecutar la herramienta nuevamente, iterando este proceso hasta recopilar el contexto necesario o alcanzar un límite de intentos.
4.  **Síntesis:** Solo cuando el agente está satisfecho con la relevancia del contexto recuperado, procede a sintetizar la respuesta estructurada final.

Este comportamiento iterativo e introspectivo permite a las arquitecturas de RAG Agéntico resolver consultas complejas que requieren saltos lógicos o agregación de información dispersa en múltiples documentos (Gao et al., 2023). Al proporcionarle al modelo la capacidad de evaluar la calidad de su propio contexto, se incrementa dramáticamente la precisión y la robustez de la extracción de información estructurada.

#### Representación de Conocimiento
Para que la información recuperada e interpretada por un modelo autónomo posea utilidad computacional, no es suficiente generar respuestas en lenguaje natural. Cuando se realizan soluciones orientadas a la automatización de procesos, al llenado de bases de datos, generación de código o interconexión con otros sistemas, se deben estructurar los resultados bajo un formato determinista e interoperable.

La Representación del Conocimiento es una rama de la Inteligencia Artificial tradicional cuyo objetivo es diseñar formalismos que permitan a un sistema informático almacenar, procesar y razonar sobre información del mundo real. A diferencia de las representaciones latentes y distribuidas que emplea una red neuronal, que son inescrutables para los sistemas informáticos convencionales, la representación del conocimiento exige que la información sea explícita, simbólica y estructurada (Russell y Norvig, 2020; Davis, Shrobe y Szolovits, 1993).

#### Ontologías Computacionales
El estándar más riguroso para la estructuración de conocimiento es la Ontología. En el contexto de las ciencias de la computación, la misma se define como una "especificación explícita y formal de una conceptualización compartida" (Studer et al., 1998).

De manera práctica, una ontología proporciona un vocabulario controlado y una estructura lógica para un dominio específico, definiendo:
*   **Entidades:** Conceptos fundamentales que existen en un dominio.
*   **Propiedades:** Las características que describen a dichas entidades.
*   **Relaciones:** Las conexiones semánticas y jerárquicas entre las entidades.
*   **Restricciones lógicas:** Reglas de validación que gobiernan los datos.

Al incluir una ontología claramente definida en los ajustes del modelo, se delimita su espacio de razonamiento, de esa forma el agente deja de ser un generador de texto libre y asume el rol de un clasificador y extractor de entidades que debe mapear la información no estructurada para cumplir con las reglas definidas por la ontología.

#### Grafos de Conocimiento (Knowledge Graphs)
Desde la perspectiva de las estructuras de datos, un Grafo de Conocimiento es una red semántica que representa topológicamente la información. Matemáticamente, se define como un grafo dirigido $G=(V,E)$, en el que un conjunto de vértices $V$ representan a las entidades individuales definidas en la ontología y el conjunto de aristas $E$ representan las relaciones lógicas y semánticas que conectan a dichas entidades (Ehrlinger y Wöß, 2016).

La unidad atómica de información dentro de un grafo de conocimiento se define como tripleta semántica y se define siguiendo la estructura: (Sujeto, Predicado, Objeto).

**Sinergia entre Grafos de Conocimiento y LLMs (GraphRAG)**
En las arquitecturas RAG, el sistema recupera fragmentos de texto basándose en la similitud espacial. Sin embargo, cuando se presentan consultas que requieren conectar información de múltiples fuentes este enfoque tiende a disminuir su eficacia.

Una alternativa que busca dar solución a este comportamiento consiste en utilizar agentes basados en LLMs para construir y consultar Grafos de Conocimiento, dando lugar al paradigma GraphRAG (Generación Aumentada por Recuperación basada en Grafos). Ahora bien, la construcción de este grafo puede seguir dos enfoques principales:

1.  **Extracción Abierta:** Se le otorga al modelo libertad total para analizar el texto y definir desde las entidades hasta sus relaciones basándose en su interpretación probabilística. Este enfoque resulta útil para el análisis exploratorio de datos desconocidos o bien para generar un boceto inicial, sin embargo, resulta ineficiente para implementaciones funcionales, ya que, dependiendo del rendimiento del modelo puede generar grafos altamente ruidosos, con sinónimos para una misma clase y relaciones ambiguas, imposibilitando la interoperabilidad con bases de datos estructuradas.
2.  **Extracción Cerrada:** En este paradigma, se define la Ontología (clases, atributos y tipos de relaciones) antes de la ejecución del modelo. Esta estructura predefinida se inyecta en los requerimientos o ajustes del sistema, estableciendo límites en el razonamiento del LLM.

Bajo el paradigma de extracción cerrada, el modelo actúa estrictamente como un mapeador de funciones. Su tarea es identificar instancias reales en texto no estructurado y ajustarlas dentro de las estructuras lógicas ya definidas en lugar de descubrir cómo funciona el dominio.

De esta forma, la ontología actúa como un "molde", asegurando que el grafo de conocimiento resultante posea una estructura canónica, determinista y matemáticamente predecible (Ehrlinger y Wöß, 2016).

Esto dota al LLM de un contexto estructurado y explícitamente definido, lo que incrementa su precisión al momento de generar una respuesta, además permite rastrear la procedencia exacta de cada afirmación.

---

#### Temas Pendientes por Desarrollar:
*   Tecnologías a utilizar

#### Referencias
*   https://arxiv.org/pdf/1412.6980 (Adam: A Method For Stochastic Optimization – Diederik P. Kingma & Jimmy Lei Ba.)
*   https://udlbook.github.io/udlbook/ (Understanding Deep Learning – Simon J. D. Prince.)
*   https://www.deeplearningbook.org/ (Goodfellow, I., Bengio, Y., & Courville, A. (2016). Deep Learning. MIT Press.)
*   https://ai.stanford.edu/~ang/papers/nips01-discriminativegenerative.pdf (Ng, A. Y., & Jordan, M. I. (2002). On discriminative vs. generative classifiers: A comparison of logistic regression and naive bayes.)
*   https://arxiv.org/pdf/1706.03762 (Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is all you need.)
*   https://www.bioinf.jku.at/publications/older/2604.pdf (Hochreiter, S., & Schmidhuber, J. (1997). Long short-term memory. Neural computation, 9(8), 1735-1780)
*   http://jalammar.github.io/illustrated-transformer/ (Alammar, J. (2018). The Illustrated Transformer. Visualizing machine learning one concept at a time.)
*   https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf (Radford, A., Narasimhan, K., Salimans, T., & Sutskever, I. (2018). Improving language understanding by generative pre-training.)
*   https://arxiv.org/pdf/2005.14165 (Brown, T., Mann, B., Ryder, N., Subbiah, M., et al. (2020). Language models are few-shot learners. En Advances in neural information processing systems (Vol. 33).)
*   https://arxiv.org/pdf/2302.13971 (Touvron, H., Lavril, T., Izacard, G., Martinet, X., et al. (2023). Llama: Open and efficient foundation language models. arXiv preprint arXiv:2302.13971.)
*   https://proceedings.neurips.cc/paper/2020/file/6b493230205f780e1bc26945df7481e5-Paper.pdf (Lewis, P., Perez, E., Piktus, A., Petroni, F., Karpukhin, V., Goyal, N., ... & Kiela, D. (2020). Retrieval-augmented generation for knowledge-intensive NLP tasks. En Advances in Neural Information Processing Systems (Vol. 33, pp. 9459-9474).)
*   https://www.mpgcamb.com/wp-content/uploads/2024/12/Abraham-Silberschatz-Henry-F.-Korth-S.-Sudarshan-Database-System-Concepts-McGraw-Hill-Education-2019.pdf (Silberschatz, A., Korth, H. F., & Sudarshan, S. (2020). Database system concepts (7ma ed.). McGraw-Hill Education.)
*   https://arxiv.org/pdf/2308.11432 (Wang, L., Ma, C., Feng, X., Zhang, Z., Yang, H., Zhang, J., ... & Wen, J. R. (2023). A survey on large language model based autonomous agents. arXiv preprint arXiv:2308.11432.)
*   https://arxiv.org/pdf/2312.10997 (Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., ... & Wang, H. (2023). Retrieval-augmented generation for large language models: A survey. arXiv preprint arXiv:2312.10997.)
*   http://lib.ysu.am/disciplines_bk/efdd4d1d4c2087fe1cbe03d9ced67f34.pdf (Russell, S. J., & Norvig, P. (2020). Artificial intelligence: a modern approach (4ta ed.). Pearson.)
*   Studer, R., Benjamins, V. R., & Fensel, D. (1998). Knowledge engineering: principles and methods. Data & knowledge engineering, 25(1-2), 161-197.
*   https://ceur-ws.org/Vol-1695/paper4.pdf (Ehrlinger, L., & Wöß, W. (2016). Towards a definition of knowledge graphs.)
*   https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/1029 (Randall Davis; Howard Shrobe; Peter Szolovits (1993). What Is a Knowledge Representation?. Association for the Advancement of Artificial Intelligence)