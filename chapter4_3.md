#### Conversão de valores

 
As instruções de conversão de valores serve para modificar o tipo da variável, essa variável pode ter seu tipo ampliado como: 

* **Promoção**: `int` para `long`, `int` para `float`, `int` para `double`. `long` para `float` e `float` para `double` (`i2l`, `i2f`, `i2d`, `l2f`, `l2d`, e `f2d`) esse ampliamento perde não perde a precisão do valor original. 
*  O **encurtamento** do tipo como: `int` para `byte`, `int` para `short`, `int` para `char`, `long` para `int`, `long` para `float` para `int` ou `long` para, `double` para `int`, `double` para `long` ou `double` para `float` (`i2b`, `i2c`, `i2s`, `l2i`, `f2i`, `f2l`, `d2i`, `d2l`, e `d2f`) vale lembrar que tais modificações existe a possibilidade de perder precisão ou estouro do valor.
