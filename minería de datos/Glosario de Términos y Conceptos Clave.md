---
fecha: 2026-09-09
materia: minería de datos
tema: Glosario Integral de Términos, Fórmulas y Conceptos Clave (Sesiones 1 a 10)
tags:
  - universidad
  - minería_de_datos
  - glosario
  - conceptos_clave
  - kdd
  - muestreo
  - calidad_de_datos
  - imputacion
  - outliers
---

# Glosario Integral de Minería de Datos
*Compilado consolidado de las Sesiones 1 a 10*

Este glosario reúne y define formal y conceptualmente todos los términos técnicos, fórmulas matemáticas y algoritmos estudiados durante el curso de **Minería de Datos (FCC - BUAP)**.

---

---

## 📑 Índice Temático del Glosario
1. [[#🧠 Diccionario Intuitivo: Conceptos Raros Explicados con Peras y Manzanas|Conceptos Raros Explicados con Peras y Manzanas]]
2. [[#Módulo 1: Fundamentos, Metodología KDD y Modelos|Fundamentos, Metodología KDD y Modelos]]
3. [[#Módulo 2: Población, Técnicas de Muestreo y Cobertura Geométrica|Población, Técnicas de Muestreo y Cobertura Geométrica]]
4. [[#Módulo 3: Calidad de Datos, Limpieza y Normalización Textual|Calidad de Datos, Limpieza y Normalización Textual]]
5. [[#Módulo 4: Tratamiento y Técnicas de Imputación de Valores Faltantes|Tratamiento y Técnicas de Imputación de Valores Faltantes]]
6. [[#Módulo 5: Detección y Taxonomía de Valores Atípicos (Outliers)|Detección y Taxonomía de Valores Atípicos (Outliers)]]

---

## 🧠 Diccionario Intuitivo: Conceptos Raros Explicados con Peras y Manzanas

Para que no te pierdas en las palabras rimbombantes de los libros, aquí tienes la traducción a español cotidiano con analogías reales:

### 🍬 1. ¿Qué diablos es un "Estrato"?
* **En palabras no tradicionales:** Un estrato es simplemente **un montoncito de cosas que son del mismo color o tipo**.
* **La analogía de los dulces M&M's:**  
  Imagina que abres una bolsa de dulces donde hay **90 amarillos**, **8 azules** y solo **2 rojos**.
  * Si metes la mano a ciegas (muestreo aleatorio), casi seguro sacarás puros amarillos y los rojos (la minoría) se quedarán olvidados en la bolsa.
  * ¿Qué es estratificar? Es vaciar la bolsa en la mesa y separar los dulces en **tres montoncitos**: el montoncito amarillo, el azul y el rojo. **Cada montoncito es un ESTRATO**.
  * Luego te obligas a sacar 1 dulce de cada montoncito. ¡Listo! Tu plato tiene todos los colores representados. Eso es **Muestreo Estratificado**.

---

### 📦 2. ¿Qué es un "Cluster / Conglomerado" y en qué se diferencia del Estrato?
* **En el Estrato:** Todos los elementos dentro del montoncito son **idénticos entre sí** (puros dulces rojos, o puras mujeres, o puros ricos).
* **En el Cluster:** El grupo es una **caja mixta con variedad**.  
  * *Analogía:* Un salón de clases de la universidad es un cluster. Adentro hay hombres, mujeres, aplicados, reprobados, ricos y de clase media. El salón entero es una "mini-ciudad".
  * En el muestreo por clusters, en lugar de revisar 100 salones, rifas y eliges al azar 5 salones completos.

---

### 🎮 3. ¿Qué es un "Descriptor"?
* **En palabras no tradicionales:** Son las **características o estadísticas de la tarjeta de tu personaje en un videojuego**.
* *Analogía:* Si tu personaje es un guerrero, sus descriptores son: $[ \text{Fuerza} = 90, \, \text{Velocidad} = 40, \, \text{Magia} = 10, \, \text{Nivel} = 5 ]$.  
* En una tabla de Excel, **cada columna es un descriptor**. Si tienes 10 columnas, tu modelo vive en un "hiperespacio de 10 dimensiones".

---

### 🧭 4. ¿Qué significa que los descriptores sean "Ortogonales"?
* **En palabras no tradicionales:** Significa que **"cero copia", cada columna te da información $100\%$ nueva y no repite chismes**.
* *Analogía de la Brújula:*  
  Caminar hacia el **Norte** y caminar hacia el **Este** son direcciones **ortogonales (a $90^\circ$)**. Caminar al Norte no te acerca ni un milímetro al Este. Son independientes.
  * Si en tu base de datos pones `Salario Mensual` y `Salario Anual`, es como caminar al Norte y luego al Norte otra vez: **¡no te estás moviendo en ninguna dirección nueva!** Solo estás repitiendo lo mismo y haciendo que el modelo se obsesione con el dinero.

---

### 🪢 5. ¿Qué es la "Cobertura Convexa" (*Convex Hull*)?
* **En palabras no tradicionales:** Es la **liga elástica que rodea los clavos**.
* *Analogía:* Imagina que clavas 50 clavos en una tabla de madera. Luego tomas una liga elástica gigante y la sueltas alrededor de todos los clavos. La liga se va a tensar tocando únicamente los clavos de las orillas exteriores.  
  La forma geométrica que forma esa liga tensada es la **cobertura convexa**. Si tu muestra conserva los clavos de la orilla, la Red Neuronal puede dibujar la frontera perfecta.

---

### 🗺️ 6. ¿Qué es un "Embedding"?
* **En palabras no tradicionales:** Es el **traductor de palabras a coordenadas de GPS**.
* *Analogía:* Una computadora es ciega a las letras. Para que entienda qué es *"médico"* y *"doctor"*, el embedding le asigna una latitud y longitud numérica en un mapa:
  * *"Médico"* = Coordenada $(45.12, 12.80)$
  * *"Doctor"* = Coordenada $(45.14, 12.81)$
  * Como están a 2 milímetros de distancia en el mapa, la computadora sabe que son casi lo mismo.

---

### ❓ 7. ¿Qué son MCAR, MAR y MNAR? (El misterio de los datos faltantes)
* **MCAR (El Accidente Puro):** Se te cayó una taza de café encima de la hoja de la encuesta y borró 3 respuestas. El café cayó al azar, no tiene malicia ni truco.
* **MAR (El Condicionado):** Los jóvenes no contestaron la pregunta de *"¿A qué edad se va a pensionar?"*. La falta del dato no es por accidente, sino porque tienen 20 años y no piensan en pensiones (depende de su edad, que sí la conoces).
* **MNAR (El Secreto Oculto):** La persona que gana 10 millones de pesos al mes deja en blanco la casilla de *"¿Cuánto gana?"* porque le da miedo el SAT o los secuestros. El dato falta **precisamente por culpa del valor que está escondiendo**.

---

### 🦒 8. ¿Qué es un "Outlier"?
* **En palabras no tradicionales:** Es **la jirafa en un corral de gallinas**.
* *Analogía:* Todos los animales miden entre 20 y 40 centímetros, y de repente hay un animal que mide 5 metros. Ese es un **Outlier**. Si calculas el "promedio de altura del corral", la jirafa hace que el promedio dé 2 metros y arruina todos tus cálculos.

---

## Módulo 1: Fundamentos, Metodología KDD y Modelos

### Minería de Datos (*Data Mining*)
Fase técnica y algorítmica central del proceso KDD orientada a la extracción automática, no trivial e inteligente de patrones válidos, novedosos, potencialmente útiles y comprensibles a partir de grandes volúmenes de datos.

### KDD (*Knowledge Discovery in Databases*)
Proceso interactivo e iterativo global de descubrimiento de conocimiento estructurado en fases secuenciales: *Selección $\to$ Preprocesamiento (Limpieza) $\to$ Transformación $\to$ Minería de Datos $\to$ Interpretación / Evaluación*.

### Estructura del Modelo
La arquitectura funcional interna elegida para representar los datos (ej. hiperplanos en Redes Neuronales o SVM, árboles de decisión con reglas jerárquicas Si-Entonces, o centroides en K-Means).

### Función de Pérdida / Costo (*Loss Function*)
Función matemática cuantitativa $J(\theta)$ que mide la discrepancia o error entre las predicciones del modelo y la realidad observada (*Ground Truth*). El objetivo del entrenamiento es minimizar esta función.

### Espacio de Búsqueda y Optimización
Conjunto multidimensional de todas las combinaciones posibles de parámetros internos del modelo. La optimización matemática (mediante Gradiente Descendente, Algoritmos Genéticos o heurísticas) navega este espacio para hallar los mejores pesos.

---

## Módulo 2: Población, Técnicas de Muestreo y Cobertura Geométrica

### Población Universo ($N$)
Conjunto total y exhaustivo de todos los elementos o eventos posibles que comparten una característica definida. Frecuentemente es infinito, inaccesible o computacionalmente inmanejable.

### Muestra Representativa ($n$)
Subconjunto finito extraído de la población que preserva con fidelidad la estructura demográfica, las proporciones de clase y las propiedades estadísticas ($\mu, \sigma$) del universo original.

### Cobertura Convexa (*Convex Hull*)
El polígono o poliedro convexo más pequeño en el espacio euclidiano $\mathbb{R}^d$ que encierra completamente a un conjunto de puntos. Para que un modelo de frontera continua (Red Neuronal) aprenda los contornos reales, la muestra debe conservar los puntos perimetrales del *Convex Hull*.

### Fórmula de Cochran
Ecuación estadística clásica para calcular el tamaño muestral representativo inicial $n_0$ en poblaciones grandes:
$$n_0 = \frac{Z^2 \cdot p \cdot q}{e^2}$$
*(Donde $Z$ es el nivel de confianza, $p$ la varianza estimada y $e$ el margen de error permitido)*.

### Muestreo Probabilístico
Familia de técnicas donde cada elemento de la población tiene una probabilidad conocida y estrictamente mayor que cero ($P(x_i) > 0$) de ser seleccionado, permitiendo calcular márgenes de error estadísticos.

### Muestreo Estratificado
Técnica probabilística que divide la población en subgrupos homogéneos internos pero disjuntos (**estratos**) y extrae muestras independientes de cada uno. Es indispensable en poblaciones con clases desbalanceadas para evitar la extinción de clases minoritarias.

### Muestreo Progresivo / Incremental (*Progressive Sampling*)
Algoritmo dinámico que inicia con una muestra pequeña ($n_0$) y la incrementa paso a paso ($n_k = n_{k-1} + \Delta n$) evaluando la estabilidad de parámetros estadísticos o curvas de aprendizaje, deteniéndose en el tamaño óptimo mínimo ($n^*$).

### Ventana de Estabilidad ($W$) y Tolerancia ($\epsilon$)
Criterio de parada del muestreo progresivo. Exige que a lo largo de $W$ iteraciones consecutivas, la fluctuación máxima de las métricas monitoreadas sea menor que un umbral estricto ($\max |\Delta| < \epsilon$).

### Información Marginal Decreciente
Principio que establece que cada nuevo dato recolectado aporta menos información novedosa que los anteriores. Los primeros datos delinean los patrones; los datos masivos posteriores solo aportan redundancia (*"Principio de la cucharada de sopa"*).

### Muestreo Sistemático
Técnica donde los elementos se eligen a intervalos regulares de paso $k$ a lo largo de un flujo o secuencia ordenada, comenzando en un punto de arranque aleatorio $r \in [1, k]$:
$$\text{Muestra} = \{ r, \, r+k, \, r+2k, \, \dots \}$$

### Muestreo de Conglomerados en Dos Etapas (*Two-Stage Cluster*)
Método en el que la población se divide en grupos densos heterogéneos (*clusters*). En la **Etapa 1** se eligen algunos clusters al azar; en la **Etapa 2** se extrae una muestra aleatoria simple dentro de los clusters elegidos.

### Muestreo Multietapa (*Multi-Stage Sampling*)
Procedimiento jerárquico que encadena tres o más niveles de muestreo en cascada (ej. *Clustering inicial $\to$ Estratificación de clusters $\to$ Selección aleatoria de clusters $\to$ Muestreo sistemático de individuos*). Ideal para Big Data y censos.

---

## Módulo 3: Calidad de Datos, Limpieza y Normalización Textual

### Muestra Inicial ($M_I$)
El primer conjunto de datos crudos recolectados tras el proceso de muestreo, antes de someterse a limpieza, imputación y normalización.

### Duplicados Ponderados
Detección de duplicidad en variables numéricas continuas (sensores) donde dos filas no son idénticas por decimales mínimos causados por ruido de hardware. Se asignan pesos $w_i$ y se fusionan si su distancia es inferior a un umbral de corte $\epsilon$.

### Normalización Textual
Pipeline de estandarización para texto no estructurado: conversión a minúsculas (*lowercasing*), recorte de espacios (*trimming*), remoción de acentos, puntuación y caracteres especiales vía expresiones regulares.

### *Stopwords* (Palabras de Paro)
Términos de alta frecuencia gramatical (artículos, preposiciones, conjunciones como *"de"*, *"el"*, *"la"*, *"que"*) que saturan las matrices sin aportar señal discriminativa, por lo que son eliminadas en la limpieza.

### Coincidencia Difusa (*Fuzzy Matching*)
Técnica de comparación no exacta entre cadenas de caracteres mediante métricas de edición como la **Distancia de Levenshtein** (número mínimo de inserciones, borrados y sustituciones para igualar dos textos), permitiendo unificar variantes tipográficas (ej. *"CDMX"* $\to$ *"Ciudad de México"*).

### *Embeddings* (Incrustaciones Vectoriales)
Representaciones matemáticas densas que transforman palabras o textos en vectores numéricos en un hiperespacio continuo ($\mathbb{R}^d$), logrando que conceptos con significados semánticos similares queden a corta distancia geométrica.

### Similitud / Distancia Coseno
Métrica que evalúa el coseno del ángulo $\theta$ entre dos vectores en el hiperespacio, midiendo su concordancia direccional sin verse distorsionada por la longitud o magnitud:
$$\cos(\theta) = \frac{\vec{A} \cdot \vec{B}}{\|\vec{A}\| \|\vec{B}\|}$$

### Descriptor (Atributo / *Feature*)
Cada variable independiente medida que conforma las columnas de la matriz de datos y define una dimensión cartesiana en el hiperespacio de representación.

### Descriptores Ortogonales
Descriptores linealmente independientes entre sí cuyo producto escalar es cero y su correlación estadística es nula ($r = 0$). Garantizan que cada variable aporte información única sin redundancia.

### Multicolinealidad
Condición patológica donde dos o más descriptores tienen alta correlación entre sí ($r \approx 1$). Causa inestabilidad matemática en los modelos y genera un sobrepeso artificial involuntario en algoritmos basados en distancias euclidianas (K-Means, KNN, SVM).

---

## Módulo 4: Tratamiento y Técnicas de Imputación de Valores Faltantes

### MCAR (*Missing Completely at Random*)
Mecanismo donde la pérdida del dato es totalmente accidental e independiente tanto del valor de la propia variable como de las demás variables del dataset. Eliminar filas con nulos no introduce sesgo en este caso.

### MAR (*Missing at Random*)
Mecanismo donde la probabilidad de que falte un dato depende sistemáticamente de los valores de **otras variables observadas**, pero no del valor del dato en sí. Requiere imputación condicionada o por modelos para evitar sesgo.

### MNAR (*Missing Not at Random*)
Mecanismo crítico donde la probabilidad de que falte el dato depende directamente del **propio valor oculto no observado** (ej. personas multimillonarias que ocultan su ingreso). Exige modelar explícitamente la ausencia mediante variables indicadoras binarias.

### Imputación por Tendencia Central
Sustitución de valores nulos por estimadores estadísticos univariados:
* **Media:** Para datos con distribución simétrica (Normal) y sin *outliers*.
* **Mediana:** El estimador más robusto para variables asimétricas o con valores atípicos.
* **Moda:** Para variables categóricas cualitativas.

### Imputación Condicionada por Grupo
Cálculo de la mediana o media particionando los datos por estratos clave (ej. $\text{Mediana}(\text{Age} \mid \text{Pclass}, \, \text{Sex})$ en Titanic), respetando la demografía interna.

### Interpolación
Técnica matemática que construye una curva continua (lineal, polinomial o *spline*) a través de las observaciones temporales adyacentes para estimar valores faltantes en series de tiempo y señales continuas.

### `KNNImputer`
Algoritmo de imputación multivariable que calcula la distancia euclidiana entre instancias sobre las variables conocidas, identifica los $k$ vecinos más cercanos y rellena el hueco con la media ponderada de esos vecinos.

### `MissForest` (Imputación por Random Forest)
Método no paramétrico iterativo del estado del arte que entrena bosques aleatorios para predecir los valores faltantes de cada columna, capturando interacciones no lineales complejas sin requerir escalado de datos.

### Imputación por Clustering No Supervisado ($M'$ sin $A_x$)
Técnica para imputar un atributo clave $A_x$ cuando no hay etiquetas de clase: se genera un subconjunto $M'$ omitiendo $A_x$, se ejecuta **K-Means** o **DBSCAN** para formar nubes densas, y se imputa el valor central del cluster al que pertenezca la instancia.

### SMOTE (*Synthetic Minority Over-sampling Technique*)
Algoritmo de balanceo que enriquece clases minoritarias creando instancias sintéticas a lo largo del segmento de línea que une a cada punto minoritario con sus vecinos más cercanos ($k$-NN):
$$x_{\text{nuevo}} = x_i + \lambda (\hat{x}_i - x_i) \quad \text{con } \lambda \in [0, 1]$$

---

## Módulo 5: Detección y Taxonomía de Valores Atípicos (*Outliers*)

### Valor Atípico (*Outlier*)
Observación que difiere de forma tan extrema del resto de los datos que genera sospechas fundadas de haber sido producida por un mecanismo generador distinto (ruido, falla técnica o evento extremo real).

### Outlier Global (Puntual)
Instancia individual cuyo valor numérico en una o más variables se aparta radicalmente de todo el conjunto de datos completo (ej. Edad $= 250$ años).

### Outlier Contextual (Condicional)
Instancia cuyo valor está dentro de los límites posibles de la población, pero resulta totalmente anómalo al evaluarlo bajo sus atributos de contexto espacial, temporal o de grupo (ej. $35^\circ\text{C}$ en pleno invierno en Alaska).

### Outlier Colectivo
Secuencia o ráfaga de instancias cuyos valores individuales son ordinarios, pero cuya aparición conjunta o consecutiva viola la dinámica del sistema (ej. línea plana de $0\text{ mV}$ en un electrocardiograma durante 5 segundos).

### Puntuación Estándar (Z-Score)
Métrica estadística de detección que calcula el desvío en unidades de desviación estándar respecto a la media:
$$z = \frac{x - \mu}{\sigma}$$
*(Si $|z| > 3$, se cataloga como outlier global bajo el supuesto de normalidad)*.

### Rango Intercuartílico ($IQR$ y Regla de Tukey)
Técnica robusta no paramétrica basada en cuartiles:
$$IQR = Q_3 - Q_1$$
$$\text{Límites} = [Q_1 - 1.5 \times IQR, \quad Q_3 + 1.5 \times IQR]$$
*(Los valores fuera de estas vallas se clasifican como posibles outliers)*.

### Enmascaramiento (*Masking*)
Efecto adverso donde la presencia de múltiples outliers extremos contamina e infla artificialmente la media ($\mu$) y la desviación estándar ($\sigma$), haciendo que el Z-Score no logre detectarlos.
