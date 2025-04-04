# Documento Informativo: Procesos de Decisión de Markov (MDPs)

### Introducción a los MDPs y su Contexto
- Los MDPs se definen como un modelo matemático para la toma de decisiones bajo incertidumbre.
- Se distinguen de los problemas de búsqueda determinísticos, donde la acción en un estado siempre lleva al mismo estado siguiente. En los MDPs, las acciones en un estado pueden llevar a diferentes estados siguientes con ciertas probabilidades.
- Históricamente, los MDPs fueron introducidos en las décadas de 1950 y 1960, con la publicación del libro de Ronald Howard sobre *Programación Dinámica y Procesos de Markov* como un hito importante.
- El término "Markov" se refiere a Andrey Markov, ya que los MDPs son extensiones de las Cadenas de Markov, pero incorporan la capacidad de tomar decisiones (acciones).

### Aplicaciones de los MDPs
Se pueden aplicar en diversas áreas donde los MDPs son aplicables debido a la presencia de incertidumbre en la toma de decisiones:
- **Robótica**: Decidir dónde mover un robot, considerando posibles fallos de actuadores u obstáculos inesperados.
- **Asignación de recursos**: Decidir qué producir ante la incertidumbre de la demanda del cliente.
- **Agricultura**: Decidir qué plantar, dada la incertidumbre del clima y su impacto en el rendimiento de los cultivos.

### El Juego de Dados como Ejemplo
Se introduce un juego de dados como un ejemplo concreto para ilustrar los conceptos de los MDPs.

**Reglas del juego**:
- En cada ronda, el jugador puede elegir entre "quedarse" (*stay*) o "salir" (*quit*).
  - Si elige "salir", recibe \$10 y el juego termina.
  - Si elige "quedarse", recibe \$4 y se lanza un dado de 6 caras.
    - Si el resultado es 1 o 2, el juego termina.
    - Si el resultado es 3, 4, 5 o 6, el juego continúa a la siguiente ronda.

**Análisis**:
- Se analizan las recompensas totales (utilidad) y la probabilidad de obtenerlas al seguir la política de "quedarse" continuamente. Se calcula la utilidad esperada de esta política:  
  Expected utility: 1/3 (4) + 2/3 · 1/3 (8) + 2/3 · 2/3 · 1/3 (12) + · · · = 12  

- También se calcula la utilidad esperada de la política de "salir" inmediatamente:
  Expected utility: 1(10) = 10


**Formalización del juego como MDP**:
- Estados: `"in"`, `"end"`
- Acciones: `"stay"`, `"quit"`
- Transiciones:
in,quit → end (1): $10  
in,stay → in (2/3): $4  
in,stay → end (1/3): $4


### Definición Formal de un Proceso de Decisión de Markov (MDP)
Un MDP incluye los siguientes elementos:
- **States**: El conjunto de todos los posibles estados.
- **s_start ∈ States**: El estado inicial.
- **Actions(s)**: El conjunto de acciones posibles en el estado `s`.
- **T(s, a, s')**: La probabilidad de transicionar al estado `s'` al tomar la acción `a` en el estado `s`.
- **Reward(s, a, s')**: La recompensa obtenida por la transición de `s` a `s'` al tomar la acción `a`.
- **IsEnd(s)**: Función que indica si el estado `s` es un estado terminal.
- **0 ≤ γ ≤ 1**: El factor de descuento (*gamma*), que determina la importancia de las recompensas futuras en comparación con las recompensas inmediatas.

### Comparación con Problemas de Búsqueda
- **Succ(s, a)** en problemas de búsqueda corresponde a **T(s, a, s')** en MDPs.
- **Cost(s, a)** en problemas de búsqueda corresponde a **Reward(s, a, s')** en MDPs.
- La principal diferencia radica en la incertidumbre de las transiciones y la presencia de recompensas en los MDPs.

### Transiciones y Probabilidades
- Las probabilidades de transición `T(s, a, s')` deben sumar uno para cada estado `s` y acción `a`:  
For each state s and action a: Σs'∈States T(s, a, s') = 1

- Se define el concepto de **sucesores** como los estados `s'` para los cuales `T(s, a, s') > 0`.

### ¿Qué es una Solución para un MDP?
A diferencia de los problemas de búsqueda donde la solución es una secuencia de acciones (un camino), la solución para un MDP es una **política**.

**Definición**:
- Una política `π` es un mapeo de cada estado `s ∈ States` a una acción `a ∈ Actions(s)`.

### Evaluación de una Política
- Seguir una política en un MDP genera una trayectoria aleatoria de estados, acciones y recompensas.
- **Utilidad**: Suma (posiblemente descontada) de las recompensas obtenidas a lo largo de esta trayectoria.
- **Valor (utilidad esperada)**: Valor esperado al seguir una política desde un estado.

### Descuento (Discounting)
- El factor de descuento (`γ`) modela la preferencia por recompensas inmediatas sobre recompensas futuras.
- La utilidad descontada de una trayectoria se calcula como:

  u1 = r1 + γr2 + γ²r3 + γ³r4 + · · ·  

### Valor y Q-Valor de una Política
- **Valor de una política (`Vπ(s)`)**: Utilidad esperada al seguir la política `π` desde el estado `s`.
- **Q-valor de una política (`Qπ(s, a)`)**: Utilidad esperada de tomar la acción `a` en el estado `s` y luego seguir la política `π`.

**Relaciones recursivas**:
Vπ(s) = Σs' T(s, π(s), s')[Reward(s, π(s), s') + γVπ(s')]  
Qπ(s, a) = Σs' T(s'|s, a)[Reward(s, a, s') + γVπ(s')]  


### Evaluación de Políticas (Policy Evaluation)
Algoritmo iterativo para calcular el valor de una política dada:

1. Inicializar `V(0)π(s) = 0` para todos los estados `s`.
2. Para cada iteración `t = 1, ..., tPE`:
   - Para cada estado `s`:
     ```
     V(t)π(s) = Σs' T(s'|s, π(s))[Reward(s, π(s), s') + γV(t-1)π(s')]
     ```
3. Condición de parada:
   maxs∈States |V(t)π(s) - V(t-1)π(s)| ≤ ε


**Complejidad temporal**: `O(tPE * S * S')`, donde `S` es el número de estados y `S'` es el número máximo de sucesores.

### Ejemplo de Evaluación de Políticas en el Juego de Dados
- Se aplica el algoritmo a la política "quedarse" (asumiendo `γ = 1`).
- Convergencia de `V(t)π(in)` a `12`.

### Valor y Política Óptimos
- **Valor óptimo (`Vopt(s)`)**: Máximo valor que se puede obtener desde el estado `s` siguiendo cualquier política posible.
- **Relaciones**:
Qopt(s, a) = Σs' T(s, a, s')[Reward(s, a, s') + γVopt(s')]  
Vopt(s) = maxa∈Actions(s) Qopt(s, a) (para estados no terminales)


### Políticas Óptimas
- La política óptima se determina tomando la acción que maximiza el Q-valor en cada estado:
  πopt(s) = arg maxa∈Actions(s) Qopt(s, a)

  
### Iteración de Valores (Value Iteration)
Algoritmo iterativo para calcular el valor óptimo:

1. Inicializar `V(0)opt(s) = 0` para todos los estados `s`.
2. Para cada iteración `t = 1, ..., tVI`:
 - Para cada estado `s`:
   ```
   V(t)opt(s) = maxa∈Actions(s) Σs' T(s, a, s')[Reward(s, a, s') + γV(t-1)opt(s')]
   ```

**Complejidad temporal**: `O(tVI * S * A * S'*)`.

### Convergencia de la Iteración de Valores
- Si `γ < 1` o el grafo del MDP es acíclico, la iteración de valores converge al valor óptimo correcto.

### Resumen de Algoritmos
1. **Evaluación de Políticas**: Toma un MDP y una política, devuelve el valor de esa política.
2. **Iteración de Valores**: Toma un MDP, devuelve el Q-valor óptimo y la política óptima.

## Conclusiones Clave
- Los MDPs proporcionan un marco formal para la toma de decisiones secuenciales en entornos inciertos.
- Una política define la estrategia de un agente.
- El valor de una política mide la utilidad esperada de seguir esa política.
- La evaluación de políticas y la iteración de valores son algoritmos clave.
- El factor de descuento (`γ`) juega un papel crucial en la convergencia de los algoritmos.
