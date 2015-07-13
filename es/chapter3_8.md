
### Recapitulando


Con esto hemos hablado de los registros de la JVM, vale aclarar que algunos son exclusivos para los `Threads` y otros no. Las **pila nativa** son importantes para obtener recursos de la máquina, no obtantes, sus valores son indefinidos, luego las  **pilas Java** son creadas, tan pronto, un método es iniciado y es subdividido en **frames**, estas pilas son especificas para `Thread`. El registro **PC** no posee información, apenas apunta a la instrucción que está siendo ejecutada y posee una por `Thread`. El **Heap** es la  **method Area** y es compartidad entre la JVM, todos los `Threads`, y tiene la responsabilidad de guardar la instancia de los objetos, los streams e información de la clase respectivamente.
