---
layout: post
title: Performance Probe
permalink: /performance-probe.html
category: ferramentas
---

Uma coisa que sempre costumo fazer para reduzir o [Confounding Factor][1] nos [testes de performance][2] é separar blocos
que façam sentido dentro da aplicação e analiso eles individualmente.

Por exemplo, separar as conexões de rede costuma ser fundamental, porque costumo testar a aplicação fora do ambiente de produção, que em geral tem uma rede dedicada de alta performance.

Depois disso, algumas vezes separo também a camada de visualização. Um caso que fiz isso foi de uma aplicação que usava 
Xslt com várias estensões para gerar a view, o que em geral consumia 60% do tempo de processamento da requisição.

Pra fazer isso, a melhor forma que encontrei foi colocar dentro da aplicação uma classe boba que simplesmente mede
o tempo gasto em cada um desses pedaços, que é o que chamo de Performance Probe.

A implementação disso não tem nenhum segredo. É apenas uma classe com vários métodos _static_ que marcam o começo
e o fim de cada pedaço da aplicação e que no fim da requisição imprime no console o que foi gasto de tempo.

A grande vantagem é que isso me dá medidas que são mais fáceis de interpretar, mas ao mesmo tempo não são tão pequenas
quanto o tempo gasto por um método.

Depois disso parto para o [profiler][3], já sabendo em que parte da aplicação focar.


[1]: /como-nao-testar.html
[2]: /como-testar.html
[3]: /visual-vm.html
