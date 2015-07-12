## Registradores de la JVM



Hablando un poco sobre los tipos de datos que son almacenados en la JVM y su tamaño. Es necesario tambien que se tenga el concepto de donde son almacenados tales informaciones. La JVM usa registros para almacenar varias cosas siendo que para todo tipo de dato existe un lugar específico. Durante la ejecución de un programa existen registros que son compartidos entre toda la JVM y otros que tiene la visibilidad del `Thread` actual.

![Los registros de JVM, Method Area y Heap son compartidas por toda la JVM y Program Counter, Stack Java y Stack Nativo cada Thread posee la suya.](imagens/chapter_3_1.png)