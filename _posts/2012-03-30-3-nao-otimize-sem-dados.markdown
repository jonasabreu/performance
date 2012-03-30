---
layout: post
title: Não otimize sem dados
permalink: /nao-otimize-sem-dados.html
category: conceitos
---

Certa vez em uma consultoria, assim que ia começar os testes de performance, um dos desenvolvedores me 
mostrou um ponto que ele tinha certeza de que melhoraria a performance da aplicação.

Passei dois dias para conseguir entender o código e cachear a resposta produzida.

Montamos um teste de performance e rodamos com a versão não otimizada. Depois rodamos com a versão otimizada.

Basicamente não teve nenhuma diferença. Analisando friamente mais tarde, vi a bobagem que tinha feito.

O problema não foi confiar no que o desenvolvedor falou. Ele tinha um conhecimento muito maior que o 
meu sobre a aplicação e estava sinceramente tentando me ajudar a fazer o melhor trabalho possível.

O problema é que ele também não sabia onde que era gasto a maior parte do tempo de processamento. Isso nós 
nunca sabemos com certeza quando desenvolvemos. Só sabemos quando fazemos um teste de performance.

Essa é a minha principal razão para sempre falar para os meus times trabalharem sem se preocupar com
performance quando eu estou dedicado à isso. Programem o melhor que puder e se precisar eu otimizo.

Assim evitamos gastar tempo com otimizações que não vão produzir efeito algum.
