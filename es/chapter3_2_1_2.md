##### Stack Operand


Como el nombre indica, este registro sirve para almacenar las instrucciones que ocurren dentro del método, como registro de variables locales, los valores son almacenados en un vector pero sus valores recuperados por la eliminación del último elemento del vector en vez de ser por el índice. Este es basado en la estructura de datos de la pila -stack- (el primero en entrar será el último en salir). El tamaño de las variables es de manera semejante a las variables locales.

![Pila de operación, semejante a su “hermano”, su unidad posee un tamaño de 32 bits, su paso-a-paso sigue como una pila convencional, el último en entrar será el primero en salir. En este ejemplo se utilizará la suma de dos enteros ( 10 y 20).](imagens/chapter_3_5.png)
Pila de operación, semejante a su “hermano”, su unidad posee un tamaño de 32 bits, su paso-a-paso sigue como una pila convencional, el último que entra será el primero que sale. En este ejemplo se utilizará la suma de dos enteros ( `10` y `20`).

![Como la pila de operación está compuesta por unidades de 32 bits, si fuera double o long este ocupará las dos unidades seguidas, en este ejemplo son sumados dos doubles ( 10.10 y 20.20 )](imagens/chapter_3_6.png)
Como la pila de operación está compuesta por unidades de 32 bits, si fuera `double` o `long` este ocupará las dos unidades seguidas, en este ejemplo son sumados dos doubles ( `10.10` y `20.20`)
