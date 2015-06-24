#### Conversão de valores

 
As instruções de conversão de valores serve para modificar o tipo da variável, essa variável pode ter seu tipo ampliado como: 

int para long, int para float, int para double. long para float e float para double (i2l, i2f, i2d, l2f, l2d, e f2d) esse ampliamento perde não perde a precisão do valor original. 
O encurtamento do tipo como: int para byte, int para short, int para char, long para int, long para float para int ou long para, double para int, double para long ou double para float (i2b, i2c, i2s, l2i, f2i, f2l, d2i, d2l, e d2f) vale lembrar que tais modificações existe a possibilidade de perder precisão ou estouro do valor.

4_4: 	Criação e manipulação de objetos: 

Instruções para a criação e manipulação de instâncias (new) e arrays (newarray, anewarray, multianewarray). Acessar atributos estáticos ou da instância de uma classe (getfield, putfield, getstatic, putstatic). Carregar (baload, caload, saload, iaload, laload, faload, daload, aaload) e salvar(bastore, castore, sastore, iastore, lastore, fastore, dastore e aastore) vetores além do seu tamanho (arraylength). Checa a propriedade da instância ou array (instanceof e checkcast).