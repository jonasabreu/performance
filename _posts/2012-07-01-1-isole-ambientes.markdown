---
layout: post
title: Isole (fisicamente) seus ambientes
permalink: /isole-fisicamente-ambientes.html
category: pitfalls
---

Passei por um problema estranho semana passada em um cliente. Duas máquinas do cluster estavam com load muito alto.

Depois de muito tempo procurando a causa, nada aparecia. Inclusive depois de derrubar as máquinas e subi-las novamente, 
nada mudava.

A única pista que tínhamos era que a performance do cluster inteiro estava abaixo do normal. Mas, exceto essas 
duas máquinas, nada alarmante.

Chegamos ao ponto em que esgotamos todas as fontes de problemas e mesmo assim as duas máquinas continuavam estranhas.

Resolvemos partir em busca de mais dados e verificar como estavam as máquinas físicas onde essas duas máquinas virtuais 
rodavam.

Para nossa surpresa, ambas estavam na mesma máquina física. E mais surpreendente ainda, a nossa máquina que roda o 
[Jenkins][1] para [Integração Contínua][2] também estava na mesma máquina física.

Enfim, desligando a integração contínua, o load voltava ao normal. Voltando a habilitar ela, as máquinas 
voltavam a apresentar problemas.

Moral da história, mantenha seu ambiente de produção isolado (de preferência fisicamente) do seu amabiente de testes e 
desenvolvimento.

[1]: http://jenkins-ci.org/
[2]: http://en.wikipedia.org/wiki/Continuous_integration
