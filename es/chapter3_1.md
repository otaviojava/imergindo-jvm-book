### Program Counter


El registro **PC**, Program counter, es creado inmediatamente que un `Thread` es creado, o sea, cada `Thread` posee el suyo. El puede guardar dos tipos de datos: 

1. 
Punteros nativos
1. 
returnAdress

Esos datos poseen información de la instrucción que esta siendo ejecutada por el `Thread`. Si el metodo ejecutivo es nativo o **PC** será un puntero y no tendrá un valor definido, caso contrario, el tendrá la dirección de la instrucción, o **returnAdress**.

![Funcionamiento de PC](imagens/chapter_3_2.png)