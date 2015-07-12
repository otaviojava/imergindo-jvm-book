### Method Area


Este registrador tiene la finalidad de almacenar logicamente el stream de la clase, esa área es compartida entre todos los `Threads`. Logicamente forma parte del Heap Space. Por ser parte tiene la labor de reunir la memoria automática, Garbage Collector. Las clases contienen las siguientes informaciones:



* El **qualified** de la clase (El qualifed es la dirección de su clase que es definido por el paquete mas `.` y el nombre de la Clase, por ejemplo, `java.lang.Object` o `java.util.Date`).
* El **qualified** de la clase padre (menos para las Interfaces es `java.lang.Object`).
* Información si es un clase o interface.
* Los modificadores.
* La lista con los **qualifieds** de las interfaces.


Para cada clase cargada en Java es cargada un **constant pool**, que contiene las siguientes informaciones:


* El **constant pool** de tipo (Para cada clase cargada es creada un pool de constant, este contiene el link simbólico para los metodos y para los atributos ademas de las constantes existentes en el tipo).
* informaciones de los atributos (el nombre del atributo, el tipo y su modificador).
* información de los metodos (el nombre del metodo, su retorno, el número y tipo de los parametros en orden y el tipo y su modificador).
* Referencia para `ClassLoader` (clase responsable para cargar la clase)
* Variables de la clase (variables compartidas entre todas las clases eso incluye las constantes).
* Referencia de la clase (una instancia de `java.lang.Class` para toda clase cargada).