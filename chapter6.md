### Garbage Collector


Diferente de algumas linguagens o Java possui um gerenciamento de memória automática, isso permite que a memória de um objeto não mais utilizado seja retomada, essa certamente é uma das grandes vantagem da plataforma em relação ao `C`. O primeiro desafio da JVM é identificar quais objetos dispensáveis, e assim retomar a memória com isso foi realizado várias técnicas para assim o fazer.



![Estilo mark and sweep, em que os objetos utilizados são marcados, os não utilizados são marcados, após esses dois passos o próximo passo será desfragmentar a memória principal.](imagens/chapter_6_1.png)


O mais conhecido certamente é o **Mark and Sweep**, basicamente dois processos que marca os objetos utilizados e no final os objetos não marcados são dispensáveis para retomar a memória, o maior problema é que todos os processos são parados para executar tal procedimento inviabilizando chamá-lo constantemente. Em função desse problema citado anteriormente falaremos do segundo algorismo, que leva em consideração que muitos objetos não possuem uma longa vida, no entanto, alguns levam bastante tempo na memória, assim os algoritmos se baseia em gerações que divide a memória em três partes (jovem, efetiva e permanente).

Para melhor gerenciar o coletor de lixo a memória heap é dividia basicamente em algumas partes:


* **Young Generation**: É onde contém os objetos recém-criados, a grande maioria dos objetos morrem dentro dessa área. Ela é subdivida em duas partes: **Eden** (local aonde o objetos nascem) e **Survivers(N)** locais aonde os objetos vão passando até sair da Young Generation. O seu funcionamento é de maneira simples: Os objetos nascem no **Eden**, depois de um tempo, os objetos são copiados “vivos” para os **Survivers**, os objetos que não foram copiados não são apagados, mas no futuro, outros objetos ocuparão seu espaço. 
* Com o passar das coleções os objetos existentes saem da **Young** e vão para **Tenured generation**, nesse espaço o gerenciamento de objetos é realizado de forma diferente, assim não há cópia, existem algoritmos derivados do **Swep and Mark**, com os objetos apagados a próxima preocupação será em relação a fragmentação do registrador, assim haverá o processo de compactação dos dados.


![Divisão da memória por geração](imagens/chapter_6_2.png)
 
Comentado um pouco sobre os processos de **minor collector** (procedimento de generation que cópia objetos para registradores sobreviventes) e o **maior collector** (procedimento cujo os algoritmos são derivados de **Mark and Swep** que apaga os objetos não utilizados e quando fragmentada a memória haverá o procedimento de compactação, vale lembrar que para tal procedimento a JVM para todos os seus processos). O objetivo agora será falar o estilo ou o modo dos Garbage Collector.
