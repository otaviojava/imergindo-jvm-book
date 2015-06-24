## Registradores da JVM



Falado um pouco sobre os tipos de dados que são armazenados na JVM e o seu tamanho. É necessário também que se tenha ciência de onde são armazenadas tais informações. A JVM usa registradores para armazenar várias coisas sendo que para todo tipo de dado existe um local específico. Durante a execução de um programa existem registrados que são compartilhados entre toda a JVM e outros que tem a visibilidade da `Thread` corrente.

![Os registradores da JVM, Method Area e o Heap são compartilhados por toda a JVM e o PC Counter, Pilha Java e a Pilha Nativa cada Thread possui a sua.](imagens/chapter_3_1.png)