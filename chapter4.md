### ByteCodes



Uma vez tendo noção dos registradores e aonde ficam armazenados cada valor na JVM, será falado um pouco sobre o funcionamento das instruções, ela possui opcode e no tamanho de 1 byte, daí o **bytecode**. Cada **bytecode** representa uma ação ou uma operação. A maioria das operações desse código operam para um tipo específico de valor, por exemplo, `iload` (carregar um `int` para a pilha) e o `fload` (carrega um `float` para a pilha) possuem operações semelhantes, no entanto, **bytecodes** diferentes. Uma boa dica para saber o tipo operado é saber a letra inicial da operação: **i** para uma operação de inteiro, **l** para `long`, **s** para `short`, **b** para `byte`, **c** para `char`, **f** para `float`, **d** para `double` e a para referência. 