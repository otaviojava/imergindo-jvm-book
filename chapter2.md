## Funcionamento básico da JVM


Nesse capítulo falará um pouco do funcionamento básico da JVM além das variáveis. Falará um pouco do coração da linguagem Java, a sua JVM. A JVM é responsável pela independência entre as plataformas e roda basicamente dois tipos de processos: 

* O escrito em java que são gerados **bytecodes** 
* Os nativos que são realizados em linguagens como o C\C++ que são *linkadas* dinamicamente para uma plataforma específica.

Os métodos nativos são muito interessantes para obter informações do SO sendo utilizado além de usar recursos da máquina. E é em função disso que apesar de a linguagem ser **RunAnyWhere** a JVM não é, ou seja, para cada plataforma existe uma máquina virtual específica. Isso acontece, por exemplo, para usar recursos específicos de uma máquina, por exemplo, existem chamadas para cada diretório e arquivos.


![A JVM precisa ser compilada para uma plataforma específica.](imagens/chapter_2_1.png)




O único e principal motivo da JVM é rodar o aplicativo. Quando se inicia uma execução a JVM nasce e quando a aplicação termina ela morre. É criado uma JVM para cada aplicação, ou seja, se executar três vezes o mesmo código em uma mesma máquina serão iniciadas 3 JVMs. Para rodar uma aplicação basta que sua classe possua um método público e estático com o nome main e tenha como parâmetro um vetor de `String`.


Ao iniciar uma JVM existem alguns processos que rodam em paralelos e em backgrouns e executam diversas operações e processos para manter a JVM sempre disponível: 


* Os Timers que são responsáveis pelos eventos que acontecem periodicamente, por exemplo, interrupções, eles são usados para organizar os processos que acontecem continuamente. 
* Os processos do Garbage Collector é responsável por executar as atividades do coletor de lixo da JVM.
* Compiladores que são responsáveis por transformar bytecode em código nativo.
* Os ouvintes, que recebem sinais (informações) e tem como principal objetivo enviar essas informações para o processo correto dentro da JVM.
 

Falando um pouco mais sobre esses processos paralelos ou `Thread`, a JVM permite que múltiplos processos executem concorrentemente, essa rotina em Java está diretamente relacionada com uma `Thread` nativa. Tão logo um processo paralelo em Java nasça, os seus primeiros passos são:

* Alocação de memória
* Sincronização dos objetos
* Criação dos registradores específicos para a mesma e a alocação da `Thread` nativa. 
 
Quando essa rotina gera uma exceção a parte nativa envia essa informação para a JVM que a encerra. Quando a `Thread` termina todos os recursos específicos, tanto para em Java quanto a parte nativa, são entregues para JVM.

	Como na linguagem, a JVM opera em dois tipos de dados: Os primitivos e os valores de referência. A máquina espera que toda a verificação quanto ao tipo tenha sido feito no momento da execução, sendo que os tipos primitivos não precisão de tal verificação ou inspeção já que eles operam com um tipo específico de instrução (por exemplo: iadd, ladd, fadd, e dadd para inteiro, long, float e double respectivamente).

	A JVM tem suporte para objetos que são ou instância de uma classe alocada dinamicamente ou um array, esses valores são do tipo reference, o seu funcionamento é semelhante de linguagens como C/C++.

	Os tipos primitivos existentes na JVM são: numéricos, booleano e returnAdress, sendo que os tipos numéricos são os valores inteiros e flutuantes.
