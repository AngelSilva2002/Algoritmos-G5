Lab G5

Solución a las preguntas:

5. Cómo reacciona su algoritmo a variadas funciones de optimización (lineal, oscilantes(varias frecuencias), etc)?
En nuestro algoritmo podemos ver que los valores en la conversión de los genes del individuo en binario a decimal convergen al número 1 sin importar el tipo de función sea lineal, cuadrática, polinómica o oscilante.Esto ocurre en la primera generación y mientras van aumentando las generaciones la aglomeración de individuos se va moviendo de a poco hacia un lado de la gráfica, este movimiento es hacia el máximo de la gráfica.
También podemos notar que en todas las posibles gráficas el error promedio de cada generación va disminuyendo en algunas el error disminuye exponencialmente, lineal o cuadrático. Tiene el resultado esperado en las diferentes funciones ya que a mayor generaciones el error va bajando.
Analizando la gráfica de mejor individuo de cada generación podemos ver que en todas las gráficas los individuos convergen a un valor, si la generación no es tan alta estos valores convergen a 1 evidentemente, y va disminuyendo o aumentando la convergencia dependiendo de la función. Tiene el resultado esperado en las diferentes funciones ya que a mayor generaciones el mejor individuo va obteniendo el valor máximo. Por ejemplo en una función cuadrática el mejor individuo aumenta y en una función oscilante convergen con el máximo y al pasar de las generaciones se nota menos dispersión.

6. Concluya y Describa, por sus experimentos, como están relacionados los parámetros de configuración de su algoritmo, con el costo en (tiempo y espacio).
Generaciones = (Directamente proporcional) Al incrementar el numero de generaciones que queremos simular, existira un mayor gasto en cuestión de tiempo y espacio, esto debido a que este valor se usa en un ciclo en el rango del numero de generaciones que se tienen, por lo tanto al aumentar este numero se generaran mas ciclos, y al aumentar los ciclos aumenta el costo computacional tanto en tiempo y en espacio. 
TGI = (Directamente proporcional) Este parametro al aumentar, permite que el costo de espacio y tiempo tambien aumente
Tp = (Directamente proporcional) Al incrementar el tamaño de la población, el costo computacional realiza un gasto en tiempo y espacio debido a que este se usa para asignarle un valor aleatorio a cada individuo dependiendo del rango de busqueda y del tamaño. 
ProbMut = Al variar este parametro el costo computacional no varia de manera significativa, ya que este es una variable que solo se usa 
para realizar operaciones
FuncionOptimizar = Este parametro indica la función que se busca optimizar, y al variarla no afecta de manera significativa el costo 
computacional del algoritmo
RangoBusqueda = (Directamente proporcional) al variar el rango de busqueda, si se incrementa el costo computacional incrementa un poco ya que hace que el rango para realizar la busqueda del optimo sea mayor.

7. ¿Qué parámetro considera usted más relevante para acelerar la convergencia de la búsqueda?
Se considera principalmente relevante para el algoritmo el Tamaño del Genoma de los individuos así como la probabilidad de mutación en los mismos pues entre mayor sea el tamaño del genoma de la población hay mayor precisión en los datos obtenidos y esto puede afectar el tamaño de los "saltos" negativamente pero al mismo tiempo puede evitar que los valores rodeen mucho al valor esperado sin acercarse a él, por otro lado, la probabilidad de mutación debe mantener un balance pues si es muy alta evita que los valores converjan rapidamente pero por el contrario si este parametro es muy bajo, no permite la libre variación dentro del sistema. Además es importante mencionar que si se aumenta el número de descendencia por generación, esto aumenta el número de individuos y acelera así la convergencia (a costa de recursos) hacia el valor buscado.
