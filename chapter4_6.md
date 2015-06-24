#### Chamada de métodos e retorno de valores

As chamadas de um método são: 

* **invokevirtual**: Chama um método de uma instância
* **invokeinterface**: Chama um método de uma interface
* **invokespecial**: Chamada de um método privado ou da superclasse
* **invokestatic**: Realiza a chamada de um método estático
* **invokedynamic**: Método que constrói um objeto 

O retorno de uma instrução pode ser definido (`ireturn`, `lreturn`, `freturn`, `dreturn` e `areturn`). Durante a execução do método caso seja interrompida de maneira inesperada com uma exceção a chamada athrow é realizada. Os métodos síncronos são possíveis graças à presença de um simples encapsulando chamado de monitor, esses tipos de métodos são definidos pela flag `ACC_SYNCHRONIZED` em seu constate pool, que quando possui tal flag o método entra no monitor(`monitorenter`) e é executado, e nenhuma outra Thread pode acessá-lo, e sai (`monitorexit`) quando seu método é encerrado (de um modo normal ou por interrupção).