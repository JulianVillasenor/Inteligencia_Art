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


  
X = {x1,x2,....,xm} ε R^n
Y = {y1,y2,....,ym} ε {-1,1}

donde:
xi = {x1,x2,....,xm}
yi = f(xi) + ei
h* : R^n -> {-1,1}, h ε H
tal que h* ≈ f

Que es H?
como mido h≈f?
Como encuentro h*?

para clasificacion lineal binaria:

y^ = h_w(x) = sign(w1x1 + w2x2 + ... + wnx2 + w0).
H = {h_w|wεR, h_w(x)=sign(Σwixi + w0)}

Ejemplo, tengo a Y y Y^estimados  
Y = {y1,y2,..,ym}
Y^ = {y^1,y^2,..,y^m}
0/1 - loss(y,y^) = {o si y=y^, 1 en otro caso}  

la funcion de perdida es:  
Ein(h_w)= 1/M Σ0/1 - loss(y,h_w(xi))

Pr(Y=1|x;w)= a(x) = Θ(w1x1 + ... + wnxn + w0)

y = {1 si a(x)>c, -1 else}

lim z-> infinito Θ(z) =0  
lim z-> infinito Θ(z) =1  
0 estrictamente creciente  
0(z) = 1/1 + e^-z  

a(x) = [[Pr(Y=1|x;w)],
Pr(Y=2|x;w),
...
Pr(Y=m|x;w)]

si yi = 1  
   loss(yi,y^i) = -log(y^i)  
si yi = 0  
   loss(yi,y^i) = -log(1-y^i)  
tal que la formula general es: yi log(y^i) + (1-yi)log(1-y^i)  

yo necesito a las w obtimas .  
w* = arg min{wεR} 1/M Σ - yi log(y^i) + (1-yi)log(1-y^i)  
donde:  
y^i = Θ(zi) = 1/1 + e^-zi  
zi = w1x1 + w2x2 + .. + wnxin + w0 = wit w + b  
w <- wins  
para epocho de 1 a max_epochs  
   (gradiente de w)J(w) = ▼wJ(w) <- calcular el gradiente (X,Y,w,b)  
   dJ(w)/db <- calcula derivada (X,Y,w,b)  
   w <- w - n(gradiente de w)J(w)  
   b <- b - ndJ(w)/db  
   si||▼wJ(w)|1↑ < e_tot :  
     regresa w,b  
     
