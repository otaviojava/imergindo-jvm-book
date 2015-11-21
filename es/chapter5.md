### Ciclo de vida de una clase


Toda clase tiene su ciclo de vida en la JVM, y comienza cuando esta nace dentro de la JVM, este proceso es hecho de modo *lazy*, es decir, la clase X será cargada en el momento en que fuera necesario, al instanciar un objeto se realiza el proceso de encontrar la representación binaria de la clase, cargar la información y colocar su clase dentro de la JVM, luego se crea el objeto. Todas las clases necesitan pasar por ese proceso inclusive la clase que inicia la JVM. En caso que la clase herede de una clase o implemente interfaces, ellas tendrán que ser cargadas primero. Como cada uno de esos procesos tienen detalles, se excluirán las acciones de cada uno.	

![El ciclo normal de una clase Java, primero es cargado dentro de la JVM, dentro de la memoria principal y convirtiendo en stream, en seguida sus instrucciones son “traducidas” para la ejecución nativa.](imagens/chapter_5_1.png)



La carga de clase consiste en subir la clase a la memoria principal y colocarla en la JVM, este proceso sucede una vez con **qualifield**, con ese stream cargado se realiza el parser al registro **method Area** y terminando este genera la interface que representa tal archivo, o `java.lang.Class`. 	

La interface `Class` es el produto del proceso de cargar la clase a la memoria principal, es la representación del archivo, con eso este contiene la información del mismo, como lista de los métodos, atributos, interfaces, anotaciones, etc.

Las clases a su vez, son cargadas por el `ClassLoader` (con excepción de los array que no tienen representación binaria).


En la JVM existen múltiples *class loaders* con diferentes reglas, podemos clasificarlas así: 

* **BootStrap** este se encuentra en la cima de la jerarquia de los *class loaders*, este objeto es responsable de cargar la API básica de Java, y los objetos que posean un altísimo nivel de confianza en la JVM. 
* **Extensión** es responsable por cargar las API estándar de Java como las de seguridad y *Collection*. 
* El **system** es el *class loader* estándar de la aplicación, es responsable de cargar las clases que están contenidas en el *classpath*. 
* Bajo el *System Class Loader* el usuario adicionará un *class loader*, que tiene algunos motivos especiales, entre ellos definir un grupo *class loader* específico para un dominio o aplicación, es el caso de los servidores de aplicación como **Tomcat** y **Glassfish**.
 

![Jerarquía de los Class Loaders](imagens/chapter_5_2.png)


Después que la clase sea cargada el próximo paso será linkearla en la JVM, este proceso consiste en la verificación de la clase recién cargada, este verifica la palabra-clave, si la estructura está correcta, el tamaño de los archivos, después de la verificación son asignadas en la memoria para los atributos y serán seteados los valores por default de los campos, son cargados los atributos estáticos, cerrando este proceso todos los link de referencia son sustituidos por links directos.

En la ultima fase será creada la instancia con la llamada al método constructor, siendo que antes es llamado el constructor de la superclase, no existe verificación para las interfaces solo si los métodos fueron implementados.


