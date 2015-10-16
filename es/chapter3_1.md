### Program Counter


El registro **PC**, Program Counter, es creado tan pronto un `Thread` es creado, es decir, cada `Thread` posee el suyo. Este puede almacenar dos tipos de datos: 

1. Punteros nativos
2. returnAdress

Esos datos poseen información como la instrucción que esta siendo ejecutada por el `Thread`. Si el método ejecutado fuera nativo **PC** será un puntero y no tiene un valor definido, al contrario, este tendrá la dirección de instrucción, el **returnAdress**.

![Funcionamiento de PC](imagens/chapter_3_2.png)
