# Problemas de Busqueda

## Definición

Un problema de búsqueda consiste en:
- Un **espacio de estados**.
- Un **modelo de transición**.
- Un **estado inicial**.
- Una **prueba de objetivo**.
- Una **función de costo de ruta**.

## Elementos del problema

- **S**: Conjunto de estados \( S = \{s_1, ..., s_n\} \)
- **S_f**: Conjunto de estados finales \( S_f \subseteq S \)
- **A**: Conjunto de acciones \( A = \{a_1, ..., a_n\} \)
- **Modelo**: Definido por:
  - **Acciones legales**: \( S \rightarrow P(A) \) (va del conjunto S al conjunto potencia de A).
  - **Transición**.
  - **Costo**.

## Ejemplo: Pac-Man

Para un problema de búsqueda en Pac-Man:
- \( S = \{p, t_1, ..., t_n\} \)
- \( p \in \{0,1,2,3,4,5,6,7,8,9\} \)
- \( t_i \in \{0,1\} \)
- \( S = \{p_1, ..., p_9\} \)
- \( p_i \in \{0,1\} \), con \( |S| = 9 \times 2^8 \)

## Problema de los Botes

### Definición
Imagina que tienes dos botes \([A, B]\), donde:
- \( A = [a_{max}, cantidad] \)
- \( B = [b_{max}, cantidad] \)
- Se pueden realizar las siguientes acciones:
  - **Llenar(A)**, **Llenar(B)**
  - **Vaciar(A)**, **Vaciar(B)**
  - **Transvasar(A, B)**, **Transvasar(B, A)**
- **Cardinalidad del estado**: \( |X| = 8 \times 6 = 48 \)

### Ejemplo: Llenar 4 litros

1. Comenzamos con \( x = [0,0] \)
2. Posibles acciones legales:
   - \( Llenar(A) = [7,0] \)
   - \( Vaciar(A) = [0,0] \)
   - \( Llenar(B) = [7,5] \)
   - \( Transvasar(A, B) = [2,5] \)

Ejemplo de transiciones:
- De \( [7,5] \) a \( [0,5] \), luego \( [5,0] \)
- De \( [2,5] \) a \( [0,5] \), luego \( [2,0] \)

El objetivo es llegar a \( [4, x] \) para cumplir con la restricción del problema.
