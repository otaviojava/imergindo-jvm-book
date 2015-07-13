## Hablando un poco sobre JVM


Ciertamente Java es actualmente unos de los lenguajes mas usados y populares del mundo, siendo su mayor diferencial no esta en el mismo lenguajes sino en la **JVM**, máquina virtual Java. La JVM viene siendo objeto de muchos estudios e investigaciones, despues de todo conocer bien la JVM va garantizar al desarrollador Java, maneras para sacar el mejor provecho del lenguaje y de la plataforma ademas de programar de manera mas eficiente teniendo en consideración todo lo que la JVM puede hacer por este y a ayudarte tambien. Con este objetivo estoy creando este pequeño texto, ayudar a la comunidad latinoamericana a conocer la  **JVM**.

Este material es fruto de mis trabajos junto con *OpenJDK*. La JVM open source es ,a partir de la versión 7, se convirtió en la implementación de la referencia. Al contrario de lo que muchas personas imaginan, existen millones de máquinas virtuales, entre las mas populares está el HotSpot (tambien conocida como la JVM de Oracle). OpenJDK es un projecto esta activo con la ayuda de muchas empresas(Oracle, Intel, RedHat, AMD, Google, etc.), pero principalmente com la grande ayuda de la comunidad, que entre las diversas fuentes de trabajo que existen podemos destacar el Adopte OpenJDK que pretende la evolución de la plataforma y  de Java Livre (ayudando la refactorización, evangelizando sobre OpenJDK, identificando y corrigiendo bugs). 


Para facilitar el entendimiento del lector esta trabajo fue dividido en seis partes:


 * 	La primera hablará un poco sobre Java, haciendo una correcta separación entre lenguaje, plataforma y maquina virtual ademas de hablar un poco sobre la historia de Java y de su evolución junto con las versiones.

* En seguida se hablará sobre el funcionamento básico de la JVM, se hará la  distinción básica entre el lenguaje Java y la máquina virtual, ya que la ultima necesita ser compilada para que el lenguaje sea multiplataforma, el ciclo de vida de la JVM y de los procesos en paralelo que nacen con una aplicación Java. 

* Saber donde queda cada información dentro de la JVM el el nombre de sus respectivos registros. Será el objetivo de esta tercera parte del trabajo. Sabrá cuales registros serán compartidos por todos los `Threads` y aquellos que no lo serán, asi nacen y mueren con su respectivo Thread. 

* El **bytecode**, el lenguaje de la Maquina virtual, poco es explicado sobre este, pero son gracias a sus opcodes que la JVM es multiplataforma. En esta parte se verá cuan diferente es y su código en Java y de su producto generado, el bytecode, además de la estructura que la clase adquiere despues el proceso de compilación.

* La **JVM** consiste en un proceso básico de coger la información de la clase, generar stream dentro de la JVM (Naturalmente en la memória principal) y ejecutar-lo o convirtiendo en código nativo, ese proceso de cargar una clase es realizada en tiempo de ejecución, o sea, solo es cargada la clase X en el momento en que esta fuera llamada, no es suficiente estar solamente en el import, si esa clase tiene un padre o implemente interfaces estas serán cargadas antes de la clase X. Toda clase posee un ciclo de vida y conozca un poco mas sobre este ciclo en la parte número cinco.
	
* Una gran diferencia de JVM es el recurso de la gestión automática de la a memoria, ese proceso consiste en liberar y recuperar memoria de los objetos que no estan mas siendo utilizados, ese es el papel del **Garbage Collector**. Conozca un poco mas sobre las implementaciones y en cuales situaciones ellas son mas aconsejables.

Para finalizar será demostrada una visión practica de JNI y del projecto OpenJDK ademas de los conceptos de compilar la JVM. 