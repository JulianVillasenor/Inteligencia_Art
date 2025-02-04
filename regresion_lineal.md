# Regresion Lineal
Es uno de los metodos mas antiguos de aprendizaje.  

X_1 pertenece a R^n, tal que:  
x_1 = {x_1_1,.....,x_1_n}, tal que:  
x_2 {x_2_1,.....,x_2_n} y_1  
x_3 {x_3_1,.....,x_3_n} y_2  
x_4 {x_4_1,.....,x_4_n} y_3  
x_5 {x_5_1,.....,x_5_n} y_4  
x_6 {x_6_1,.....,x_6_n} y_5  
x_m {x_m_1,.....,x_m_n} y_m  

si yo digo:  
x_1 = {x_1_1,.....,x_1_n} perteneciente a R^n  
Θ(x) = {Θ1(x),Θ2(x),Θ3(x),...,Θm(x)}  

Ejemplo:  
x = x1  
Θ(x)= {1 , xi}  
w= (w0, w1)  
hw(x) = (w0,w1) * (1 , xi) = w0 + w1x1.  

## Funcion de perdida  
"Mi mejor solucion es donde los errores son minimos"  
loss(y,y^) = 1/2(y-y^)^2  

Ein(hΘ) = 1/m Σloss(yi,hΘ(xi)), tal que:  
Ein(hΘ) = 1/m Σ1/2(yi - w^t Θ(xi))^2  
w* = argumento minimo; w pertenece a R^(n+1)  
1/2m Σ{1,m}(yi - Σ{1,n}wixi - w0)^2  
Tengo que encontrar los valores de la w talque la ecuacion de arriba sea la minima.  

## DEsenso de gradiente:  
El gradiente ▼w TrainLoss(w) es la direccion que incrementa la perdida de entrenamiento.  
El gradiente se aplica a una funcion que de un vector te da un numero.  
El gradiente de una funcion que depende de varios parametros y me regresa un solo valor:  
▼f(x,...,xn) = [[derivada(x,..xn)/derivadax1],  
               [....],  
               [....],  
               [derivadaf(x1,...,xn)/derivadaxn]]  
  ## Diferenciacion automatica  
  


