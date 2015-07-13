
## Funcionamento básico de la JVM


Este capítulo hablará un poco sobre el funcionamiento básico de la JVM, que es el corazón del lenguaje java. Ella es la responsable por la independencia entre plataformas y ejecuta basicamente dos tipos de procesos:

* Lo escrito en java y que genera **bytecodes** 
* Lo nativo que es escrito en lenguajes como C\C++ y son *linkeados* dinámicamente para una plataforma específica.

Los métodos nativos son muy interesantes para obtener información del SO donde la JVM se esta ejecutando y de la cual se utiliza recursos.

Y es sobre esta base en que a pesar de que el lenguaje es **RunAnyWhere** la JVM no lo es, o sea, para cada plataforma existe una máquina virtual específica. Eso sucede, por ejemplo, para usar recursos específicos de la plataforma. Un ejemplo, son las llamadas distintas que existen para trabajar con directorios y archivos.



![La JVM necesita ser compilada para una plataforma específica.](imagens/chapter_2_1.png)



El único y principal motivo de la JVM es ejecutar el aplicativo. Cuando se inicia, una ejecución nace en la JVM y cuando la aplicación termina esta muere. Se crea una JVM para cada aplicación, o sea, si se ejecuta tres veces el mismo código en una misma máquina, se inician 3 JVMs. Para ejecutar una aplicación basta que su clase posea un método público estático con el nombre de main y tenga como parámetro un array de `String`.


Al iniciar una JVM existen algunos procesos que se ejecutan en paralelo y en background se ejecutan diversas operaciones y procesos para mantener a la JVM disponible:


* Los Timers que son responsables por los eventos que suceden periodicamente, por ejemplo, las interrupciones, las cuales son usadas para organizar los procesos que suceden continuamente. 
* Los procesos de Garbage Collector que son responsables por ejecutar las actividades del recolector de basura de la JVM.
* Compiladores que son los responsables en transformar bytecode a código nativo.
* Los oídores, que reciben señales (informaciones) y tienen como principal objetivo enviar dichas informaciones al proceso correcto dentro de la JVM.
 

Hablando más un poco sobre esos procesos paralelos o `Thread`, una JVM permite que múltiples procesos se ejecuten concurrentemente, esa rutina en Java está directamente relacionada con un `Thread` nativo. Tan pronto como un proceso paralelo en java nace, sus primeros paso son:


* Asignación de memoria
* Sincronización de objetos
* Creación de registros específicos para el mismo y la asignación de un `Thread` nativo. 
 
Cuando esa rutina genera una excepción, la parte nativa envía esa información para que la JVM se cierre. Cuando el `Thread` termina todos sus recursos específicos, tanto en Java como para la parte nativa, son entregados a la JVM.

Como un lenguaje, la JVM opera con dos tipos de datos: 

1. 
Los primitivos
1. 
Los valores de referencia.


La JVM espera que toda verificación de tipo se haga en tiempo de ejecución, siendo los tipos primitivos los que no necesitan de verificación o inspeccción ya que operan con un tipo específico de instrucciones (por ejemplo: iadd, ladd, fadd, y dadd para enteros, long, float, y double respectivamente).

La JVM tiene soporte para objetos que son instancia de una clase asignada dinámicamente o un array, esos valores son de tipo **reference** y su funcionamiento es similar al de los lenguajes C/C++.

Los tipos primitivos que existen en la JVM son: 

* Numéricos
* Booleanos 
* returnAdress

Siendo los tipos numéricos valores enteros o flotantes.

|Nombre|Tamaño|Variación|Valor por defecto|Tipo|
| -- | -- | -- | -- | -- |
|byte|8-bit|-2⁷  até 2⁷|0|entero|
|short|16-bits|-2¹⁵ até  2¹⁵|0|entero|
|integer|32-bits|-2³² até 2³¹|0|entero|
|long|64-bits|-2⁶³ até 2⁶³|0|entero|
|char|16-bits|UFT-8|'\u0000'|entero|
|float|32-bits||0|flotante|
|double|64-bits||0|flotante|
|boolean|entero||false|booleano|
|returnAddress|||nulo|puntero|


Los formatos de punto flotante son `float`, con precisión simple, y `double`, con precisión doble. Tanto los valores como las operaciones siguen el estándar IEEE para aritmética de punto flotante binário (ANSI/ IEEE. 754-1985, Nueva York). Este estándar incluye valores positivos y negativos, cero, positivo y negativo infinito, y no es número (cuya abreviatura es **Nan** y es utilizado para representar valores inválidos como división por cero). Por defecto, las JVM soportan esos formatos, más también pueden soportar versiones extendidas de `double` y `float`.

El **returnAdress** es utilizado apenas por la JVM, no posee representación en el lenguaje, tiene un funcionamiento similar a punteros y a diferencia de los tipos primitivos, no se pueden modificar en tiempo de ejecución.

En la JVM el tipo booleano posee un soporte bien limitado, no existen instrucciones para booleanos,  de hecho, ellos son compilados para usar los tipos de instrucciones de `int` y si es un array de booleano son tratados como `array` de `byte`. Los valores son tratados como `1` para verdadero y `0` para falso.

Hablando un poco sobre el tipo de referencia, existen tres tipos: 

1. 
classes
1. 
array
1. 
interfaces



El Valor de referência es iniciado como `null`, el nulo no es un tipo definido, mas se le puede hacer cast con cualquier tipo de referencia.
	
En resumen, existen basicamente dos tipos de datos:

* Primitivos y Referencia. 
 * Las referencias poseen subtipos: classe, interface y array.
 * Los primitivos poseen returnAdress, booleano, flotantes (float y double de simple y doble precisión respectivamente), enteros (short, byte, int, long, char).
