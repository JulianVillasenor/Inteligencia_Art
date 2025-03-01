# Heuristicas en los problemas de busqueda

## Definición
Una **heurística** es una estimación de cuán cerca está un estado del objetivo. Se diseña específicamente para un problema de búsqueda en particular.

## Ejemplos de heurísticas
- **Distancia Manhattan** (para movimientos en una cuadrícula con movimientos ortogonales).
- **Distancia Euclidiana** (para movimientos en línea recta).

## Problemas de búsqueda y heurísticas

### Problema de la Torre de Hanói
Sabemos que la solución óptima tiene una complejidad:
\[ T(n) = 2^n - 1 \]
Una posible heurística:
\[ h(n) = 2^m - 1 \]
Donde \( m \) es el número de discos que aún no están en la torre destino.

### Problema de los Caníbales y Cristianos
Se pueden diseñar heurísticas basadas en la cantidad de personas en cada orilla y las restricciones del bote.

## Algoritmos relacionados

### Best First / Greedy Search
- **Estrategia**: Expandir el nodo más cercano al objetivo.
- **Problema**: Puede llevar por el camino más costoso si la heurística no está bien definida.

### A* Search
- **Fórmula**:
  \[ f(n) = g(n) + h(n) \]
  donde:
  - \( g(n) \) es el costo acumulado desde el inicio.
  - \( h(n) \) es la estimación del costo restante.

## Heurísticas admisibles
Una heurística \( h \) es **admisible** si es optimista:
\[ h(n) \leq h^*(n) \]
Donde \( h^*(n) \) es el costo real hasta el objetivo.

## Consideraciones finales
- **Si la heurística es bien diseñada**, mejora la eficiencia de búsqueda.
- **Si la heurística no es óptima**, puede llevar a soluciones ineficientes o no encontrar la mejor ruta.
