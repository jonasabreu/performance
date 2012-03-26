---
layout: post
title: HashMap consumindo 100% de CPU
permalink: /hashmap-100-cpu.html
category: concorrencia
---

Uma vez enfrentei um caso estranho. O cluster subia normalmente e as primeiras horas nada de estranho aparecia.
Depois de umas 3 ou 4 horas, um dos cores da máquina ficava em 100% e não descia mais. Passadas mais algumas horas,
outro core ficava em 100% e também não descia. Isso se repetia até a máquina não ser mais capaz de responder, 
momento em que o "watch dog" notava que tinha algo muito sério acontecendo, matava a aplicação e reiniciava.

Esse é um problema clássico relacionado à programação concorrente. Em algum momento surgia uma interação estranha
que causava um loop infinito.

Depois de rastrear bastante, descobrimos que o culpado era uma cache que utilizava um `java.util.HashMap` para armazenar
os dados.

Em diversos casos isso não seria problemático, mesmo o `HashMap` não sendo thread-safe. O problema é que essa cache
era preenchida de forma lazy e um `HashMap.put` pode causar problemas em um ambiente concorrente.

Segundo a documentação do `HashMap`, ele pode ser compartilhado entre diversas threads desde que sejam chamados apenas
métodos que não alterem sua estrutura. O `put` muda sua estrutura. E as vezes pode gerar uma condição de corrida que
causa um loop infinito.

Mudar para `java.util.concurrent.ConcurrentHashMap` resolveu o problema.
