# Arboles de decision
### Arbol binario
  Dividir en el atributo X con el valor t  
    Una rama : X < t  
    Una rama : X >= t  
  Requiere un pequeño cambio  
    Permitir repetidas divisiones en la misma variable a traves del recorrido.  
### Los arboless binarios llegan a una profundidad mayor muy rapido  
Solo los arboles pueden soportar variables cualitativas  
Los arboles que estan en skipiklear estan hechos para numeros  

## Criterio ganancia de entropia  
Entropia la medida de ganacia de informacion  
Ejemplo de entropia:  
  Xa = [10,10,5] -> [8,10,4] , [2/0/1]  
  Xb = [10,10,5] -> [7,7,0],[1,0,4],[2,3,1]  
  H(<10,10,5>) = -10/25 ln_2(10/20) - 10/25 ln_2(10/25) - 5/25ln2(5/25)  
  H(<10,10,5>|Xa) = 22/25 [-8/22ln_2(8/22) - 10/22 ln_2(10/22) - 4/44 ln_2(4/22) ] + 3/25[-2/3ln_2(2/3) - 0*ln_2(0) - 1/3 ln_2(1/3)]  

  H(<10,10,5>|Xb)14/25[-1/2ln_2(1/2) -1/2ln_2(1/2) - 0] + 5/25[-1/3ln_2(1/3) -0 -4/5ln_2(4/5] + 6/25[-1/3ln_2(1/3) -1/2ln_2(1/2) -1/6 ln_2(1/6)]
### De estos dos resultados Xa y Xb tu necesitas restarselo a H-Xa y a H-Xb y quedarte con el que tenga el residuo mayor por que es el que itne mayor ganancia de informacion

## Arboles cualitativos
para ej ejercicio, mi conjunto de datos es una lista D = [d1,...,dn]  di = ['a1': V1, ..., 'am':Vm]  
Una lista de diccionarios donde cada diccionario representa una instancia.  
CAda diccionario tiene al menos un par de llave-vLOR, donde la llave es elnombre de un atributo y el valor es el valor del atributo
Totodos los diccionarios tienen la misma llava-valor  
target: str  
  El nombre del atributo que se quiere predecir.  
clase default: str  
  El valor de la clase default  
Max_profundidad: int
  la maxima profundidad del arbol. Si es none no hay limite de profundidad.  
acc_nodod : int  
  El porcentaje de acierto minimo para considerar un nodo como hoja  
### Como modelar el arbol?? :

Necesitamos un nodo raiz que tenga enlace a sus hijos tal que sus hijos tengan nodos hojas, no necesito que esten doblemente enlazados.  
  
     atributos = list(datos[0].keys())
     atributos.remove(target)

     criterios para determinar si es nodo hoja
     if len(datos) == 0 or len(atributos) == 0:
       return NodoQ(termional = True, clase_default=clase_default)
    clases = Counter(d[target] for d in datos)
    clase_default = clases.most_common(1)[0][0]

    if (max_prfundidad == 0 or
      len(datos) <= min ejemplos or
      clases.most_common(1)[0][1] / len(datos) >= acc_node:

      return NodoQ(terminal=True, clase_default = clase_default)

