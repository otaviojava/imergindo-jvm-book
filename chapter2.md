## Funcionamento básico da JVM


Nesse capítulo falará um pouco do funcionamento básico da JVM além das variáveis. Falará um pouco do coração da linguagem Java, a sua JVM. A JVM é responsável pela independência entre as plataformas e roda basicamente dois tipos de processos: 

* O escrito em java que são gerados **bytecodes** 
* Os nativos que são realizados em linguagens como o C\C++ que são *linkadas* dinamicamente para uma plataforma específica.

Os métodos nativos são muito interessantes para obter informações do SO sendo utilizado além de usar recursos da máquina e é em função disso que apesar de a linguagem ser RunAnyWhere a JVM não é, ou seja, para cada plataforma existe uma máquina virtual específica. Isso acontece, por exemplo, para usar recursos específicas de máquina, por exemplo, existem chamadas para cada diretório e arquivos.