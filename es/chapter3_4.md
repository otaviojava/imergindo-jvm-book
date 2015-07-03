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