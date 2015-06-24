### Method Area


Esse registrador tem a finalidade de armazenar logicamente o stream da classe, essa área é compartilhada entre todas as`Threads`. Logicamente faz parte do Heap espace. Por ser parte do Heap ele possui o recolhimento de memória automático, Garbage Collector. As classes contém as seguintes informações:



* O **qualified** da classe (O qualifed é o endereço da sua classe que é definido pelo pacote mais “.” e o nome da Classe, por exemplo, `java.lang.Object` ou `java.util.Date`)
* O **qualified** da classe pai (menos para as Interfaces e o `java.lang.Object`) 
* Informação se é uma classe ou interface 
* Os modificadores
* A lista com os **qualifieds** das interfaces