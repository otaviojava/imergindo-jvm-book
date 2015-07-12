### Program Counter


El Registro **PC**, Program counter, es creado tan pronto un `Thread` es creado, es decir, cada `Thread` posee el suyo. Este puede almacenar dos tipos de datos: 

1. 
Punteros nativos
1. 
returnAdress

Esos datos poseen informaciones como la instrucción que esta siendo ejecutada por el `Thread`. Si el metodo ejecutado fuera nativo **PC** será un puntero y no tiene su valor definido, al contrario, este tendrá la dirección de instrucción, el **returnAdress**.

![Funcionamiento de PC](imagens/chapter_3_2.png)