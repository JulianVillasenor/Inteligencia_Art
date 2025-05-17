# Backpropagation en Redes Neuronales




Este documento explora el algoritmo de *backpropagation*, fundamental para el entrenamiento de redes neuronales mediante el cálculo automático de gradientes. Se basa en la visualización mediante grafos de computación y el uso sistemático de la regla de la cadena.

## Temas Principales y Conceptos Clave

### 1. Motivación: Regresión con Redes Neuronales de Cuatro Capas

Se considera una red con cuatro capas y una función de pérdida cuadrática:

```
Loss(x, y, V1, V2, V3, w) = (w · φ(V3φ(V2φ(V1φ(x)))) - y)^2
```

Donde se minimiza la función de pérdida utilizando *descenso de gradiente estocástico* (SGD), actualizando cada parámetro en la dirección opuesta a su gradiente:

```
V1 ← V1 - η ∇V1 Loss(x, y, ...)
V2 ← V2 - η ∇V2 Loss(x, y, ...)
V3 ← V3 - η ∇V3 Loss(x, y, ...)
w  ← w  - η ∇w  Loss(x, y, ...)
```

> Pregunta clave: **¿Cómo obtener los gradientes automáticamente?**

---

### 2. Grafos de Computación

Un **grafo de computación** es un grafo dirigido acíclico donde:

* Cada nodo representa una subexpresión.
* La raíz representa la expresión final.

**Ventajas:**

* Permite *calcular gradientes automáticamente*.
* Facilita la visualización y modularidad de las operaciones.

---

### 3. Funciones como Cajas: Bloques Básicos

Cada operación se representa como una caja con entradas/salidas y reglas de derivación:

| Operación             | Derivadas parciales                  |
| --------------------- | ------------------------------------ |
| Suma (c = a + b)      | ∂c/∂a = 1, ∂c/∂b = 1                 |
| Resta (c = a - b)     | ∂c/∂a = 1, ∂c/∂b = -1                |
| Producto (c = a·b)    | ∂c/∂a = b, ∂c/∂b = a                 |
| Cuadrado (c = a^2)    | ∂c/∂a = 2a                           |
| Máximo (c = max(a,b)) | ∂c/∂a = 1\[a > b], ∂c/∂b = 1\[a < b] |
| Sigmoide (σ(a))       | ∂c/∂a = σ(a)(1-σ(a))                 |

Estas derivadas locales son los *bloques fundamentales* para el cálculo automático.

---

### 4. Composición de Funciones y la Regla de la Cadena

En funciones compuestas, el gradiente se propaga usando la **regla de la cadena**:

```
∂c/∂a = (∂c/∂b) * (∂b/∂a)
```

Este principio permite calcular gradientes en redes profundas capa por capa.

---

### 5. Ejemplos Prácticos

#### a) Clasificación Lineal con Hinge Loss

```
Loss(x, y, w) = max{1 - (w · φ(x))y, 0}
∇w Loss = -1[margin < 1] φ(x)y
```

#### b) Red Neuronal de Dos Capas

```
Loss(x, y, V, w) = (w · φ(Vφ(x)) - y)^2
∇w Loss = 2(w φ(Vφ(x)) - y) φ(Vφ(x))
∇V Loss = ... (incluye derivadas de capas anteriores)
```

---

### 6. Algoritmo de Backpropagation

#### Definiciones:

* **Forward (fᵢ):** valor computado en el nodo i (de hojas a raíz).
* **Backward (gᵢ):** influencia de fᵢ en la pérdida total (∂loss/∂fᵢ).

#### Pasos del algoritmo:

1. **Forward pass:** computar cada fᵢ desde entradas hasta salida.
2. **Backward pass:** computar cada gᵢ desde la salida hasta las entradas usando la regla de la cadena.

---

### 7. Optimización y Práctica

* Redes neuronales son **no convexas**, por lo que su entrenamiento puede ser más complejo que modelos lineales.
* Aun así, **funcionan eficazmente en la práctica**.
* Se introducen más adelante técnicas como regularización, normalización, inicialización y optimizadores avanzados.

---

## Conclusión

Backpropagation es el corazón del entrenamiento de redes neuronales modernas. A través de grafos de computación, funciones básicas y la regla de la cadena, permite el cálculo eficiente de gradientes necesarios para el aprendizaje. Su implementación ha sido crucial para el éxito de bibliotecas como TensorFlow y PyTorch.

---

> Próximo tema sugerido: **Entrenamiento práctico de redes neuronales** y técnicas para mejorar la eficiencia y generalización.
