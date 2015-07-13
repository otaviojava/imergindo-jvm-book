#### Heap Space



Luego de que una instancia es creada, la información de su objeto es guardado aqui, y ese espacio de memoria también es compartido entre los `Threads`. El **heap** tiene un mecanismo que reclama memoria en tiempo de ejecución, moviendo los objetos  y evitando la fragmentación de espacio.


![Representación de uma variable de tipo de referencia en el Heap](imagens/chapter_3_8.png)


La representación de una variable de tipo de referencia en el **Heap** es diferente de los tipos primitivos, ellos tienen un mecanismo muy similar a los punteros en `C/C++` ya que no poseen la información, sino que apuntan a la ubicación que posee. El objeto de referencia está constituído de dos punteros menores:

* Uno que apunta al pool de objetos, ubicación donde esta la información.
* El segundo apuntará a su constant pool (que posee la información de la clase, sus atributos, métodos, encapsulamientos, etc.) que serán localizados en **method Area**.



La representación de los vectores se comportan de forma similar a las variables de referencia, mas ellos tienen dos campos adicionales: 

1. 
El **tamaño**, que define el tamaño del vector
2. 
Una **lista de referencia** que apunta a los objetos que estan al interior del vector


![Representación de un vector al interior del Heap](imagens/chapter_3_9.png)


