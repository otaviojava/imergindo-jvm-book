#### Operações aritméticas: 

Elas são realizadas com os dois primeiros valores na pilha de operações e retornando o resultado. O seu processamento é subdividido em flutuantes e inteiros que possuem comportamentos diferentes para alguns resultados, por exemplo, em estouro de pilha e divisão por zero.

* **adicionar**: iadd, ladd, fadd, dadd. 
* **subtrair**: isub, lsub, fsub, dsub. 
* **multiplicar**: imul, lmul, fmul, dmul. 
* **divisão**: idiv, ldiv, fdiv, ddiv. 
* **resto**: irem, lrem, frem, drem. 
* **negação**: ineg, lneg, fneg, dneg. 
* **deslocar**: ishl, sidh, iushr, lshl, lshr, lushr. 
* **bit a bit  *"or"***: ior, lor. 
* **bit a bit *"and"***: iand, a terra. 
* **bit a bit ou exclusivo**: ixor, lxor. 
* **Variável local incremente**: `iinc`. 
* **Comparação**: `dcmpg`, `dcmpl`, `fcmpg`, `fcmpl`, `lcmp`.