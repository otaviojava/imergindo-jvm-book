## Se queres prever o futuro, estuda o passado


**JVM**, java virtual machine ou máquina virtual java, tem sua história inciada em 1992. O Green Project na época a linguagem era denominada de oak. Com o passar do tempo a máquina virtual foi evoluindo e ficando cada vez mais complexa. A linguagem Java possui uma sintaxe similar ao C++, ele pode ser usado de várias maneiras e é orientado a objetos e se tornou popular em conjunto com a web. A JVM funciona como o alicerce da plataforma Java ficando responsável por tratar todas as plataformas e Sistemas Operacionais de modo independente para a linguagem. A JVM não conhece absolutamente nada da linguagem Java, apenas o seu **bytecode**, que vem no formato `.class`,  que são as instruções da JVM (daí a possibilidade de portar outras linguagens para a JVM já que ele não roda Java e sim o bytecode). Esse `class` é o código compilado em java e representa uma classe ou interface em java. 


Do seu início até a presente data o Java teve diversas versões. Essas modificações são gerenciadas pelo **JCP**, Java Community Process (o comitê que rege as mudanças da plataforma java com cerca de 30 empresas), a partir de JSRs, Java Specification Requests, especificações que fornecem tais modificações e melhorias. A documentação da linguagem fica no JSL, Java Language Specification, documentação da JVM fica Java Virtual Machine Specification.





1.1.8 - Java SE 6 (11 de dezembro de 2006) 

	Com o codinome Mustangue, nessa versão a Sun substitui o nome “J2SE” e removeu o “.0” do número da versão e foi desenvolvida na JSR 270.

Suporte a linguagem de script JSR 223): Uma API Genérica para integração com linguagens scripts e foi embutido a integração com o Mozilla JavaScript Rhino.
Suporte a Web Service através do JAX-WS (JSR 224) 
JDBC 4.0  (JSR 221). 
Java Compiler API (JSR 199): uma API para permitir chamar compilação programando
 JAXB  2.0: 
Melhorias no Annotations (JSR 269)
Melhorias no GUI, como SwingWorker, tabela filtrada e ordenada
Melhorias na JVM incluindo: sincronização e otimizações do compilador, melhorias no algorismo do coletor de lixo.


1.1.9 - Java SE 7 (28 de julho de 2011)

	Com o codinome Dolphin possui o maior número de atualização no Java. Foi lançado no dia 7 de Julho e foi disponibilizado no dia 28 de julho do mesmo ano.

Da Vinci Machine: Suporte para linguagens dinâmicas
Projeto Coin
Strings in switch
Automatic resource management in try-statement
Diamond
Simplified varargs 
Binary integer literals
 numeric literals
mult-try
Novo pacote utilitário de concorrência: JSR 166
NIO2: novos biblioteca para IO


	Nesse primeiro capítulo houve uma pequena introdução sobre o interior da JVM e da sua importância para a plataforma além do aspecto histórico das versões do Java e de sua evolução tanto como plataforma, linguagem e máquina virtual. 