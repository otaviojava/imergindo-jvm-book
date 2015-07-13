
## Registros de la JVM



Hablaremos un poco sobre los tipos de datos que son almacenados en la JVM y de su tamaño. Es necesario también que se tenga referencia de donde son almacenadas dichas informaciones. La JVM usa registros para almacenar varias cosas teniendo para todo tipo de dato una ubicación específica. Durante la ejecución de un programa existen registros que son compartidos entre toda la JVM y otros que tienen visibilidad del `Thread` actual.

![Los registros de la JVM, Method Area y el Heap son compartidos por toda la JVM; el PC Counter, La Pila Java y la Pila Nativa si son por cada Thread](imagens/chapter_3_1.png)

