# Problemas de Satisfacción de Restricciones (CSPs)


## Introducción

Los Problemas de Satisfacción de Restricciones (CSPs, por sus siglas en inglés) son una clase de problemas en los que el objetivo es encontrar asignaciones de valores a variables que satisfacen un conjunto de restricciones. A diferencia de la búsqueda tradicional que se enfoca en encontrar una ruta, los CSPs se centran en identificar soluciones que cumplan con todas las restricciones impuestas.

---

## ¿Qué es la Búsqueda? Planificación vs. Identificación

- **Búsqueda estándar**: Se enfoca en la **planificación**, es decir, en encontrar la mejor **ruta** hacia un objetivo.
- **CSPs**: Se enfocan en la **identificación**, buscando **asignaciones válidas** para un conjunto de variables. La ruta no importa, solo la solución final.

---

## Definición Formal de CSPs

Un CSP está definido por:

- **Variables:** \( X_1, X_2, ..., X_n \)
- **Dominios:** Cada variable \( X_i \) tiene un dominio \( D_i \) de valores posibles.
- **Restricciones:** Subconjuntos de variables con combinaciones válidas de valores.

El objetivo es encontrar una **asignación completa** que satisfaga **todas las restricciones**.

---

## Ejemplos Clásicos de CSPs

### 🗺️ Coloreado de Mapas

- **Variables:** Regiones (ej. WA, NT, Q, etc.)
- **Dominios:** Colores (rojo, verde, azul)
- **Restricciones:** Regiones adyacentes no deben tener el mismo color.

### ♛ N-Reinas

- Ubicar \( n \) reinas en un tablero \( n \times n \) sin que se ataquen entre sí.
- Varias formas de representar variables y restricciones.

### 🔢 Criptoaritmética

- Asignar dígitos a letras de una ecuación como `SEND + MORE = MONEY`.
- **Restricciones:** Letras diferentes tienen dígitos diferentes, y deben cumplir con la suma.

### 🧩 Sudoku

- **Variables:** Casillas vacías.
- **Dominios:** Dígitos del 1 al 9.
- **Restricciones:** 
  - Filas, columnas y subcuadrículas 3x3 deben contener todos los dígitos del 1 al 9 sin repetir.

---

## Grafos de Restricciones

- En CSPs binarios, cada restricción involucra a lo sumo dos variables.
- Se representan como **grafos**:
  - **Nodos:** Variables
  - **Aristas:** Restricciones entre pares

La estructura del grafo puede utilizarse para **optimizar** la búsqueda.

---

## Tipos de Variables y Restricciones

### Variables

- **Discretas:** Dominios finitos (ej. colores, dígitos).
- **Infinitas:** Enteros, cadenas (restricciones lineales o no lineales).
- **Continuas:** Tiempo, espacio (pueden resolverse con programación lineal).

### Restricciones

- **Unarias:** Involucran una sola variable.
- **Binarias:** Entre dos variables.
- **De orden superior:** Involucran más de dos variables.
- **Blandas (soft):** Representan preferencias con un costo.

---

## Aplicaciones Reales

Los CSPs son ampliamente usados en:

- Asignación de tareas
- Planificación de horarios
- Diseño de circuitos
- Configuración de hardware
- Diagnóstico automático

---

## Resolución de CSPs

### Formulación como búsqueda

- **Estado inicial:** Asignación vacía \(\{\}\)
- **Sucesor:** Asignar un valor a una variable no asignada
- **Test de objetivo:** Asignación completa y válida

### 🔁 Búsqueda de Retroceso (Backtracking)

- Estrategia básica no informada.
- Avanza asignando valores y retrocede cuando encuentra una violación de restricciones.

### 🧹 Filtrado

- **Forward checking:** Elimina valores inconsistentes después de cada asignación.
- **Consistencia de arco:** Reduce dominios mediante propagación de restricciones.

### 🔀 Heurísticas

- **Ordenamiento de variables:** Escoge primero las más restrictivas.
- **Ordenamiento de valores:** Elige el valor menos restrictivo.

---

## Conclusión

Los CSPs ofrecen una poderosa estructura formal para resolver problemas complejos de asignación y planificación. Su tratamiento mediante técnicas de filtrado, heurísticas y búsqueda estructurada los convierte en herramientas clave en la inteligencia artificial.

---

