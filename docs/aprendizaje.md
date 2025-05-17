# Aprendizaje

## Error en muestra
\[
E_{in} = \frac{1}{2} \sum_{i=1}^{N} e(y_i, y'_i)
\]

## Error fuera de muestra
\[
E_{out} = E_{x \in X}[e(y_i, y'_i)]
\]

El aprendizaje existe si y solo si \( E_{out} \approx 0 \). Esto solo es posible si \( E_{in} \approx E_{out} \).

## Análisis de las fórmulas:
\[
E_{in} = \frac{1}{2} \sum_{i=1}^{n} e(y_i, y'_i)
\]

- \( n \) = número de muestras de entrenamiento
- \( y_i \) = valor real de la i-ésima muestra
- \( y'_i \) = predicción del modelo para la muestra

## ¿Cómo se define \( e(y_i, y'_i) \)?

1. **Para clasificación:**
   \[
   e(y, y') = \begin{cases} 
   0, & \text{si } y = y' \\ 
   1, & \text{si } y \neq y' 
   \end{cases}
   \]

2. **Entropía cruzada:**
   \[
   e(y, y') = -y \log(y') - (1 - y) \log(1 - y')
   \]

3. **Para regresión:**
   \[
   e(y, y') = (y - y')^2
   \]

---

# Esperanza matemática (Valor esperado)
Es una variable aleatoria \( X \), es el promedio ponderado de todos los posibles valores, considerando sus probabilidades de ocurrencia.

1. Para una variable aleatoria discreta con valores \( x_i \) y probabilidades \( P(X = x_i) \):
   \[
   E[X] = \sum x_i P(X = x_i)
   \]

2. Para una variable aleatoria continua con función de densidad de probabilidad \( f(x) \):
   \[
   E[X] = \int_{-\infty}^{\infty} x f(x)dx
   \]

### Explicación intuitiva de esperanza
- Es el promedio ponderado de los valores que puede tomar \( X \).
- En términos simples, si repitiésemos el experimento muchas veces, la media de los resultados convergería a \( E[X] \).

#### Ejemplo de lanzar un dado justo:
\[
E[X] = 1 \cdot \frac{1}{6} + 2 \cdot \frac{1}{6} + 3 \cdot \frac{1}{6} + 4 \cdot \frac{1}{6} + 5 \cdot \frac{1}{6} + 6 \cdot \frac{1}{6} = 3.5
\]

Aunque no puedes obtener 3.5 en un tiro, es el promedio esperado si lanzas muchas veces.

---

# Aplicación en \( E_{out} \)
\[
E_{out} = E_{x \in X}[e(y,y')] = \int e(y,y') P(x)dx
\]

Esto significa que \( E_{out} \) es el promedio ponderado del error \( e(y,y') \) considerando la distribución de los datos \( P(x) \).
