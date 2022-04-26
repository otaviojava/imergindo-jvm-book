#### Implementação Incremental Concurrent



Também é concorrente, mas é realizado de forma incremental (realizado aos poucos e agendado entre as minor-collector) seu funcionamento é bem semelhante ao anterior, mas adiciona um processo que é redimensionar e preparar os dados para uma próxima coleção o ciclo que controla o tempo que o colector fica no processador. Caso tenha problemas com fragmentação, ele também acionará o serialOdl (que além de remover os dados também compactará os objetos sobreviventes).

![Incremental concurrent](imagens/chapter_6_6.png)