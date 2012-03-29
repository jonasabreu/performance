---
layout: post
title: Otimização Prematura é a raiz de todos os males
permalink: /otimizacao-prematura.html
category: conceitos
---

Acho que um dos maiores causadores de problemas de performance é a frase 
"[Otimização prematura é a raiz de todos os males][1]" do [Donald Knuth][2].

Essa frase faz todo sentido. Deixar que performance influêncie o design do seu código **vai** produzir 
resultados bem ruins, como código de difícil manutenção, além de todo o tempo gasto para escrever o 
código otimizado que te deu 1 nano segundo a cada 10 requisições.

O problema é que muita gente usa essa frase como uma desculpa para entregar software lerdo para o cliente.

E [software lerdo faz seus clientes não gostarem de usar seu produto][3].

O grande ponto é que Otimização Prematura não é a otimização feita desde o começo do projeto. Otimização 
prematura é a otimização feita sem ter a menor noção do impacto que aquilo terá no projeto e sem ter como
verificar que a [melhoria](/metas-otimizacao-aplicacoes-existentes.html) aconteceu (efetivamente) e que ela 
continua efetiva durante o desenvolvimento.

Não adianta achar que é possível simplesmente pegar uma aplicação depois de 6 meses de desenvolvimento
e achar que com dois dias de trabalho você consegue melhorar a aplicação. Em geral não existem 
"low hanging fruits". O que você tem que fazer é otimizar diversos pontos da aplicação ou até mesmo
mudar um pouco a arquitetura (como o uso de caches) ou o negócio (como acrescentar uma diferença de 1 minuto 
entre uma modificação ser feita e estar disponível).

[1]: http://en.wikipedia.org/wiki/Program_optimization
[2]: http://en.wikipedia.org/wiki/Donald_Knuth
[3]: http://www.scribd.com/doc/4970486/Make-Data-Useful-by-Greg-Linden-Amazoncom
