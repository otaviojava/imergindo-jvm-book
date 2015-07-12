## Funcionamento basico de la JVM


Este capítulo hablará un poco sobre el funcionamiento basico de la JVM, que es el corazón del lenguaje java. Esta es la responsable por la independencia entre las plataformas y corren basicamente dos tipos de procesos: 

* Los escrito en java que son generados **bytecodes** 
* Los nativos que son escritos en lenguajes como C\C++ y *enlazadas* dinamicamente para uma plataforma específica.

Los métodos nativos son muy interesantes para obtener información del SO donde la JVM esta en ejecución, ademas de utilizar recursos de este. Y es en función de eso que a pesar de un lenguaje ser **RunAnyWhere** la JVM no es, es decir, para cada plataforma existe una máquina virtual específica. Esto sucede, por ejemplo, para usar recursos específicos de la plataforma donde, por ejemplo, existen llamadas distintas para trabajar con directorio y archivos.


![La JVM necesita ser compilada para una plataforma específica.](imagens/chapter_2_1.png)




El único y principal motivo de la JVM es correr el aplicativo. Cuando se inicia una ejecución la JVM nace y cuando la aplicación termina esta muere. Es creado una JVM para cada aplicación, o sea, si se ejecuta tres veces el mismo codigo en una misma maquina serán iniciadas 3 JVMs. Para correr una aplicación es suficiente que su clase tenga un metodo publico y estatico com el nombre main y tenga como parametro y vector de `String`.


Al iniciar una JVM existen algunos procesos que corren en paralelo y en segundo plano y ejecutan diversas operaciones y procesos para mantener la JVM siempre disponible: 


* Los Timers que son responsables por los eventos que suceden periodicamente, por ejemplo, interrupciones, estos son usados para organizar los procesos que ocurren continuamente. 
* Los procesos de Garbage Collector que es responsable por ejecutar las actividades del colector de basura de la JVM.
* Compiladores que son responsables por transformar bytecode en código nativo.
* Los listeners, que reciben señales (informaciones) y tiene como principal objetivo enviar esas informaciones para el proceso correcto dentro de la JVM.
 

Hablando un poco mas sobre esos procesos paralelos o `Thread`, la JVM permite que múltiples procesos se ejecuten concurrentemente, esta rutina en Java está directamente relacionada con un `Thread` nativo. Tan pronto un proceso paralelo en Java nace, sus primeros pasos son:

* Asignación de memoria
* Sincronización de los objetos
* Creación de los registradores específicos para estos y la asignación del `Thread` nativo.
 
Cuando esta rutina genera una excepción la parte nativa envia esa información para la JVM que la cierra. Cuando un `Thread` termina todos los recursos específicos, tanto para Java como para la parte nativa, son entregados para la JVM.

Como en el lenguaje, la JVM opera en dos tipos de datos: 

1. 
Los primitivos
1. 
Los valores de referencia. 


La JVM espera que toda la verificación como tipo haya sido realizado en tiempo de ejecución, siendo que los tipos primitivos no necesitan de tal verificación o inspección ya que ellos operan con un tipo especifico de instrucción (por ejemplo: iadd, ladd, fadd, y dadd para entero, long, float y double respectivamente).

La JVM tiene soporte para objetos que son instancia de una clase asignada dinamicamente o un array, esos valores son de tipo **reference** y su funcionamiento es semejante a los lenguajes como  C/C++.

Los tipos primitivos existentes en JVM son: 

* Numéricos
* Booleano 
* returnAdress

Siendo que los tipos numéricos son los valores enteros y flotantes.

|Nombre|Tamaño|variación|Valor default|Tipo|
| -- | -- | -- | -- | -- |
|byte|8-bit|-2⁷  hasta 2⁷|0|entero|
|short|16-bits|-2¹⁵ hasta  2¹⁵|0|entero|
|integer|32-bits|-2³² hasta 2³¹|0|entero|
|long|64-bits|-2⁶³ hasta 2⁶³|0|entero|
|char|16-bits|UFT-8|'\u0000'|entero|
|float|32-bits||0|flotante|
|double|64-bits||0|flotante|
|boolean|entero||false|booleano|
|returnAddress|||nulo|puntero|

Los formatos de punto flotante son `float`, con precisión simple, y `double`, con doble precisión. Tanto los valores como las operaciones siguen lo especificado en el standard IEEE para aritmética de punto flotante binario (ANSI/ IEEE. 754-1985, New York). Este standard no incluye solo valores positivos y negativos, mas cero, positivo y negativo infinito y no un número (abreviado como **Nan** es utilizado para representar valores inválidos como división por cero). Por standard, las JVM soportan ese formato, pero tambien pueden soportar versiones extendidas como `double` y `float`.

El **returnAdress** es usado solo por la JVM, no tiene representación en el lenguaje, tiene su funcionamento similar a los punteros y diferente de los tipos primitivos no podrán ser modificados en tiempo de ejecución.

En la JVM el tipo booleano tiene un soporte bien limitado, no existen instrucciones para booleano, la verdad ellos son compilados para usar los tipos de instrucciones de `int` y de array de booleano son manipulados como `array` de `byte`. Los valores son representados con `1` para verdadero y `0` para falso.

Hablando un poco sobre tipo de referencia, existen tres tipos: 

1. 
classes
1. 
array
1. 
interfaces


El valor de referencia es iniciado como `null`, nulo no es un tipo definido, pero puede ser hecho cast para cualquier tipo de referencia.
	
Resumiendo, existen basicamente dois tipos de datos:

* Primitivos y referencia.
 * Las referencias tienen tres subtipos: clase, interface y array.
 * Los primitivos tienen returnAdress, booleano, flotantes (float y double de simple y doble precisión respectivamente), enteros (short, byte, int, long, char).