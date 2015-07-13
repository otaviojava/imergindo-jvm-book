### Java Stack (Java virtual machine stack)


Así como el **PC**, este es un registro privado para cada `Thread`, dicho registro almacena **frames** (será visto al frente). Su funcionamiento es similar a los lenguajes clasicos como `C`, y sirven para guardar variables locales y resultados parciales, invocaciones y resultados de métodos. El no modifica las variables directamente sino que agrega o remueve frames del registro. Tan pronto como el `Thread` actual llama a un método, un nuevo frame es añadido con toda su información como parámetros, variables locales, etc. De la misma manera, cuando el método termina de forma normal, ya sea porque acaba el método, o por interrupción, cuando ocurre una excepción al interior del método, ese frame es descartado. El Java Stack puede ser de tamaño fijo o determinado dinámicamente.

