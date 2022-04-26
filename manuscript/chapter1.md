## Se queres prever o futuro, estuda o passado


**JVM**, java virtual machine ou máquina virtual java, tem sua história inciada em 1992. O Green Project na época a linguagem era denominada de oak. Com o passar do tempo a máquina virtual foi evoluindo e ficando cada vez mais complexa. A linguagem Java possui uma sintaxe similar ao C++, é orientado a objetos e se tornou popular em conjunto com a web. A JVM funciona como o alicerce da plataforma Java ficando responsável por tratar todas as plataformas e Sistemas Operacionais de modo independente para a linguagem. A JVM não conhece absolutamente nada da linguagem Java, apenas o seu **bytecode**, que vem no formato `.class`,  que são as instruções da JVM (daí a possibilidade de portar outras linguagens para a JVM, já que ele não roda Java e sim o bytecode). Esse `class` é o código compilado e representa uma classe ou interface em java. 


Do seu início até a presente data o Java teve diversas versões. Essas modificações são gerenciadas pelo **JCP** ou Java Community Process (o comitê que rege as mudanças da plataforma java com cerca de 30 empresas), a partir de JSRs (Java Specification Requests), especificações que fornecem tais modificações e melhorias. A documentação da linguagem fica no JSL (Java Language Specification) e a documentação da JVM fica no Java Virtual Machine Specification.

### Histórico da JVM


Antes de se falar dos aspectos do Java, como linguagem, plataforma e máquina virtual é interessante conhecer um pouco sobre a evolução que o Java vem sofrendo. O projeto nasceu em 1995 e a partir desta data veio sofrendo constante evolução com ajuda de empresas e da comunidade.


#### JDK Alpha e Beta (1995) 

Nas versões alfas e betas se tiveram uma máquina instável.
1.1.2 - JDK 1.0 (23 de janeiro de 1996) 

Com o código nome Oak, que também foi o primeiro nome da linguagem. Na versão 1.0.2 foi lançado a primeira versão estável.


#### JDK 1.1 (19 de fevereiro de 1997)


* Grandes melhorias e refatorações nos modelos de evento do AWT
* Inner class adicionado a linguagem
* JavaBeans 
* JDBC 
* RMI 
* Reflection que suportava apenas introspecção, nenhuma modificação em tempo real era possível.

#### J2SE 1.2 (8 de dezembro de 1998)

	
Com o codinome **Plaground**. Essa e as outras versões foram denominadas de Java 2, J2SE Java 2 Platform, Standard Edition, Houve modificações significantes nessa versão triplicando o código para 1520 classes em 59 pacotes incluindo:

* A palavra-chave strictfp 
* A api do Swing foram integrados ao Core
* Adicionando o JIT compilador
* Java Plug-in
* Java IDL, uma implementação CORBA IDL para interoperabilidade
* Collections framework 

#### J2SE 1.3 (8 de maio de 2000)


Com o codinome **Kestrel**, as modificações mais importantes foram:


* HotSpot JVM incluído (a JVM HotSpot foi lançado em abril de 1999 para os 1,2 J2SE JVM).
* RMI foi modificado para suportar a compatibilidade opcional com CORBA
* JavaSound
* Java Naming and Directory Interface (JNDI) incluído em bibliotecas centrais
* Java Platform Debugger Architecture (ACDP)
* Sintéticos classes de proxy

#### J2SE 5.0 (30 de setembro de 2004)


Com o codinome **Tiger**, foi desenvolvida na **JSR 176**, teve seu final de vida em 8 de abril de 2008 e o encerramento do suporte dia 3 de novembro de 2009. O **Tiger** adicionou significantes melhorias para a linguagem:

* Generics:  (JSR14).
* Annotations: (JSR 175)
* Autoboxing/unboxing: Conversão automática entre os tipos primitivos e as classes encapsuladas (JSR 201).
* Enumerations: (JSR 201.) 
* Varargs: 
* for each loop
* Correções para o Java Memory Model(Que define como Threads interagem através da memória).
* Static imports 
* Geração automática do stub para objetos RMI
* Novo look and feel para o Swing chamado synth
* Um pacote utilitário de concorrência (java.util.concurrent)
* A classe Scanner para analisar dados de input streams e buffers


#### Java SE 6 (11 de dezembro de 2006)


Com o codinome **Mustangue**, nessa versão a Sun substitui o nome “J2SE” e removeu o “.0” do número da versão. Essa versão foi desenvolvida na JSR 270.

* Suporte a linguagem de script (JSR 223): Uma API Genérica para integração com linguagens scripts e foi embutido a integração com o Mozilla JavaScript Rhino.
* Suporte a Web Service através do JAX-WS (JSR 224) 
* JDBC 4.0  (JSR 221). 
* Java Compiler API (JSR 199): uma API para permitir chamar compilação programando
* JAXB  2.0
* Melhorias no Annotations (JSR 269)
* Melhorias no GUI, como SwingWorker, tabela filtrada e ordenada
* Melhorias na JVM incluindo: sincronização e otimizações do compilador,
* Melhorias no algorismo do coletor de lixo.


#### Java SE 7 (28 de julho de 2011)

	
Com o codinome **Dolphin** possui o maior número de atualização no Java. Foi lançado no dia 7 de Julho e foi disponibilizado no dia 28 de julho do mesmo ano.

* Da Vinci Machine: Suporte para linguagens dinâmicas
* Projeto Coin
* Strings in switch
* Automatic resource management in try-statement
* Diamond
* Simplified varargs 
* Binary integer literals
*  Numeric literals
* mult-try
* Novo pacote utilitário de concorrência: JSR 166
* NIO2: novos biblioteca para IO


#### Java SE 8 (18 de março de 2014)

O Java 8 foi entregue no dia 18 de março de 2014 e nessa versão foi incluída alguns recursos que antes estavam planejados para o Java 7. Os recursos submetidos para essa versão foram baseadas em propostas de melhorias do JDK, os JEPS. Dentre essas melhorias podemos destacar:

* JSR 223, JEP 174: **Projeto Nashorn**, um executor runtime de JavaScript, permitindo a execução de código JavaScript dentro da aplicação. Esse projeto teve como objetivo ser o sucessor do **Rhino**, usando `Invoke Dynamic` em vez de `reflection`.
* JSR 335, JEP 126: Suporte para expressões lambdas
* JSR 310, JEP 150: Date and Time API
* JEP 122: Remoção do Permanent generation

