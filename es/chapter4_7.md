#### Clases despues de la compilación


Una vez hablando de los **bytecodes** es interesante “tirar el gancho” y hablar como queda una clase despues de su compilación. Como ya fue dicho, despues de la compilación es generado un **bytecode**, cuyo archivo tiene una extensión .class, y cada archivo representa solo una clase. Cada archivo tiene las siguientes características:

 
* Un número mágico en hexadecimal definiendo que esa clase es un .class el valor es **0xCAFEBABE**

* El mayor y menor número de la versión del archivo class que juntos definen la versión del archivo, o sea, JVM antes de correr se necesita verificar si la versión V que esta puede ejecutar entre: Menor Versión< V < Maior Versión.

* **access_flags**: Este flag indica el tipo de encapsulamiento de la clase, metodos y de sus propiedades los flags pueden ser:


* **ACC_PUBLIC**: flag método, atributos públicos
* **ACC_PRIVATE**: flag para privados
* **ACC_PROTECTED**: protected
* **ACC_STATIC**: estático
* **ACC_FINAL**: final
* **ACC_SYNCHRONIZED**: indica un método sincronizado
* **ACC_BRIDGE**: indica que el metodo fue generado por el compilador
* **ACC_VARARGS**: indica que es varags 
* **ACC_NATIVE**: nativo
* **ACC_ABSTRACT**: abstracto
* **ACC_STRICT**: indica que el método es strict
* **ACC_SYNTHETIC**: indica que el método no es “original”


. 
* **this_class**: el valor de la clase actual debe tener un indice válido en la constant pool
 
* **super_class**: las informaciones de la superclase deben estar dentro y puede ocupar el índice cero o no, si ocupa el indice cero esa clase es java.lang.Object, la única clase que no tiene padre, de otra manera tendrá que ser un indice válido y tener informaciones que apuntan para la clase padre. Las informaciones de la clase es definida por su nombre con su ruta, por ejemplo, el nombre de String seria java/lang/String.

* **constant pool**: El constant pool es una estructura de tabla que contiene el nombre de las clases, interfaces, metodos, atributos y otras informaciones de las clases. Para guardar esas informaciones existen dos registadores para cada información importante: El vector con las informaciones de la clase, metodo, o atributos y su contador o índice que funciona como limitador del vector. Este es el caso de las interfaces que la clase implementa, atributos, metodos que tienen sus respectivos vector e índices.

* Las descripciones de los atributos o de los parametros en un método como su tipo es definido a seguir:

  * B byte signed byte 
  * C char 
  * D double 
  * F float 
  * I int 
  * J long 
  * L Classname ; referencia 
  * S short
  * Z boolean 
  * [ referencia de un vector 
  * [[ referencia de una matriz 


Asi, por ejemplo: `double dobro(double d)` es igual  `(D)D` y `Double dobro(Double d)` es `(Ljava/lang/Double;)Ljava/lang/Double`.

Dentro del constant pool cada información tiene su primero byte que indica su tipo de información:


  * CONSTANT_Class 7 
  * CONSTANT_Fieldref 9 
  * CONSTANT_Methodref 10 
  * CONSTANT_InterfaceMethodref 11 
  * CONSTANT_String 8 
  * CONSTANT_Integer 3 
  * CONSTANT_Float 4 
  * CONSTANT_Long 5 
  * CONSTANT_Double 6 
  * CONSTANT_NameAndType 12 
  * CONSTANT_Utf8 1 
  * CONSTANT_MethodHandle 15 
  * CONSTANT_MethodType 16 
  * CONSTANT_InvokeDynamic 18 




**StackMapTable**: es compuesto de stackmapframe y tiene el objetivo de verificaciones para el bytecode

Para auxiliar la depuración en lenguaje Java existen algunas informaciones para depurar el código esas variables son: LocalVariableTable y LocalVariableTypeTable que define las informaciones das variables locales para el debug y LineNumberTable define la parte de bytecode y su correspondiente linea de código.
Para las anotaciones existen: `RuntimeVisibleAnnotations`, `RuntimeInvisibleAnnotations`, `RuntimeVisibleParameterAnnotations`, `RuntimeInvisibleParameterAnnotations` que contienen informaciones de las anotaciones como su visibilidad en tiempo de ejecución a los atributos y metodos o no, existen esas mismas informaciones para los parametros como sus visibilidades. `AnnotationDefault` define las informaciones dentro de las anotaciones.


El contador de constant pool posee 16 bits, o sea, este solo puede contener 2¹⁶=65535 elementos, ese mismo número vale para el número de metodos, atributos, interfaces implementadas, variables locales, pila de operaciones (en que lugar para esos dos ultimos es largo y el double ocupan dos espacios), el nombre del método o atributo. El número de dimensiones de una matriz es 255 el mismo número vale para la cantidad de parametros, en caso no sea un método estático se debe incluir la instancia.
	
Con el objetivo de poner en practica y visualizar esos **bytescodes**, será demostrado un simple código y su respectivo bytecode.


```java 
public class PrimerTest{ 

public Double sumarIntancias(Double a, Double b) { 

	Double resultado = a + b; 
	return resultado; 
} 

public double sumarDouble(double a, double b) { 
        return a + b; 
} 
public int sumarEnteros(int a, int b) { 
        return a + b; 
} 

public short sumarShort(short a, byte b) { 
        return (short) (a + b); 
} 

public static int sumarStatic(int a, int b) { 
        return a + b; 
} 

}
```


Creado el archivo PrimerTest.java e insertado el código 1 en ese archivo, los próximos pasos serán entrar por el terminal en la ruta que se encontra el archivo PrimerTest.java, compilar y analizar su respectivo byte code con los siguientes comandos.

* `javac PrimerTest.java`
* `javap -verbose PrimerTest`

El resultado:

```bytecode

  minor version: 0 
  major version: 51 
  flags: ACC_PUBLIC, ACC_SUPER 
Constant pool: 
   #1 = Methodref          #5.#21         //  java/lang/Object."<init>":()V 
   #2 = Methodref          #22.#23        //  java/lang/Double.doubleValue:()D 
   #3 = Methodref          #22.#24        //  java/lang/Double.valueOf:(D)Ljava/lang/Double; 
   #4 = Class              #25            //  PrimerTest 
   #5 = Class              #26            //  java/lang/Object 
   #6 = Utf8               <init> 
   #7 = Utf8               ()V 
   #8 = Utf8               Code 
   #9 = Utf8               LineNumberTable 
  #10 = Utf8               sumarIntancias 
  #11 = Utf8               (Ljava/lang/Double;Ljava/lang/Double;)Ljava/lang/Double; 
  #12 = Utf8               sumarDouble 
  #13 = Utf8               (DD)D 
  #14 = Utf8               sumarEnteros 
  #15 = Utf8               (II)I 
  #16 = Utf8               sumarShort 
  #17 = Utf8               (SB)S 
  #18 = Utf8               sumarStatic 
  #19 = Utf8               SourceFile 
  #20 = Utf8               PrimerTest.java 
  #21 = NameAndType        #6:#7          //  "<init>":()V 
  #22 = Class              #27            //  java/lang/Double 
  #23 = NameAndType        #28:#29        //  doubleValue:()D 
  #24 = NameAndType        #30:#31        //  valueOf:(D)Ljava/lang/Double; 
  #25 = Utf8               PrimerTest 
  #26 = Utf8               java/lang/Object 
  #27 = Utf8               java/lang/Double 
  #28 = Utf8               doubleValue 
  #29 = Utf8               ()D 
  #30 = Utf8               valueOf 
  #31 = Utf8               (D)Ljava/lang/Double; 
  
 ```


En ese primer resultado podemos visualizar el constant pool y la menor y la mayor versión del class. El Constant Pool contiene las informaciones de la respectiva clase, ya que toda clase tiene esa información, inclusive los InnerClass, y estos son almacenados en un vector.



```bytecode

public PrimerTest(); 
    flags: ACC_PUBLIC 
    Code: 
      stack=1, locals=1, args_size=1 
         0: aload_0       
         1: invokespecial #1                  // Method java/lang/Object."<init>":()V 
         4: return        
      LineNumberTable: 
        line 1: 0 
      LocalVariableTable: 
        Start  Length  Slot  Name   Signature 
               0       5     0  this   LPrimerTest; 

  public java.lang.Double sumarIntancias(java.lang.Double, java.lang.Double); 
    flags: ACC_PUBLIC 
    Code: 
      stack=4, locals=4, args_size=3 
         0: aload_1       
         1: invokevirtual #2                  // Method java/lang/Double.doubleValue:()D 
         4: aload_2       
         5: invokevirtual #2                  // Method java/lang/Double.doubleValue:()D 
         8: dadd          
         9: invokestatic  #3                  // Method java/lang/Double.valueOf:(D)Ljava/lang/Double; 
        12: astore_3      
        13: aload_3       
        14: areturn       
      LineNumberTable: 
        line 5: 0 
        line 6: 13 
      LocalVariableTable: 
        Start  Length  Slot  Name   Signature 
               0      15     0  this   LPrimerTest; 
               0      15     1     a   Ljava/lang/Double; 
               0      15     2     b   Ljava/lang/Double; 
              13       2     3 resultado   Ljava/lang/Double; 

  public double sumarDouble(double, double); 
    flags: ACC_PUBLIC 
    Code: 
      stack=4, locals=5, args_size=3 
         0: dload_1       
         1: dload_3       
         2: dadd          
         3: dreturn       
      LineNumberTable: 
        line 10: 0 
      LocalVariableTable: 
        Start  Length  Slot  Name   Signature 
               0       4     0  this   LPrimerTest; 
               0       4     1     a   D 
               0       4     3     b   D 

  public int sumarEnteros(int, int); 
    flags: ACC_PUBLIC 
    Code: 
      stack=2, locals=3, args_size=3 
         0: iload_1       
         1: iload_2       
         2: iadd          
         3: ireturn       
      LineNumberTable: 
        line 13: 0 
      LocalVariableTable: 
        Start  Length  Slot  Name   Signature 
               0       4     0  this   LPrimerTest; 
               0       4     1     a   I 
               0       4     2     b   I 

  public short sumarShort(short, byte); 
    flags: ACC_PUBLIC 
    Code: 
      stack=2, locals=3, args_size=3 
         0: iload_1       
         1: iload_2       
         2: iadd          
         3: i2s           
         4: ireturn       
      LineNumberTable: 
        line 17: 0 
      LocalVariableTable: 
        Start  Length  Slot  Name   Signature 
               0       5     0  this   LPrimerTest; 
               0       5     1     a   S 
               0       5     2     b   B 

  public static int sumarStatic(int, int); 
    flags: ACC_PUBLIC, ACC_STATIC 
    Code: 
      stack=2, locals=2, args_size=2 
         0: iload_0       
         1: iload_1       
         2: iadd          
         3: ireturn       
      LineNumberTable: 
        line 21: 0 
      LocalVariableTable: 
        Start  Length  Slot  Name   Signature 
               0       4     0     a   I 
               0       4     1     b   I 
               
```


Cuando vemos los metodos podemos percibir que todos los metodos tienen el tamaño de la pila de operación y de variables ademas del tamaño de las variables implicadas en un determinado metodo. 

En el primero que es el método constructor, ese metodo es construido automaticamente caso no sea hecho por el usuario, este tiene 1 tamaño de operación, ya que se trata de la creación de un objeto del tipo referencia y este ocupa un espacio en el vector de operación, 1 en el tamaño de variable, ya que este es un método no estático y esas informaciones pertenece a la interface que la está llamando y el número de variables utilizadas es de uno ya que nos estamos refiriendo a la instancia creada. 
En el segundo método, la suma de las instancias y retorna una tercera instancia, `(Ljava/lang/Double;Ljava/lang/Double;)Ljava/lang/Double`, este tiene el tamaño de tres en la pila de variables, una para las dos variables de referencia y una para método y de las instancias, cuatro en el tamaño de pila de operaciones, ya que en el proceso los Doubles serán transformados en double primitivo, asi cada uno ocupará dos unidades en el vector. El campo `LineNumberTable` es para ayudar a debuggear el código en un determinado método, `LineNumberTable` 5: 0, dice que la linea de número cinco del código java equivale a la instrucción del comienzo, linea cero del **bytecode** y linea 6: 13, la linea seis del código java comienza en la instrucción del **bytecode** número 13. El campo `LocalVariableTable` tambien sirve para debuggear y define el nombre del campo, tipo, linea en la que nace y que muere. Eso demuestra como es diferente el código Java y el **byteCode** generado.


En este capítulo hablamos un poco sobre **bytecode** y el truco para entenderlo, mirando por los inicios en comando, cabe recordar que durante la ejecución los booleanos, byte, shorts son transformados para enteros. Se demostró cuan diferente es el código Java del bytecode generado y en función de eso se creó tablas y variables, por ejemplo, LocalVariable y LineNumberTable para auxiliar en la hora de debuggear, esas variables son utilizadas por el modo debug de las IDEs modernas.