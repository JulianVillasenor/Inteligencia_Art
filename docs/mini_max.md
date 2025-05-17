# Minimax y Minimax con Poda Alpha-Beta

## Minimax
### Definición
El algoritmo **Minimax** se utiliza en juegos adversariales para determinar la mejor jugada posible asumiendo que el oponente también juega de manera óptima. La idea principal es:
- Maximizar mi ganancia minimizando la del oponente.
- Asumir que el oponente jugará de la mejor manera posible.
- Adoptar una estrategia conservadora.

### Modelo de juego
```python
class ModeloJuego:
    def inicializa(self):
        return (50, 3)  # Estado inicial

    def acciones_legales(self, s, jugador):
        return {a1, a2, ...}  # Conjunto de acciones legales

    def transicion(self, s, a, j):
        return s'  # Estado resultante

    def terminal(self, s):
        return bool  # Determina si el estado es terminal

    def ganancia(self, s):
        return ganancia_jugador_1  # Juego de suma cero
```

## Minimax con Poda Alpha-Beta
### Problema con Minimax
El algoritmo Minimax explora **todo el árbol de juego**, lo cual es ineficiente en juegos complejos como **Connect 4**.

### Mejora: Poda Alpha-Beta
Para mejorar Minimax, aplicamos **poda Alpha-Beta**, que evita evaluar ramas innecesarias.

#### Concepto de Poda
Ejemplo:
\[ MAX( MIN(3,7), MIN(7,X) ) = 3 \]
Aquí, no es necesario conocer el valor de **X**, pues ya sabemos que el resultado es 3.

#### Implementación de Alpha-Beta Pruning
```python
def max_value(state, alpha, beta):
    v = float('-inf')
    for succesor in state.sucesores():
        v = max(v, value(succesor, alpha, beta))
        if v >= beta:
            return v
        alpha = max(alpha, v)
    return v

def min_value(state, alpha, beta):
    v = float('inf')
    for succesor in state.sucesores():
        v = min(v, value(succesor, alpha, beta))
        if v <= alpha:
            return v
        beta = min(beta, v)
    return v
```

### Optimización adicional
- **Orden de exploración**: Explorar **primero** las mejores jugadas esperadas.
- **Búsqueda a profundidad limitada**: En juegos muy grandes, evaluamos solo hasta cierta profundidad.
- **NegaMax**: Variante de Minimax donde se unifican las funciones de Max y Min utilizando cambio de signos.
- **Tablas de transposición**: Evita recalcular estados ya explorados.

## Conclusión
La poda Alpha-Beta mejora Minimax reduciendo la cantidad de nodos explorados, lo que hace que sea más eficiente sin afectar la precisión de la solución.
