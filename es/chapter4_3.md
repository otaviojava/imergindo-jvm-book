#### Conversión de valores

 
Las instrucciones de conversión de valores sirve para modificar el tipo de la variable (casting), esta variable puede tener ampliar su tipo, así: 

* **Promoción -a mayor precisión-**: de `int` a `long`, de `int` a `float`, de `int` a `double`. De `long` a `float` y de `float` a `double` (`i2l`, `i2f`, `i2d`, `l2f`, `l2d`, y `f2d`) con esta ampliación no se pierde la precisión del valor original. 
*  El **acortamiento -a menor precisión-** del tipo como: de `int` a `byte`, de `int` a `short`, de `int` a `char`, de `long` a `int`, de `long` a `float`, de `float` a `int` o a `long`, de `double` a `int`, de `double` a `long` o de `double` a `float` (`i2b`, `i2c`, `i2s`, `l2i`, `f2i`, `f2l`, `d2i`, `d2l`, y `d2f`) cabe recordar que en tales modificaciones existe la posibilidad de perder precisión o volcado del valor.
