### Method Area


Este registro tiene la finalidad de almacenar lógicamente el stream de clases, esa área es compartida entre todos los `Threads`. Logicamente forma parte del Heap Space. Por ser parte tiene la labor de reunir la memoria automática, Garbage Collector. Las clases contienen la siguiente información:


* El **qualified** de la clase (El qualifed es la dirección de su clase que es definido por el paquete más `.` y el nombre de la clase, por ejemplo, `java.lang.Object` o `java.util.Date`).
* El **qualified** de la clase padre (menos para las Interfaces es `java.lang.Object`).
* Información si es una clase o una interface.
* Los modificadores.
* La lista con los **qualifieds** de las interfaces.


Para cada clase cargada en Java es cargada un **constant pool**, que contiene la siguiente información:


* El **constant pool** de tipo (Para cada clase cargada es creada un `pool de constant`, este contiene el link simbólico para los métodos y para los atributos, además de las constantes existentes en el tipo).
* información de los atributos (el nombre del atributo, el tipo y su modificador).
* información de los métodos (el nombre del método, su retorno, el número y tipo de los parámetros en orden y el tipo y su modificador).
* Referencia para `ClassLoader` (clase responsable de cargar la clase)
* Variables de la clase (variables compartidas entre todas las clases eso incluye las constantes).
* Referencia de la clase (una instancia de `java.lang.Class` para toda clase cargada).
