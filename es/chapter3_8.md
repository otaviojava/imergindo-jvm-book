### Resumen


Con eso se describió todo sobre los registros que tiene la JVM, vale recordar que algunas son exclusivas por `Threads`y otras no. La **pila nativa** es importante para obtener recursos de la máquina, no obstante, sus valores son indefinidos, y las **pilas Java** son creadas tan pronto un método es iniciado, este es subdividido en **frames**, ambas pilas son particulares por cada `Thread`. El registro **PC** no tiene información, solo apunta para la instrucción que está siendo ejecutada y tiene una por `Thread`. El **Heap** y el **method Area** son compartidas por la JVM, todas las `Threads`, y tiene la responsabilidad de almacenar la instancia de los objetos y los *streams* y la información de la clase, respectivamente.
