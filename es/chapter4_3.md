#### Conversión de valores

 
Las instrucciones de conversión de valores sirve para modificar el tipo de la variable, esta variable pode tener su tipo ampliado como: 

* **Promoción**: `int` para `long`, `int` para `float`, `int` para `double`. `long` para `float` e `float` para `double` (`i2l`, `i2f`, `i2d`, `l2f`, `l2d`, e `f2d`) este ampliamento pierde no pierde la precisión del valor original. 
*  El **acortamiento** del tipo como: `int` para `byte`, `int` para `short`, `int` para `char`, `long` para `int`, `long` para `float` para `int` ou `long` para, `double` para `int`, `double` para `long` ou `double` para `float` (`i2b`, `i2c`, `i2s`, `l2i`, `f2i`, `f2l`, `d2i`, `d2l`, e `d2f`) cabe recordar que tales modificaciones existe la posibilidad de perder precisión o volcado del valor.
