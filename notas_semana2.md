# Machine Learning
at = f(pt ; α)

f : X -> Y yo recivo una percepcion que puede estar en algun espacio y devuelvo un valor
yo asumo que f existe, una funcion que me permita detectar algo

Existira la funcion que siempre me determine cuando darle credito a un cliente, (probablemnte no), pero si hay una que es suficiente

## El aprendizaje maquina es cuando no tienes otra opcion!
si ya existe esa via es la mas practica

El aprendizaje que estamos viendo es un metodo inductivo y no se puede decir que una regla inductiva es verdadera o falsa
"Siempre va a salir el sol por el este por tal y tal" = deductivo
inductivo es a partir de otros axiomas que asumes verdaderos 
 ejemplo un programa que haga un programa
 X = {x1,x2,...,xn}
 tomar una muestra de la distribucion descnoncida
 D={(x1,y1),(x2,y2),...,(xn,yn)} ejemplo el cliente 1 pago1, el cliente 2 pago 2

 tengo aveces errores de medicion, involuntarios y voluntarios por el compadre
 y que es lo que pasa:
  yi = f(xi) + e , y el error es una variable aleatoria desconocida
  Y que quiero hacer con esto??, encontrar una h que pertenesca a un conjunto H tal que:
  hεH, h: X -> Y, talque h* ≈ f
  sup. h3,5= 3x+5, h3,4 = 3x +4 puede tomar otros valores
  hw0w1 = w1*x + w0
  el aprendizaje es encontrar el valor de w1 y w0

  "Machine learning: Field of study that gives computers the ability to learn without bieng program"

  TMitchel:
    Well-posed Learning Problem: A computer program is said to learn from experience E with respect  
    to some task T and some perfromance measure P, if its performance on T, as measured by P,  
    improves with experience E.  
    "se dice que aprende si el desempeño mejora al aplicar la experiencia"

funciones de estimacion para un set de graficos en un f(x):
  y = w1x + b
  y = w1x + w2x^2 + b
  y = w1x + w2x^2 + w3x^3 + w4x^4 + b
  "al tener 2 explicaciones del mismo fenomeno siempre hay que escojer la mas simple"-monje chino japones de inglaterra
### Aprendizaje = "es tratar de miniminizar el error en los datos que No tengp"

Error en muestra Ein = 1/N Σe(yi,y(gorro)i) yi = lo que estime, y(gorro)= lo que tengo
Error fuera de muestra Eout = Exε X[e(y,y(gorro))]
El aprendizaje existe si y solo si Eout ≈ 0
esto solo es posible si:
   Ein ≈ 0
   Ein ≈ Eout el promedio en mi muestra se parece al promedio en todos los dados
   Hacer los errores suficientemente chiquitos y tener confianza que Ein ≈ Eout

## K vecinos proximos
datos de un scatrerplot de terremotos y explosiones donde se tienen puntos blancos de terremoto y negro de explosiones
clase del punto mas cercano, busco el punto mas cercano y si es positivo digo que lo es
Mejor con los 5 vecinos mas cercanos para determinar el area de explosivo y de terremoto para poder generalizar mejor


 ## Un mundo en una dimension
 los vecinos mas cortos funcionan bien para bajas dimensiones
  sign(x):
     if x >= 0:
      return 1
     return 0
  
 ^y = h_w1,w0(x) = sign(w1x + w0)
es decir esta va a ser mi H, o decir que voy a escoger una red neuronal, becinox proximos etc.
H= mi funcion, theta= los parametros de mi funcion

## para medir los datos mal clasificados
usamos una funcion de error:
   Ein(h)= 1/m Σ Perdida(yesperada,h(xesperada))

E0(h) = Esperanza_x_en_X[Perdida(f(xespe), h(xespera)] //esta es la funcion que quiero pero no la puedo hacer

### desir que hay aprendizaje es poder asegurar que Ein ≈ Eout

### Recapitulando
Ei(h*) ≈ 0
Problema de optimizacion
Encontrar h* equivalente a encontrar el vector

si Ein ≈ Eout vamos a desir que el aprendizaje es probablemente aproximadamente correcto(PAC Learning)

## Desigualdad de Hoeffding
Pr[E0(h*)-Ei(h*)[>=ε]<= 2exp(-2ε^2 * M)]
{la probabilidad que no se parescan es menor o igual a esto}
donde m es el numero de datos y ε la diferencia entre el eerror en  muestra y el error fuera de muestra impuesto.

### Entonces el planteamiento
Ein(h*) ≈ Eout(h*) es PAC

### Traaduciendo
Pr[|E0(h*)-Ei(h*)|>=ε] <= PR[Union_h_en_H |E0(h) -Ei(h)| >= ε]

### El problema del aprendizaje queda como:
Pr[|E0(h*)-Ei(h*)|>=ε] <= 2Nexp(-2ε^2 *M)
donde N es el numero de hipotesis posibles en el conjunto H
