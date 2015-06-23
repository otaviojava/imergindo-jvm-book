## Se queres prever o futuro, estuda o passado


**JVM**, java virtual machine ou máquina virtual java, tem sua história inciada em 1992. O Green Project na época a linguagem era denominada de oak. Com o passar do tempo a máquina virtual foi evoluindo e ficando cada vez mais complexa. A linguagem Java possui uma sintaxe similar ao C++, ele pode ser usado de várias maneiras e é orientado a objetos e se tornou popular em conjunto com a web. A JVM funciona como o alicerce da plataforma Java ficando responsável por tratar todas as plataformas e Sistemas Operacionais de modo independente para a linguagem. A JVM não conhece absolutamente nada da linguagem Java, apenas o seu **bytecode**, que vem no formato `.class`,  que são as instruções da JVM (daí a possibilidade de portar outras linguagens para a JVM já que ele não roda Java e sim o bytecode). Esse `class` é o código compilado em java e representa uma classe ou interface em java. 


Do seu início até a presente data o Java teve diversas versões. Essas modificações são gerenciadas pelo **JCP**, Java Community Process (o comitê que rege as mudanças da plataforma java com cerca de 30 empresas), a partir de JSRs, Java Specification Requests, especificações que fornecem tais modificações e melhorias. A documentação da linguagem fica no JSL, Java Language Specification, documentação da JVM fica Java Virtual Machine Specification.


1.1 - Histórico da JVM

    	Antes de se falar dos aspectos do Java, como linguagem, plataforma e máquina virtual é interessante conhecer um pouco sobre a evolução que o Java vem sofrendo. O projeto nasceu em 1995 e a partir desta data veio sofrendo constante evolução com ajuda de empresas e da comunidade.

1.1.1 - JDK Alpha and Beta (1995) 

	Nas versões alfas e betas se tiveram uma máquina instável.
1.1.2 - JDK 1.0 (23 de janeiro de 1996) 

	Com o código nome Oak, que também foi o primeiro nome da linguagem. Na versão 1.0.2 foi lançado a primeira versão estável.

1.1.3 - JDK 1.1 (19 de fevereiro de 1997) 

Grandes melhorias e refatorações nos modelos de evento do AWT
Inner class adicionado a linguagem
JavaBeans 
JDBC 
RMI 
Reflection que suportava apenas introspecção apenas, nenhuma modificação em tempo real era possível

1.1.4 - J2SE 1.2 (8 de dezembro de 1998) 

	Com o codinome Plaground. Essa e as outras versões foram denominadas de Java 2, J2SE Java 2 Platform, Standard Edition, Houve modificações significantes nessa versão triplicando o código para 1520 classes em 59 pacotes incluindo:

palavra-chave strictfp 
A api do Swing foram integrados ao Core
Adicionando o JIT compilador
Java Plug-in
Java IDL, uma implementação CORBA IDL para interoperabilidade
Collections framework 

1.1.5 - J2SE 1.3 (8 de maio de 2000) 

	Com o codinome Kestrel, as modificações mais importantes foram:
HotSpot JVM incluído (a JVM HotSpot foi lançado em abril de 1999 para os 1,2 J2SE JVM)

RMI foi modificado para suportar a compatibilidade opcional com CORBA
JavaSound
Java Naming and Directory Interface (JNDI) incluído em bibliotecas centrais
Java Platform Debugger Architecture (ACDP)
Sintéticos classes de proxy

1.1.6 - J2SE 1.4 (6 de fevereiro de 2002)

	Com o codinome Merlin, foi a primeira versão para a plataforma desenvolvida pelo JCP como a JSR 59:

Alterações na linguagem
A palavra-chave assert( JSR 41)
Melhorias nas bibliotecas
Expressões regulares
Encadeamento de exceção permite uma exceção de maior nível encapsule uma exceção de menor nível.
Suporte ao Protocolo de internet versão 6 (IPv6)
Chamadas de IO (chamado de NIO) novos Input/Output (JSR 51)
API de loggin (JSR 47)
API para ler e escrever imagens in formatos como JPED e PNG
Integração com o XML e XSLT (JAXP) na JSR 63
Novas integrações com extensões de segurança e criptografia (JCE, JSSE, JAAS)
Java Web Start incluído (JSR 56)
API de preferências  (java.util.prefs) 

1.1.7 - J2SE 5.0 (30 de setembro de 2004) 


	Com o codinome Tiger, foi desenvolvida na JSR 176, teve seu final de vida em 8 de abril de 2008 e o encerramento do suporte dia 3 de novembro de 2009. O Tiger adicionou significantes melhorias para a linguagem:

Generics:  (JSR14).
Annotations: (JSR 175)
Autoboxing/unboxing: Conversão automática entre os tipos primitivos e as classes encapsuladas (JSR 201).
Enumerations: (JSR 201.) 
Varargs: 
for each loop
Correções para o Java Memory Model(Que define como Threads interagem através da memória).
Static imports 
Geração automática do stub para objetos RMI
Novo look and feel para o Swing chamado synth
Um pacote utilitário de concorrência (java.util.concurrent)
A classe Scanner 
Classe Scanner para analisar dados de input streams e buffers


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