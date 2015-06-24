#### Classes após compilação


Uma vez falando dos **bytecodes** é interessantes “puxar o gancho” e falar como fica uma classe após sua compilação. Como já foi dito após a compilação é gerado um **bytecode**, cujo arquivo possui a extensão .class, e cada arquivo representa apenas uma classe. Cada arquivo possui as seguintes características:

 
* Um número mágico em hexadecimal definindo que essa clase é um .class o valor é **0xCAFEBABE**

* O maior e menor número da versão do arquivo class que juntos definem a versão do arquivo, ou seja, JVM antes rodar precisa verificar se a versão V que ela pode executar estar entre: Menor Versão<V< Maior Versão.

* **access_flags**: Essa flag indica o tipo de encapsulamento da classe, métodos e de suas propriedades os flags podem ser:


* **ACC_PUBLIC**: flag método, atributos públicos
* **ACC_PRIVATE**: flag para privados
* **ACC_PROTECTED**: protected
* **ACC_STATIC**: estático
* **ACC_FINAL**: final
* **ACC_SYNCHRONIZED**: indica um método sincronizado
* **ACC_BRIDGE**: indica que o método foi gerado pelo compilador
* **ACC_VARARGS**: indica que é varags 
* **ACC_NATIVE**: nativo
* **ACC_ABSTRACT**: abstrato
* **ACC_STRICT**: indica que o método é strict
* **ACC_SYNTHETIC**: indica que o método não é “original”


. 
* **this_class**: o valor da corrente classe deve ter um índice válido na constant pool
 
* **super_class**: as informações da superclasse devem estar dentro e pode ocupar o índice zero ou não, se ocupar o índice zero essa classe é o java.lang.Object, a única classe que não possui pai, do contrário terá que ser um índice válido e ter informações que apontam para a classe pai. As informações da classe é definida pelo seu nome com o seu caminho, por exemplo, a nome da String seria java/lang/String.

* **constant pool**: O constant pool é uma estrutura de tabela que contém o nome das classes, interfaces, métodos, atributos e outras informações das classes. Para guardar essas informações existem dois registadores par cada informação importante: O vetor coma s informações da classe, método, ou atributos e o seu contador ou índice que funciona como limitador do vetor. Esse é o caso das interfaces que a classe implementa, atributos, métodos que possuem seus respectivos vetor e índices.

* As descrições dos atributos ou dos parâmetros em um método quanto ao seu tipo é definido a seguir:

  * B byte signed byte 
  * C char 
  * D double 
  * F float 
  * I int 
  * J long 
  * L Classname ; referência 
  * S short
  * Z boolean 
  * [ referência de um vetor 
  * [[ referência de uma matriz 


Assim, por exemplo: `double dobro(double d)` é igual  `(D)D` e `Double dobro(Double d)` é `(Ljava/lang/Double;)Ljava/lang/Double`.

Dentro da constant pool cada informação possui o seu primeiro byte que indica o seu tipo de informação:


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




**StackMapTable**: é composto de stackmapframe e tem o objetivo de verificações para o bytecode

Para auxiliar a depuração na linguagem Java existem algumas informações para depurar o código essas variáveis são: LocalVariableTable e LocalVariableTypeTable que define as informações das variáveis locais para o debug e LineNumberTable define a parte do bytecode e sua correspondente linha de código.
Para as anotações exitem: `RuntimeVisibleAnnotations`, `RuntimeInvisibleAnnotations`, `RuntimeVisibleParameterAnnotations`, `RuntimeInvisibleParameterAnnotations` que contém informações das anotações quanto a sua visibilidade em tempo de execução aos atributos e métodos ou não, existem essas mesmas informações para os parâmetros quanto as suas visibilidades. `AnnotationDefault` define as informações dentro das anotações.


O contador da consant pool possui 16 bits, ou seja, ele só pode conter 2¹⁶=65535 elementos, esse mesmo número vale para o número de métodos, atributos, interfaces implementadas, variáveis locais, pilha de operações (sendo que para esses dois últimos o longo e o double ocupam dois espaços), o nome do método ou atributo. O número de dimensões de uma matriz é 255 o mesmo número vale para a quantidade de parâmetros, caso não seja um método estático deve-se incluir a instância.
	
Com o objetivo de pôr em prática e visualizar esses **bytescodes**, será demonstrado um simples código e o seu respectivo bytecode.


```java 
public class PrimeiroTeste{ 

public Double somarInstancias(Double a, Double b) { 

	Double resultado = a + b; 
	return resultado; 
} 

public double somarDouble(double a, double b) { 
        return a + b; 
} 
public int somarInteiros(int a, int b) { 
        return a + b; 
} 

public short somarShort(short a, byte b) { 
        return (short) (a + b); 
} 

public static int somarStatic(int a, int b) { 
        return a + b; 
} 

}
```


Criado o arquivo PrimeiroTeste.java e inserido o código 1 nesse arquivo, os próximos passos serão entrar pelo terminal no caminho que se encontra o arquivo PrimeiroTeste.java, compilar e analisar o seu respectivo byte code com os seguintes comandos.

* `javac PrimeiroTeste.java`
* `javap -verbose PrimeiroTeste`

O resultado:

```bytecode

  minor version: 0 
  major version: 51 
  flags: ACC_PUBLIC, ACC_SUPER 
Constant pool: 
   #1 = Methodref          #5.#21         //  java/lang/Object."<init>":()V 
   #2 = Methodref          #22.#23        //  java/lang/Double.doubleValue:()D 
   #3 = Methodref          #22.#24        //  java/lang/Double.valueOf:(D)Ljava/lang/Double; 
   #4 = Class              #25            //  PrimeiroTeste 
   #5 = Class              #26            //  java/lang/Object 
   #6 = Utf8               <init> 
   #7 = Utf8               ()V 
   #8 = Utf8               Code 
   #9 = Utf8               LineNumberTable 
  #10 = Utf8               somarInstancias 
  #11 = Utf8               (Ljava/lang/Double;Ljava/lang/Double;)Ljava/lang/Double; 
  #12 = Utf8               somarDouble 
  #13 = Utf8               (DD)D 
  #14 = Utf8               somarInteiros 
  #15 = Utf8               (II)I 
  #16 = Utf8               somarShort 
  #17 = Utf8               (SB)S 
  #18 = Utf8               somarStatic 
  #19 = Utf8               SourceFile 
  #20 = Utf8               PrimeiroTeste.java 
  #21 = NameAndType        #6:#7          //  "<init>":()V 
  #22 = Class              #27            //  java/lang/Double 
  #23 = NameAndType        #28:#29        //  doubleValue:()D 
  #24 = NameAndType        #30:#31        //  valueOf:(D)Ljava/lang/Double; 
  #25 = Utf8               PrimeiroTeste 
  #26 = Utf8               java/lang/Object 
  #27 = Utf8               java/lang/Double 
  #28 = Utf8               doubleValue 
  #29 = Utf8               ()D 
  #30 = Utf8               valueOf 
  #31 = Utf8               (D)Ljava/lang/Double; 
  
 ```


Nesse primeiro resultado podemos visualizar a constant pool e a menor e a maior versão do class. O Constant Pool contém as informações da respectiva classe, já que toda classe possui essa informação, inclusive as InnerClasses, e eles são armazenadas em um vetor.



```bytecode

public PrimeiroTeste(); 
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
               0       5     0  this   LPrimeiroTeste; 

  public java.lang.Double somarInstancias(java.lang.Double, java.lang.Double); 
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
               0      15     0  this   LPrimeiroTeste; 
               0      15     1     a   Ljava/lang/Double; 
               0      15     2     b   Ljava/lang/Double; 
              13       2     3 resultado   Ljava/lang/Double; 

  public double somarDouble(double, double); 
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
               0       4     0  this   LPrimeiroTeste; 
               0       4     1     a   D 
               0       4     3     b   D 

  public int somarInteiros(int, int); 
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
               0       4     0  this   LPrimeiroTeste; 
               0       4     1     a   I 
               0       4     2     b   I 

  public short somarShort(short, byte); 
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
               0       5     0  this   LPrimeiroTeste; 
               0       5     1     a   S 
               0       5     2     b   B 

  public static int somarStatic(int, int); 
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


Ao vermos os métodos podemos perceber que todos os métodos possui o tamanho da pilha de operação e de variáveis além do tamanho das variáveis envolvidas em um determinado método. 

No primeiro que é o método construtor, esse método é construído automaticamente caso não seja feita pelo usuário, ele possui 1 tamanho de operação, já que se trata da criação de um objeto do tipo referência e esse ocupa um espaço no vetor de operação, 1 no tamanho de variável, já que ele é um método não estático e essas informações pertence a interface que a está chamando e o número de variáveis utilizadas é de um já que estamos nos referindo a instância criada. 
No segundo método, a soma de instâncias e retorna uma terceira instância, `(Ljava/lang/Double;Ljava/lang/Double;)Ljava/lang/Double`, ele possui o tamanho de três na pilha de variáveis, já que uma para as duas variáveis de referência e uma já que o método é da instância, quatro no tamanho de pilha de operações, já que no processo os Doubles serão transformados em double primitivo, assim cada um ocupará duas unidades no vetor. O campo `LineNumberTable` é para ajudar a debugar o código num determinado método, `LineNumberTable` 5: 0, diz que a linha de número cinco do código java equivale a instrução do começo, linha zero do **bytecode** e line 6: 13, a linha seis do código java começa na instrução do **bytecode** número 13. O campo `LocalVariableTable` também serve para debugar e define o nome do campo, tipo, linha que ele nasce e a que morre. Isso demonstra como é diferente o código Java e o **byteCode** gerado.


Nesse capítulo falamos um pouco sobre o **bytecode** e o seu macete para entender, olhando pelas inicias do comando, vale lembrar que durante a execução os boolianos, byte, shorts são transformados para inteiros, assim suas operações são realizadas como inteiros. Se demonstrou quão diferente é o código Java do bytecode gerado e em função disso se criou tabelas e variáveis, por exemplo, LocalVariable e LineNumberTable para auxiliar na hora de debugar, essas variáveis são utilizadas pelo modo debug das IDEs modernas.