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

## Recapitulando
Decimos que f ≈ h* si:
      Ei(h*) ≈0  
      y  
      E0(h*)≈Ei(h*)  
 Ein(theta) = 1/M Σ Perdida(yi, h_theta(yi))
 Eout(theta) = E_x_ε_X[Perdida(f(x), h_theta(yi))]
Ein(theta)≈0, Ein(theta) ≈ Eout(theta)  
              estimacion ≈ error  
 ### La probabilidad de que el error promedio en todos mis datos es , es algun numero menor o igual a ke^(-ε^2 * M)
PR[|Eout(theta) - Ein()theta|> ε] = < ke^(-ε^2 * M)  

### Entonces para que el aprendizaje sea posible necesito muchos datos
pero tambien me interesa mas
PR[Union |Eout(theta)-Ein(theta)| > ε]

un evento es cualquier subconjunto de posible salida  
una funcion de probabilidad es:
P: P -> R  
P(A) >= 0  
P(vacio) = 0  
P(U) = 1  
P(AUB) = P(A) + P(B) - P(AinterseccionB)  
tal que:  
PR[Union |Eout(theta)-Ein(theta)| > ε] <= ΣPr[Eout(theta)-Ein(theta)| > ε]  
## Y el problema de aprendizaje queda como...
Pr[|E0(h*)-Ei(h*) >= ε]...

## Clasificacion binaria
h0: X -> {-1,1}, h0εH  
Una gran cantidad de transplantes entre diferentes hipotesis  
Respecto al conjunto de aprendizaje, muchas hipotesis son iguales  

## Dicotomias
Hipotesis h : X ->{-1,1}, h0 ε H  
H = un conjunto de funciones que se van a estar aplicando en esl espacio X -> {-1,1}  
Dicotomia  
h: {x(1),...,x(M)} -> {-1,1}, h0 ε H(x(1),...,x(M))  
|H| = infinito  

## La funcion de crecimiento
m_H(M) = max_(x(1),...,x(M) ε X) |H(x(1),...,x(M))|  
Acotando a m_h(M) < 2^M  

la cardinalidad depende de la funcion que estoy utilizando y mis puntos  
la funcion de crecimiento me da la maxima cardinalidad posible  

2^4 - 2 = respuesta a como podemos dividir los puntos

h(x) = sign(w1x1 + w2x2 + b)  
X = R^2  
card(H)= infinito  
m_H(1) = 2  
m_h(2) = 4 = 2^2   
m_h(3) = 8 = 2^3  tal que la dimension VC de esta formula va  a ser 3  
mh+h(4) = 14 < 2^4 ... a partir de aqui no me puedo aprender de memoria la cardinalidad de los datos  

m_H(M)<= 2^M  
puesdo desir que el crecimiento es de notacion O(M^(dvc))
## La dimension VC  
d_vc(H) es el valor ,as grande de M para el cual m_H(M) = 2^M  
Para cualquier conjunto {x1,...,x(m)} ε X  
Para cualquier asignacion f(x) ε {-1,1}  

## REgla de oro
si el conjunto de datos es 10 veces la dimencion vc significa que aprendo
M >= 10d_vc  
Necesito comprimir la informacion al menos 10 veces para poder decir que aprendi algo  


## Reacpitulacion
 ### 23/01/2025  
 Y_gorro  = w1x1 + w2x3 + b  
### Necesito datos para aprender
 Cuantos datos?  
 Cual es mi funcion?  
 Entre mas complicado el modelo se necesitan mas datos  
 Necesito muchos datos y una funcion que cuando la utilice el error se haga chiquito  
 Necesito un modelo y que se pueda ajusta, el numero de datos es 10 veces la dimension VC  
 El numero total de parametros multiplicadao por 10 = el minimo numero de datos que necesitamos  

 ## Arboles de decision:
 ### Hypotesis : decision trees f: X-> Y  
 explicar los fenomeno a traves de los arboles de decision, es explicar los datos.  
 El numero de arboles si tienes n variables con 2 estados el numero de arboles que puedes hacer es 2^(2^n)  
 Aprender de el arbol mas chico es un problema NP-complete [Hyafil & Rivest]  

 Heuristica:  
   -Empieza de un arbol de decision vacion  
   - Divide en el mejor 
 
