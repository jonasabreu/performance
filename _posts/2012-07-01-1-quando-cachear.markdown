---
layout: post
title: Quando Cachear?
permalink: /quando-cachear.html
category: conceitos
---

Colocar cache em uma aplicação é uma troca clássica de memória por processamento. Você guarda um valor
pré-calculado e da próxima vez que precisar reutiliza ele, ao invéz de recalcular.

Mas isso não é sempre a melhor solução, mesmo que você tenha memória sobrando.

A cache coloca um nível de indireção no seu código e pode dificultar a manutenção dele dependendo de 
como for implementada, além de poder causar efeitos indesejados, como inconsistência de resultados
quando acontece alguma mudança nos dados.

Então quando cachear? Quando o custo de melhorar a performance sem cache for mais alto do que colocar
a cache e os possíveis problemas que ela pode trazer.

Por exemplo, muitas consultas em banco demoram muito porque estão mal escritas ou por falta de um índice
em alguma coluna no banco. Uma cache resolveria (em partes) o problema de performance, mas isso não muda
o fato de você precisar otimizar a sua consulta.

Uma cache pode amenizar o problema de você usar 10 serviços diferentes para construir uma página, mas se 
você só precisa realmente de 4 desses serviços, é muito mais interessante deixar de acessar os outros 6 (sim,
isso é um caso óbvio, mas eu já vi mais de uma vez).

Enfim, cache é uma técnica muito boa, mas não deve ser usada indiscriminadamente.
