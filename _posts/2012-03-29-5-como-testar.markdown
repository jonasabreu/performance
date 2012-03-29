---
layout: post
title: Como testar a performance de uma aplicação
permalink: /como-testar.html
category: conceitos
---

Eu conheci realmente pouca gente que sabia testar uma aplicação com relação à performance.

A maioria das pessoas que vi testando obtêm dados que simplesmente levam à direções erradas
ou que não informam muita coisa.

A principal regra que eu tenho quando vou testar uma aplicação é **testar apenas uma coisa
por vez**.

O objetivo disso é reduzir ao máximo a interferência de outras variáveis no meu teste.

Por exemplo, eu costumo escolher uma página e testá-la fazendo diversas requisições (+2000)
e acompanhando em um [profiler](/visual-vm.html) até notar um padrão específico de gasto de 
tempo.

Mas isso em geral tem muita influência da latência de rede (no acesso ao banco, por exemplo)
que costuma ser bem diferente do ambiente de produção.

Para contornar esse problema, eu costumo medir separadamente quanto tempo é gasto em cada
pedaço da minha aplicação e me foco nas classes que estão no pedaço que consome mais tempo
do que deveria.

Essas medições em pedaços menores me permitem ter certeza de onde estão os gargalos de 
performance.

Se eu somente olhar de fora, posso no máximo saber que uma página está lenta. Mas não sei
onde olhar para melhorar a performance.

