Punto #2
Complejidad :

9O(1) + O(n)[2O(1) + O(n)[6*O(1)] + 8O(1)] + 5O(1)
O(n^2)
Los parametros que más afectan el tiempo de ejecicion del entrenamiento son el número de iteraciones y el tamaño de datos que se muestran (train_data) ya que de estos depende la ejecucion de los ciclos for y por tanto entre mas grandes sean, mas tiempo de ejecución llevará el algoritmo de entrenamiento.

Punto #3
El experimento fue realizado con un ciclo for extra en el que hacemos un entrenamiento de acuerdo a cada numero de epocas hasta 50. Observamos que al algoritmo le basta con entre 40 y 50 epocas o iteraciones para llegar a un valor de precisión aceptable.

Punto #4
Tenemos que al cambiar la función de activación de una sigmoide a una tangente hiperbólica el costo de entrenamiento sube lo cual no es óptimo para el entrenamiento de esta red neuronal. Del mismo modo tenemos que la precision lograda es la misma que con la función sigmoide por lo tanto, es mejor hacer uso de la función sigmoide.