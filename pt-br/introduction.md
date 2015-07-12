## Falando um pouco sobre JVM


Certamente o Java é atualmente uma das linguagens mais usadas e populares no mundo, sendo que o seu maior diferencial não está na linguagem e sim na **JVM**, máquina virtual Java. A JVM vem sendo alvo de muitos estudos e pesquisas, afinal conhecer bem a JVM vai garantir ao desenvolvedor Java, maneiras para tirar o melhor proveito da linguagem e da plataforma além de programar de maneira mais eficiente levando em consideração tudo o que a JVM pode fazer por ele e ajudando a mesma a te ajudar. Com esse objetivo estou criando esse pequeno texto, ajudar a comunidade brasileira a conhecer a **JVM**.

Esse material é fruto dos meus trabalhos junto com o *OpenJDK*. A JVM open source e ,a partir da versão 7, se tornou a implementação de referência. Ao contrário do que muitas pessoas imaginam, existem milhões de máquinas virtuais, dentre as mais populares está a HotSpot (também conhecida como a JVM da Oracle). O OpenJDK é um projeto é vivo com ajuda de muitas empresas (Oracle, Intel, RedHat, AMD, Google, etc.), mas principalmente com a grande ajuda da comunidade, que dentre as diversas frentes de trabalho que existem podemos destacar o Adote o OpenJDK que visa a evolução da plataforma e do Java Livre (ajudando na refatoração, evangelizando sobre o OpenJDK, identificando e corrigindo bugs). 


Para facilitar o entendimento do leitor esse trabalho foi dividido em seis partes:


 * 	A primeira falará um pouco sobre o Java, fazendo a devida separação entre linguagem, plataforma e máquina virtual além de falar um pouco sobre a história do Java e da sua evolução junto com as versões.

* Em seguida se falará sobre o funcionamento básico da JVM, fará a distinção básica entre o Java linguagem e da máquina virtual, já que a última precisa ser compilada para que a linguagem seja multiplataforma, o ciclo de vida da JVM e dos processos em paralelo que nascem com uma aplicação Java. 

* Saber aonde fica cada informação dentro da JVM e o nome dos seus respectivos registradores. Será o alvo dessa terceira parte do trabalho. Saberá quais registradores serão compartilhados por todas as `Threads` e aqueles que não serão, assim nascem e morrem com a sua respectiva Thread. 

* O **bytecode**, a linguagem da Máquina virtual, pouco é explicado sobre ela, mas são graças aos seus opcodes que a JVM é multiplataforma. Nessa parte se verá quão diferente é o seu código em Java e do produto gerado, o bytecode, além da estrutura que a classe adquire após o processo de compilação.

* A **JVM** consiste em um processo básico de pegar a informação da classe, gerar stream para dentro da JVM (Naturalmente na memória principal) e executá-lo o tornando em código nativo, esse processo de carregar uma classe é feita em tempo de execução, ou seja, só é carregada a classe X no momento em que ela for chamada, não basta estar apenas no import, caso essa classe tenha um pai ou implemente interfaces elas serão carregadas antes dessa classe X. Toda classe possui um ciclo de vida e conheça um pouco mais sobre este ciclo na parte número cinco.
	
* Um grande diferencial da JVM é o recurso de gerenciamento automático da memória, esse processo consistem em matar e recuperar memória de objetos que não estão mais sendo utilizados, esse é o papel do **Garbage Collector**. Conheça um pouco mais sobre as implementações e em quais situações elas são mais aconselhadas.

Para finalizar será demonstrada uma visão prática do JNI e do projeto OpenJDK além dos conceitos de compilar a JVM. 