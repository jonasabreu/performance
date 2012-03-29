---
layout: post
title: Metas de otimização em aplicações existentes
permalink: /metas-otimizacao-aplicacoes-existentes.html
category: conceitos
---

Uma coisa fundamental que deve ser feita antes de qualquer esforço de otimização é definir qual é a 
meta de otimização.

Isso é importante para evitar que fiquemos tentando extrair cada millisegundo possível, enquanto que 
poderíamos aproveitar melhor esse tempo para diversas outras coisas.

Quando vamos otimizar uma aplicação já existente, é um pouco mais fácil definir as metas. E você não 
precisa definir elas atravéz de cálculos super complexos. Um pouco de bom senso é o suficiente.

Por exemplo, no meu último cliente, defini a meta mais ou menos assim:

No ano anterior, meu cliente teve um pico de acesso de `X` requisições em um dia. Esse ano eles esperavam um crescimento
de `30%`, então o cluster deles precisava aguentar `1,3X`.

Para não perder tempo analisando o histograma de acesso deles e vendo qual seria o máximo por hora, 
simplesmente trabalhei com o pior caso que consegui imaginar que seria todo aquele acesso em `2 horas` 
(eles tinham 2 picos de acesso de mais ou menos 1 hora por dia).

Isso implica (assumindo uma distribuição uniforme - longe da realidade, mas bom o suficiente nesse caso)
que o cluster precisava aguentar `0,65X por hora`, `0,01X por minuto` ou `0.0002X por segundo`.

Por causa do tamanho do cluster deles, isso dava mais ou menos `40 req/s` em cada máquina. Cada máquina tinha
4 cores então assumi `10 / core` a cada segundo o que dava **100ms** para cada requisição no backend (que era o que
eu estava otimizando).

Parti então para a otimização propriamente dita. No momento que a página ficava abaixo de 100ms, era a hora 
de parar e partir para a próxima.

Nesse caso específico eu preferi trabalhar levando em conta apenas os piores casos, porque ao mesmo
tempo em que eu otimizava, tinha uma equipe bem grande acrescentado funcionalidade numa velocidade bem alta.

Mas você não precisa ser tão pessimista.

Normalmente vai ser melhor estabelecer uma meta menos agressiva e ir ajustando ela com o passar do tempo. O
meu caso era meio emergêncial, então uma meta mais agressiva fez sentido.
