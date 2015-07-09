### Method Area

Ese registro tiene la finalidad de guardar logicamente el stream de la clase, esa area es compartida entre todos los `Threads`. Logidamente s parte del Heap space. Por ser parte del Heap posee reconocimiento de memoria automático, Garbagge collector. Las clases contienen la siguiente información:



* El **qualified** de la clase (El qualifed es la dirección de la clase que esta definida por el paquete más `.` y el nombre de la Clase, por ejemplo, `java.lang.Object` o `java.util.Date`).
* El **qualified** de la clase padre (menos para las Interfaces es `java.lang.Object`).
* Información de si es una clase o interface.
* Los modificadores.
* Una lista con los **qualifieds** interfaces.


Para cada clase cargada en Java se carga un **constant pool**, que contiene la siguiente información:


* El **constant pool** de tipo (Para cada clase Cargada es creado un pool de constantes, ellos contienen links simbólicos a los métodos y a los atributos, además de, constantes existentes por tipo).
* Información de los atributos (el nombre del atributo, el tipo y su modificador).
* Información de los métodos (el nombre del método, su retorno, el número y tipo de parámetros, su orden, tipo y su modificador).
* Referencia para el `ClassLoader` (clase responsable para cargar la clase)
* Variables de clase (variables compartidas entre todas las clases, incluso constantes).
* Referencia de la clase (una instancia de `java.lang.Class` para toda clase cargada).