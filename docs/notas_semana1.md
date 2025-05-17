El ejercicio de la rumba en el cuarto {A/B}, donde
A={S/L} (la cardinalidad es 2)
, B={S/L}, donde la aspiradora es X={A/B}
X= A*B*X = 8 cardinalidad

para la percepcion
Pt = (localizacion, situacion de la loc)
Percepts : location A, state S

para saber si limpiar
A ={limpiar, ↓,→,↑,←,No}

Agente aleatorio  

/**********************************/
Ejemplo de la clase:  
class Entorno:  
  """  
   CLase abstracta para entornos  
   En realidad funciona como un  


def accion_legal(self, s, a):  
    """  
     @param s: una tupla con un estado legal del entorno  
     @param a : una accion en el entorno  
     @return: True si accion es legal en el estado  

def transicion(self, s, a):  

   """  
     @param s: una tupla con un estado legal del entorno  
     @param a : una accion en el entorno  
     @return: True si accion es legal en el estado  

class Agente(object):  



def simulador(entorno, agente, s, T=10, c=0):  
   """  
    @param entorno: una objeto de la clase entorno  
    @param agente: un objeto de la clase agente  
     @param s : tuple con un estado legal del entorno  
     @return T: numero de pasos a simular  
     @param c : el costo  
     @return: una lista de tripletas con la accion, estado y costo total  

/********************************/








