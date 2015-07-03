##### Stack Operand


Como su nombre indica, ese registro sirve para guardar las instrucciones que ocurren al interior de un método, como el registro de variables locales, los valores son almacenados en un vector,  más sus valores son recuperados removiendo el último elemento del vector en lugar de usar el indice. Esto es basado en la estructura de datods de la Pila (Primero en entrar es el último en salir). El tamaño de las variables sucede de manera semejante a las variables locales.

![Pila de operaciones, semejante a su “hermano”, su unidad posee el tamaño de 32 bits, su paso a paso sigue el estilo de una pila convencional, es decir, el último en entrar es el primero en salir. En el ejemplo se utiliza la suma de dos enteros ( 10 y 20).](imagens/chapter_3_5.png)
Pila de operaciones, semejante a su “hermano”, su unidad posee el tamaño de 32 bits, su paso a paso sigue el estilo de una pila convencional, es decir, el último en entrar es el primero en salir. En el ejemplo se utiliza la suma de dos enteros (`10` y `20`).


![Como la pila de operaciones esta compuesta por unidades de 32 bits, entonces para double y long se ocupara dos unidades contiguas, en este ejemplo se suman dos doubles ( 10.10 y 20.20)](imagens/chapter_3_6.png)
Como la pila de operaciones esta compuesta por unidades de 32 bits, entonces para double y long se ocupara dos unidades contiguas, en este ejemplo se suman dos doubles (`10.10` y `20.20`)