# Uniform Cost Search (UCS)

## Definición
El **Uniform Cost Search** (UCS) es un algoritmo de búsqueda que expande el nodo con el costo acumulado más bajo primero.

## Características
- Expande el nodo más barato primero.
- Utiliza una **frontera** que es una **cola de prioridad** ordenada por costo acumulado.

## Ejemplo de ejecución
Dado un conjunto de caminos:
\[ p(1), d(3), e(9) \]
1. Se elimina el nodo con menor costo: \( p(1) \)
2. Se expanden sus nodos sucesores y se agregan a la frontera:
   - \( d(3), e(9), q(16) \)
3. Se elige el de menor costo: \( d(3) \)
4. Se agregan sus sucesores a la frontera:
   - \( e(5), e(9), q(16) \)
5. Se repite el proceso hasta encontrar el objetivo.

## Problemas del UCS
- **Explora en todas las direcciones** sin información sobre la ubicación del objetivo.
- **Alto costo computacional** debido a la expansión uniforme.
- **No funciona bien si hay costos negativos**.

## Propiedades
- **Completitud**: Sí, si los costos son positivos.
- **Óptimo**: Sí, siempre encuentra la ruta de menor costo.
- **Eficiencia**: Puede ser ineficiente en grandes espacios de búsqueda.
