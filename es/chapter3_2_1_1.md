##### Stack variables


Cada **frame** contiene un vector para almacenar las variables locales y/o parámetros, su tamaño es definido en tiempo de ejecución. En dicho vector las variables `double` y `long` ocupan dos elementos del vector y son guardado consecutivamente. Las variables de tipo `int` y `returnAdress` ocupan un elemento del vector (`byte`, `short` y `char` son convertidos a `int`). En caso el método sea de instancia, no sea estático, el primer elemento del vector será ocupado por la instancia que está ejecutando dicho método y a continuación los parámetros, en el orden que fueron pasados. En caso el método sea de classe, el método sea estático, no habra referencia de la instancia que llama al método, de modo que el primer elemento seran los parámetros.


![Las pilas de variables son compuestas por indices de 32 bits, de modo que las variables de tipo double y long ocupan dos espacios continuos y las otras variables apenas uno.](imagens/chapter_3_4.png)

