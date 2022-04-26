### Garbage Collector


Diferente de algumas linguagens o Java possui um gerenciamento de memória automática, isso permite que a memória de um objeto não mais utilizado seja retomada, essa certamente é uma das grandes vantagem da plataforma em relação ao `C`. O primeiro desafio da JVM é identificar quais objetos dispensáveis, e assim retomar a memória com isso foi realizado várias técnicas para assim o fazer.



![Estilo mark and sweep, em que os objetos utilizados são marcados, os não utilizados são marcados, após esses dois passos o próximo passo será desfragmentar a memória principal.](chapter_6_1.png)


O mais conhecido certamente é o **Mark and Sweep**, basicamente dois processos que marca os objetos utilizados e no final os objetos não marcados são dispensáveis para retomar a memória, o maior problema é que todos os processos são parados para executar tal procedimento inviabilizando chamá-lo constantemente. Em função desse problema citado anteriormente falaremos do segundo algorismo, que leva em consideração que muitos objetos não possuem uma longa vida, no entanto, alguns levam bastante tempo na memória, assim os algoritmos se baseia em gerações que divide a memória em três partes (jovem, efetiva e permanente).

Para melhor gerenciar o coletor de lixo a memória heap é dividia basicamente em algumas partes:


* **Young Generation**: É onde contém os objetos recém-criados, a grande maioria dos objetos morrem dentro dessa área. Ela é subdivida em duas partes: **Eden** (local aonde o objetos nascem) e **Survivers(N)** locais aonde os objetos vão passando até sair da Young Generation. O seu funcionamento é de maneira simples: Os objetos nascem no **Eden**, depois de um tempo, os objetos são copiados “vivos” para os **Survivers**, os objetos que não foram copiados não são apagados, mas no futuro, outros objetos ocuparão seu espaço. 
* Com o passar das coleções os objetos existentes saem da **Young** e vão para **Tenured generation**, nesse espaço o gerenciamento de objetos é realizado de forma diferente, assim não há cópia, existem algoritmos derivados do **Swep and Mark**, com os objetos apagados a próxima preocupação será em relação a fragmentação do registrador, assim haverá o processo de compactação dos dados.


![Divisão da memória por geração](chapter_6_2.png)
 
Comentado um pouco sobre os processos de **minor collector** (procedimento de generation que cópia objetos para registradores sobreviventes) e o **maior collector** (procedimento cujo os algoritmos são derivados de **Mark and Swep** que apaga os objetos não utilizados e quando fragmentada a memória haverá o procedimento de compactação, vale lembrar que para tal procedimento a JVM para todos os seus processos). O objetivo agora será falar o estilo ou o modo dos Garbage Collector.

#### Implementação Serial


Esse estilo é muito indicado para pequenas aplicações ou hardware de pequeno poder computacional e apenas um processador, monocore, ele se na baseia na execução dos processos ,maior e menor collector, utilizando apenas uma `Thread`, desse modo pode economizar recursos, porém caso haja um grande número de memória haverá um grande delay. 

![Serial](chapter_6_3.png)

#### Implementação Paralelo



Trabalha de forma semelhante da serial, no entanto, será utilizado duas ou mais `Threads` por coleção, assim o processo tende a ser realizar em um tempo menor, porém utilizando mais recursos de máquina.

![Implementação Paralelo](chapter_6_4.png)

#### Implementação Concurrent



Esse também executa processos em paralelos, no entanto, o seu objetivo é diminuir o tempo do maior collector, mesmo que para isso o execute várias vezes. Indicado para muitos objetos duram muito tempo, assim eles ficam na **Turnered**. Em resumo seu processo divide realizar marcação em que todas as `Thread` estão paradas e marcações concorrentes, mas a remoção dos objetos ocorrem sem nenhum processo parar, o único problema desse estilo é o fato que não há compactação de dados periódicos, apenas quando se torna crítico (usando o **SerialOdl**).


![Implementação concurrent](chapter_6_5.png)

#### Implementação Incremental Concurrent



Também é concorrente, mas é realizado de forma incremental (realizado aos poucos e agendado entre as minor-collector) seu funcionamento é bem semelhante ao anterior, mas adiciona um processo que é redimensionar e preparar os dados para uma próxima coleção o ciclo que controla o tempo que o colector fica no processador. Caso tenha problemas com fragmentação, ele também acionará o serialOdl (que além de remover os dados também compactará os objetos sobreviventes).

![Incremental concurrent](chapter_6_6.png)

#### Implementação Garbage First
	


Lançado na versão 7 do Java, o **Garbage first**, é coletor paralelo projetada para ter um grande throughput, ele foi projetado para sistemas com uma alta quantidade de memória e de processadores. Para alcançar seu objetivo ele divide igualmente o tamanho do **Heap**. Assim como os dois últimos concorrentes, ele possui uma fase em que realiza a marcação concorrente, e realiza o calculo de objetos alcançáveis de cada região, assim de tempos em tempos, todos os processos são parados os objetos vivos são copiados para outra região, fazendo com que a região em questão seja totalmente tomada. Terão maior prioridade as regiões com o maior número de objetos “mortos” (assim se terá menos trabalho em realizar a copia para a outra área). O **G1** veio para substituir os tipos concorrente de coleção (`CMS` e `I-CMS`) devido a lacuna que ambos deixavam.

Não ter um tempo determinado para deixar o processador e a compactação do heap (uma vez que muito crítica chamada o serialOdl). O **G1** toma como estratégia o fato de ser mais fácil controlar pequenas regiões do que uma geração, um outro aspecto é que tão logo as memórias existentes tenha sido copiado para uma nova área, a anterior é considerada uma área limpa.


![G1](chapter_6_7.png)
