#### Llamadas de métodos y retorno de valores

Las lamadas de un método son: 

* **invokevirtual**: Llama un método de una instancia
* **invokeinterface**: Llama un método de una interface
* **invokespecial**: Llamadas de un método privado o de la superclase
* **invokestatic**: Realiza la llamada de un método estático
* **invokedynamic**: método que construye un objeto 

El retorno de una instrucción puede ser definido (`ireturn`, `lreturn`, `freturn`, `dreturn` y `areturn`). Durante la ejecución del método en caso sea interrumpida de manera inesperada con una excepción se realiza la llamada a throw. Los métodos síncronos son posibles gracias a la presencia de un simple encapsulado llamado de monitor, esos tipos de métodos son definidos por el flag `ACC_SYNCHRONIZED` en su *constast pool*, que cuando tiene tal flag el método entra en el monitor(`monitorenter`) y es ejecutado, y ningun otro *Thread* puede accesarlo, y sale (`monitorexit`) cuando su método es cerrado (de un modo normal o por interrupción).
