Punto #2
Complejidad :

n_hidden = 2 # Número de unidades en la capa escondida                                                 #O(1)
epochs = 1000000000 # Número de iteraciones sobre el conjunto de entrenamiento                               #O(1)
alpha = 0.01 # Taza de aprendizaje                                                                     #O(1)

ult_costo = None                                                                                       #O(1)

m,k = features.shape # Número de ejemplos de entrenamiento, número de dimensiones en los datos         #O(1)
# Inicialización de los pesos
entrada_escondida = np.random.normal(scale = 1/k**0.5,size = (k,n_hidden))                             #O(1)
escondida_salida = np.random.normal(scale = 1/k**0.5,size = n_hidden)                                  #O(1)
print(entrada_escondida.shape)                                                                         #O(1)
print(escondida_salida.shape)                                                                          #O(1)
# Entrenamiento
for e in range(epochs):                                                                                #O(n)
    # Variables para el gradiente
    gradiente_entrada_escondida = np.zeros(entrada_escondida.shape)                                    #O(1)
    gradiente_escondida_salida =  np.zeros(escondida_salida.shape)                                     #O(1)
    # Itera sobre el conjunto de entrenamiento
    for x,y in zip(features.values,targets):                                                           #O(n)
        # Pasada hacia adelande (forward pass) or forward propagation
        z = sigmoide(np.matmul(x, entrada_escondida))                                                  #O(1)
        y_ =sigmoide(np.matmul(escondida_salida,z)) # predicción                                       #O(1)
        # Pasada hacia atrás (backward pass)
        salida_error = (y - y_) * y_ *(1- y_) #error * derivada de la funcion sigmoide                 #O(1)
        escondida_error = np.dot(salida_error, escondida_salida) * z * (1 -z)                          #O(1)

        gradiente_entrada_escondida += escondida_error * x[:,None]                                     #O(1)
        gradiente_escondida_salida += salida_error * z                                                 #O(1)
    # Actualiza los parámetros (pesos)
    entrada_escondida += alpha * gradiente_entrada_escondida / m  #alpha = tasa de aprendizaje         #O(1)
    escondida_salida +=  alpha * gradiente_escondida_salida / m                                        #O(1)

    if e % (epochs / 10 ) == 0:                                                                        #O(1)
        z = sigmoide(np.dot(features.values, entrada_escondida))                                       #O(1)
        y_ = sigmoide(np.dot(z, escondida_salida))                                                     #O(1)

        # Función de costo
        costo = np.mean(( y_ - targets)**2 )                                                           #O(1)

        if ult_costo  and ult_costo < costo:                                                           #O(1)
            print("Costo de  entrenamiento: ", costo, " ADVERTENCIA -  Costo subiendo")                #O(1)
        else:
            print("Costo de entrenamiento: ", costo )                                                  #O(1)
        
        ult_costo = costo                                                                              #O(1)

#  Precisión en los datos de prueba 
z = sigmoide(np.dot(features_test, entrada_escondida))                                                 #O(1)
y_ = sigmoide(np.dot(z, escondida_salida))                                                             #O(1)

predicciones =  y_ > 0.5                                                                               #O(1)
precision = np.mean(predicciones == targets_test)                                                      #O(1)
print("Precisión: {:.3f}".format(precision))                                                           #O(1)

9O(1) + O(n)[2O(1) + O(n)[6*O(1)] + 8O(1)] + 5O(1)
O(n^2)

Los parametros que más afectan el tiempo de ejecicion del entrenamiento son el número de iteraciones y el tamaño de datos que se muestran (train_data) ya que de estos depende la ejecucion de los ciclos for y por tanto entre mas grandes sean, mas tiempo de ejecución llevará el algoritmo de entrenamiento.

Punto #3
El experimento fue realizado con un ciclo for extra en el que hacemos un entrenamiento de acuerdo a cada numero de epocas hasta 50. Observamos que al algoritmo le basta con entre 40 y 50 epocas o iteraciones para llegar a un valor de precisión aceptable.

Punto #4
Tenemos que al cambiar la función de activación de una sigmoide a una tangente hiperbólica el costo de entrenamiento sube lo cual no es óptimo para el entrenamiento de esta red neuronal. Del mismo modo tenemos que la precision lograda es la misma que con la función sigmoide por lo tanto, es mejor hacer uso de la función sigmoide.
