---
layout: post
title: -XX:+UseCompressedOops
permalink: /use-compressed-oops.html
category: flags
---

A JVM da Oracle, em um ambiente 64bits, utiliza 8 bytes para manter as referências (ou ponteiros). Isso é ótimo, 
pois assim podemos alocar mais de 4gb de memória.

O problema disso é que 8 bytes para um ponteiro pode começar a ficar pesado caso sua aplicação mantenha alguns
milhões de referências para objetos pequenos, em especial quando eles são formados por outros pequenos objetos
(ou seja, qualquer coisa que não seja um primitivo).

Para casos como esse, existe a flag `-XX:+UseCompressedOops`, que força a JVM a usar, enquanto for possível, 32 bits
para armazenar as referências e você continua podendo alocar mais de 4gb de memória.

Uma das aplicações em que usei essa flag simplesmente não subia sem ela, porque o consumo de memória subia cerca de 30%.
