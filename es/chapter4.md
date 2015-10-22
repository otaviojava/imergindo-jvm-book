### ByteCodes



Una vez que tiene la noción de registros y dónde se almacena cada valor de la JVM, hablaremos un poco sobre el funcionamiento de las instrucciones, esta tiene código de operación y tamaño de 1 byte, de ahi el **bytecode**. Cada **bytecode** representa una acción o una operación. La mayoría de las operaciones de ese código operan para un tipo específico de valor, por ejemplo, `iload` (carga un `int` a la pila) y `fload` (carga un `float` a la pila) tienen operaciones similares, sin embargo, **bytecodes** diferentes. Un buen truco para saber el tipo operador es saber la letra inicial de la operación: **i** para una operación de entero, **l** para `long`, **s** para `short`, **b** para `byte`, **c** para `char`, **f** para `float`, **d** para `double` y **a** para `referencia`. 
