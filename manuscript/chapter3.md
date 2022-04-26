## Registradores da JVM



Falado um pouco sobre os tipos de dados que são armazenados na JVM e o seu tamanho. É necessário também que se tenha ciência de onde são armazenadas tais informações. A JVM usa registradores para armazenar várias coisas sendo que para todo tipo de dado existe um local específico. Durante a execução de um programa existem registrados que são compartilhados entre toda a JVM e outros que tem a visibilidade da `Thread` corrente.

![Os registradores da JVM, Method Area e o Heap são compartilhados por toda a JVM e o PC Counter, Pilha Java e a Pilha Nativa cada Thread possui a sua.](chapter_3_1.png)

### Program Counter


O registrador **PC**, Program counter, é criado tão logo uma `Thread` é criada, ou seja, cada `Thread` possui o seu. Ele pode armazenar dois tipos de dados: 

1. 
Ponteiros nativos
1. 
returnAdress

Esses dados possuem informações quanto a instrução que está sendo executada pela `Thread`. Se o método executado for nativo o **PC** será um ponteiro e não tem o seu valor definido, do contrário, ele terá o endereço de instrução, o **returnAdress**.

![Funcionamento do PC](chapter_3_2.png)

### Java Stack (Java virtual machine stack)


Assim como o **PC**, ele é um registrador privado para cada `Thread`, esse registrador armazena **frames** (que será visto a frente). Seu funcionamento é similar a linguagens clássicas como o `C`, ele serve para armazenar variáveis locais e resultados parciais, invocações e resultados dos métodos. Ele não modifica as variáveis diretamente somente inserindo e removendo frames do registrador. Tão logo a corrente `Thread` chama um método um novo frame é inserindo contado informações como parâmetros, variáveis locais, etc. Assim quando o método termina de uma maneira normal, quando acaba o método, ou por interrupção, quando ocorre uma exceção dentro do método, esse frame é descartado. O Java Stack pode ter tamanho fixo ou determinado dinamicamente.

#### Stack Frame


O **frame** é a unidade do **Java Stack** ele é criado tão logo se cria um método e é destruído quando o método é encerrado (normalmente ou ininterrompido por uma exceção). Cada **frame** possui uma lista das variáveis locais, pilha de operações além da referência da classe corrente e do método corrente. Esse frame é dividido em três partes:

1. 
Stack variables
1. 
Stack Operand
1. 
Frame Data


![Stack Frame](chapter_3_3.png)

##### Stack variables



Cada **frame** contém um vetor para armazenar variáveis locais e os parâmetros e esse tamanho é definido em tempo de execução. Nesse vetor as variáveis `double` e `long` ocupam dois elementos do vetor e são armazenados consequentemente. Variáveis do tipo `int` e `returnAdress` ocupam um elemento desse vetor (`byte`, `short` e `char` são convertidos para `int`). Caso o método seja da instância, não seja estático, o primeiro elemento desse vetor será ocupado pela instância que está executando esse método e em seguida os parâmetros, na ordem que foram passados. Caso o método seja da classe, o método seja estático, Não haverá referência da instância que chama o método, assim o primeiro elemento será os parâmetros.


![As pilhas de variáveis são compostas por índices de 32 bits, assim as variáveis do tipo double e long ocupam dois espaços contínuos e as outras variáveis apenas um.](chapter_3_4.png)

##### Stack Operand


Como o nome indica, esse registrador serve para armazenar as instruções que ocorrem dentro do método, como o registrador de variáveis locais os valores são armazenados em um vetor mas seus valores recuperados pela remoção do último elemento do vetor em vez de ser pelo índice. Ele é baseado na estrutura de dados de Pilha (Primeiro a entrar último a sair). O tamanho das variáveis acontecem de maneira semelhante as variáveis locais.

![Pilha de operação, semelhante ao seu “irmão”, sua unidade possui o tamanho de 32 bits, seu passo-a-passo segue o mesmo de uma pilha convencional, o ultimo que entrar será o primeiro a sair. Nesse exemplo será utilizado a soma de dois inteiros ( 10 e 20).](chapter_3_5.png)
Pilha de operação, semelhante ao seu “irmão”, sua unidade possui o tamanho de 32 bits, seu passo-a-passo segue o mesmo de uma pilha convencional, o ultimo que entrar será o primeiro a sair. Nesse exemplo será utilizado a soma de dois inteiros (`10` e `20`).


![Como a pilha de operação é composta por unidade de 32 bits, quando for double ou long ele ocupará as duas unidades seguidas, nesse exemplo são somados dois doubles ( 10.10 e 20.20)](chapter_3_6.png)
Como a pilha de operação é composta por unidade de 32 bits, quando for `double` ou `long` ele ocupará as duas unidades seguidas, nesse exemplo são somados dois doubles (`10.10` e `20.20`)

##### Frame Data


Esse pequeno registrador possui o link da constant pool da classe que o possui o corrente método que está sendo executado.

### Native Method Stacks


Possui finalidade de armazenar variáveis e valores nativos (métodos escritos em outras linguagens), é criado tão logo uma `Thread` é iniciada e todas as `Threads` possuem o seu registrador.


![Pilha nativa](chapter_3_7.png)

### Method Area


Esse registrador tem a finalidade de armazenar logicamente o stream da classe, essa área é compartilhada entre todas as`Threads`. Logicamente faz parte do Heap espace. Por ser parte do Heap ele possui o recolhimento de memória automático, Garbage Collector. As classes contém as seguintes informações:



* O **qualified** da classe (O qualifed é o endereço da sua classe que é definido pelo pacote mais `.` e o nome da Classe, por exemplo, `java.lang.Object` ou `java.util.Date`).
* O **qualified** da classe pai (menos para as Interfaces e o `java.lang.Object`).
* Informação se é uma classe ou interface.
* Os modificadores.
* A lista com os **qualifieds** das interfaces.


Para cada classe carregada no Java é carregada um **constant pool**, que contém as seguintes informações:


* O **constant pool** do tipo (Para cada classe Carregada é criada um pool de constant, ele contém o link simbólico para os métodos e para os atributos além das constantes existentes no tipo).
* informações dos atributos (o nome do atributo, o tipo e o seu modificador).
* informação dos métodos (o nome do método, o seu retorno, o número e tipo dos parâmetros em ordem e o tipo e o seu modificador).
* Referência para o `ClassLoader` (classe responsável para carregar a classe)
* Variáveis da classe (variáveis compartilhadas entre todas as classes isso inclui as constantes).
* Referência da classe (uma instância da `java.lang.Class` para toda classe carregada).

### Vendo os conceitos na prática

#### Heap Space


Tão logo uma instância é criada, as informações do seu objeto ficam armazenados aqui, esse espaço de memória também é compartilhado entre as `Threads`. O **heap** tem seu mecanismo de reclamar memória em tempo de execução além de mover objetos evitando a fragmentação do espaço.


![Representação de uma variável do tipo de referência dentro do Heap](chapter_3_8.png)


Representação de uma variável do tipo de referência dentro do **Heap** é diferente dos tipos primitivos, ele tem o seu mecanismo muito semelhante aos ponteiros do `C/C++` já que ele não possui a informação, apenas aponta para o local que o possui. O objeto de referência é constituído de dois ponteiros menores:

* Um apontará para o pool de objetos, local aonde estão as informações.
* O segundo apontará para o seu constant pool (que possui as informações da classe quanto aos atributos, métodos, encapsulamentos, etc.) que fica localizado no **method Area**.



A representação dos vetores se comporta de forma semelhante as variáveis de referência, mas eles ganham dois campos a mais: 

1. 
O **tamanho**, que define o tamanho do vetor
1. 
Uma **lista de referência** que apontam para os objetos que estão dentro desse vetor. 


![Representação de um vetor dentro do Heap](chapter_3_9.png)

### Cache de código


Esse registrador é usado para compilação e armazenamento dos métodos que foram compilados para o modo nativo pelo **JIT**, esse registrador é compartilhado por todas as `Threads`.

#### Just In Time (JIT) Compilation


O **bytecode** Java interpretado não são tão rápido quanto os códigos nativos, para cobrir esse problema de performance, a JVM verifica métodos críticos (regiões que executam constantemente, por exemplo) e compila para o código nativo. Esse código nativo será armazenado dentro do **cache de código** em uma região fora da heap. A JVM tenta escolher as regiões mais críticas para que mesmo com o gasto memória e poder computacional de compilar o código para nativo, seja uma decisão vantajosa.

### Recapitulando


Com isso foi falado sobre os registradores que contém na JVM, vale lembrar que algumas são exclusivas por `Threads` ou outra não. A **pilha nativa** são importantes para obter recursos da máquina, no entanto, os seus valores são indefinidos, já as **pilhas Java** são criados tão logo um método é iniciado ele é subdividido em **frames**, ambas as pilhas são particular por `Thread`. O registrador **PC** não possui informações, apenas aponta para a instrução que está sendo executada e possui uma por `Thread`. O **Heap** e o **method Area** são compartilhadas entre a JVM, todas as `Threads`, e tem a responsabilidade de armazenar a instância dos objetos e o streams e informações da classe respectivamente.

