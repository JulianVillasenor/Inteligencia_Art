# Introducción a las Redes Neuronales



Este documento presenta una introducción a las redes neuronales como técnica para construir **predictores no lineales** en aprendizaje automático. Se destaca su capacidad para descomponer problemas complejos en **subproblemas intermedios** que pueden resolverse en paralelo mediante **capas** que representan diferentes niveles de abstracción. Se comparan con modelos lineales, se introducen funciones de activación como solución al problema de gradientes nulos, y se presentan las redes neuronales profundas como una extensión empíricamente eficaz.

---

## Temas Principales y Conceptos Clave

### Predictores No Lineales

* Los predictores lineales tienen la forma general:
  `f_w(x) = w · ϕ(x)`
  donde `ϕ(x)` es una transformación lineal del input, por ejemplo `ϕ(x) = [1, x]`.

* Las redes neuronales permiten predictores **no lineales** mediante transformaciones anidadas:
  `f_w(x) = w · ϕ(V ϕ(x))`
  donde `ϕ` introduce la no linealidad mediante funciones de activación y composiciones.

* Ejemplo: al usar `ϕ(x) = [1, x, x^2]`, se obtiene un predictor cuadrático.

### Descomposición del Problema

* Las redes neuronales abordan tareas complejas dividiéndolas en **subproblemas intermedios paralelos**.

* Ejemplo: predicción de colisiones entre autos, donde la condición `y = sign(|x1 - x2| ≤ 1)` se descompone como:

  * `h1(x) = 1[x1 - x2 ≤ -1]`
  * `h2(x) = 1[x2 - x1 ≤ -1]`
  * Salida final: `f(x) = sign(h1(x) + h2(x))`

* Esta descomposición puede representarse vectorialmente como `h(x)`, un vector de salidas intermedias.

### Funciones de Activación

* Las funciones indicadoras (como las anteriores) tienen **gradiente cero**, lo cual bloquea el aprendizaje basado en gradiente.

* Solución: utilizar **funciones de activación suaves** con gradientes no nulos. Ejemplos:

  * **Threshold**: `ϕ(z) = 1[z ≥ 0]` → *no derivable*
  * **Logística**: `ϕ(z) = 1 / (1 + e^-z)` → *gradiente suave*
  * **ReLU**: `ϕ(z) = max(0, z)` → *gradiente no nulo para z > 0*

* Forma general de los subproblemas ahora:
  `h_i(x) = ϕ(v_i · ϕ(x))`

### Redes Neuronales de Dos Capas

* Estructura típica:

  * Capa intermedia:
    `h(x) = ϕ(V ϕ(x))`
  * Capa de salida (clasificación):
    `f_{V,w}(x) = sign(w · h(x))`

* `h(x)` se interpreta como una **representación de características aprendida** del input `x`.

* La clase de hipótesis `F` incluye todos los predictores que varían sobre los parámetros `V` y `w`.

### Redes Neuronales Profundas

* Las redes profundas extienden la arquitectura a **múltiples capas**:

  * 1 capa: `score = w · ϕ(x)`
  * 2 capas: `score = w · ϕ(V ϕ(x))`
  * 3 capas: `score = w · ϕ(V2 ϕ(V1 ϕ(x)))`

* Cada capa representa un **nivel adicional de abstracción** o un **paso de cómputo adicional**.

#### ¿Por qué profundidad?

* Para representar múltiples niveles de abstracción.
* Para realizar cálculos complejos mediante composición de operaciones simples.
* **Empíricamente funciona bien**, aunque **la teoría aún es incompleta**.

---

## Ideas Clave y Citas Notables

* "Las redes neuronales descomponen problemas complejos en subproblemas intermedios paralelos."
* "La profundidad permite representar múltiples niveles de abstracción."
* "Las funciones de activación son esenciales para el aprendizaje, ya que permiten gradientes no nulos."
* "h(x) en una red de dos capas puede verse como una 'representación aprendida' del input."
* "La teoría todavía es incompleta, pero empíricamente funciona bien."

---

## Próximos Pasos

El siguiente tema en el curso es **aprendizaje en redes neuronales**, incluyendo los algoritmos de entrenamiento como el descenso del gradiente y backpropagation, así como cuestiones de optimización y generalización.
