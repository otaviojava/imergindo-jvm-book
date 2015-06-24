#### Implementação Concurrent



Esse também executa processos em paralelos, no entanto, o seu objetivo é diminuir o tempo do maior collector, mesmo que para isso o execute várias vezes. Indicado para muitos objetos duram muito tempo, assim eles ficam na **Turnered**. Em resumo seu processo divide realizar marcação em que todas as `Thread` estão paradas e marcações concorrentes, mas a remoção dos objetos ocorrem sem nenhum processo parar, o único problema desse estilo é o fato que não há compactação de dados periódicos, apenas quando se torna crítico (usando o **SerialOdl**).


![Implementação concurrent](imagens/chapter_6_5.png)