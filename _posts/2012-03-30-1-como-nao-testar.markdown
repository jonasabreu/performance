---
layout: post
title: Como não testar uma aplicação
permalink: /como-nao-testar.html
category: conceitos
---

Acho que a forma que mais vi aplicações serem testadas até hoje era mais ou menos a seguinte:

* Faça um script que bata em dezenas de urls diferentes
* Compare o tempo que demorou hoje com a semana passada
* Mexa um pouco na aplicação
* Rode novamente o teste que demora 2 horas para terminar
* Mexa mais um pouco na aplicação
* Considere o ganho como suficiente e só pense novamente nisso daqui uma semana

Eu sinceramente entendo o que as pessoas estão pensando quando tentam reproduzir o comportamento de usuários
**reais** na aplicação. Você está tentando aproximar o máximo possível da realidade para que seus esforços 
não sejam em vão.

O problema é que testando dessa forma, o máximo que você consegue é otimizar **um** fluxo de **um** usuário. O 
seu ganho geral é bem próximo à **zero**.

As interações dos seus usuários com o software são muito mais complexas do que nós vamos conseguir modelar, então
precisamos de uma [estratégia diferente][1].

O meu maior problema com esse tipo de teste é que ele simplesmente não te dá um resultado confiável.

Existe um efeito em estatística chamado [Confounding][2] [Factor][3], que basicamente é a interferência de 
variáveis não previstas com o que você está tentando medir. E isso basicamente te leva para direções erradas.

E conforme você tenta medir mais coisas (ou coisas mais complexas) de uma única vez, a possibilidade de uma
variável não prevista atrapalhar o seu trabalho aumenta.

Essa é a razão de eu preferir reduzir o máximo que faça sentido o escopo do que pretendo otimizar. Apenas tome 
cuidado para não cair em [micro otimizações][4].

[1]: /como-testar.html
[2]: http://stats.org/in_depth/faq/confounding_factors.htm
[3]: http://en.wikipedia.org/wiki/Confounding
[4]: /micro-otimizacao.html
