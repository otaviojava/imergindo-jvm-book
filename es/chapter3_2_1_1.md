##### Stack variables



Cada **frame** contém um vetor para armazenar variáveis locais e os parâmetros e esse tamanho é definido em tempo de execução. Nesse vetor as variáveis `double` e `long` ocupam dois elementos do vetor e são armazenados consequentemente. Variáveis do tipo `int` e `returnAdress` ocupam um elemento desse vetor (`byte`, `short` e `char` são convertidos para `int`). Caso o método seja da instância, não seja estático, o primeiro elemento desse vetor será ocupado pela instância que está executando esse método e em seguida os parâmetros, na ordem que foram passados. Caso o método seja da classe, o método seja estático, Não haverá referência da instância que chama o método, assim o primeiro elemento será os parâmetros.


![As pilhas de variáveis são compostas por índices de 32 bits, assim as variáveis do tipo double e long ocupam dois espaços contínuos e as outras variáveis apenas um.](imagens/chapter_3_4.png)