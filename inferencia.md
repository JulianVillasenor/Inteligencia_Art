# Inferencia Probabilística



## Introducción

La inferencia probabilística es una herramienta fundamental en Inteligencia Artificial. Permite razonar bajo incertidumbre mediante el cálculo de cantidades a partir de una distribución de probabilidad conjunta, utilizando modelos como Redes Bayesianas. Este documento resume los métodos exactos y aproximados de inferencia en dichos modelos.

---

## 1. Fundamentos de la Probabilidad e Inferencia

> “La teoría de la probabilidad no es más que el sentido común reducido a cálculo.” – Pierre Laplace (1819)  
> “La verdadera lógica para este mundo es el cálculo de las probabilidades.”  

- La probabilidad ofrece una forma formal de razonar con incertidumbre.
- Google aplica técnicas bayesianas como parte esencial de su ingeniería, según una anécdota de Joel Spolsky.

---

## 2. Redes Bayesianas (Bayesian Networks)

- Modelo gráfico para representar relaciones probabilísticas.
- Cada nodo representa una variable aleatoria.
- Las conexiones (arcos dirigidos) codifican dependencias condicionales.

**Ejemplo: Red de Alarma**  
Variables: Burglary (B), Earthquake (E), Alarm (A), JohnCalls (J), MaryCalls (M).  
Se utilizan Tablas de Probabilidad Condicional (CPTs) para definir la red.

---

## 3. Tipos de Inferencia

### a) Probabilidad Posterior
Calcular la probabilidad de una variable dada cierta evidencia observada.

### b) Explicación Más Probable (Most Likely Explanation)
Encontrar la asignación de valores más probable dadas ciertas observaciones.

- Variables:
  - Consulta (Q o X)
  - Evidencia (E)
  - Ocultas (H o Y)

---

## 4. Inferencia Exacta

### a) Enumeración

**Pasos:**
1. Establecer probabilidades incondicionales.
2. Enumerar todas las combinaciones de variables ocultas.
3. Calcular suma de productos para obtener P(Q | E).

**Problemas:**
- Muy lento para redes grandes.
- Escala exponencialmente con el número de variables (e.g., 10^16 filas posibles).

---

### b) Eliminación de Variables

Más eficiente que enumeración, aunque sigue siendo NP-hard.

**Concepto:** Entrelaza la combinación (join) y la marginalización (eliminate) de factores.

#### Factores
- Son arreglos multidimensionales que almacenan probabilidades.
- Ejemplos: P(X, Y), P(X | Y), P(Y | x)

#### Operaciones

- **Join (Unión):** Combina factores que comparten variables. Producto punto a punto.
- **Eliminate (Marginalizar):** Suma una variable del factor, reduciendo su dimensionalidad.

#### Proceso General:
1. Comenzar con CPTs instanciadas por la evidencia.
2. Mientras existan variables ocultas:
   - Elegir una variable H.
   - Unir todos los factores que mencionan H.
   - Eliminar H del nuevo factor.
3. Unir factores restantes.
4. Normalizar el resultado.

---

## 5. Evidencia

- Se incorpora desde el inicio seleccionando valores en los factores.
- Resultado: distribución conjunta seleccionada.
- Se normaliza para obtener P(Q | E).

---

## 6. Inferencia Aproximada

Cuando la inferencia exacta no es viable computacionalmente.

**Técnicas:**
- Muestreo (Sampling)
- Simulación (Simulating)
- Observación (Observing)

**Idea:** Generar muestras para aproximar la distribución de interés.

---

## Conclusión

La inferencia probabilística es esencial para agentes inteligentes que razonan bajo incertidumbre. Las redes bayesianas ofrecen una representación poderosa, y aunque los métodos exactos son costosos, existen técnicas eficientes como la eliminación de variables y métodos aproximados por muestreo para problemas grandes.

---
