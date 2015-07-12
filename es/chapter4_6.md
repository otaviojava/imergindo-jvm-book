#### Llamadas de metodos y retorno de valores

Las lamadas de un metodo son: 

* **invokevirtual**: Llama un metodo de una instancia
* **invokeinterface**: Llama un metodo de una interface
* **invokespecial**: Llamadas de un metodo privado o de la superclase
* **invokestatic**: Realiza la llamada de un metodo estático
* **invokedynamic**: metodo que construye un objeto 

El retorno de una instrucción puede ser definido (`ireturn`, `lreturn`, `freturn`, `dreturn` y `areturn`). Durante la ejecución del metodo en caso sea interrumpida de manera inesperada con una excepción la llamada athrow es realizada. Los metodos síncronos son posibles gracias a la presencia de un simple encapsulado llamado de monitor, esos tipos de metodos son definidos por el flag `ACC_SYNCHRONIZED` en su constast pool, que cuando tiene tal flag el metodo entra en el monitor(`monitorenter`) y es ejecutado, y ningun otro Thread puede accesarlo, y sale (`monitorexit`) cuando su metodo es cerrado (de un modo normal o por interrupción).