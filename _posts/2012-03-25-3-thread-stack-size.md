---
layout: post
title: -XX:ThreadStackSize
permalink: /thread-stack-size.html
category: flags
---

Em uma aplicação que sempre tinha **muitas threads (> 3000)** e estava com problemas de memória, a solução que adotamos
para economizar um pouco de memória foi reduzir o tamanho reservado a cada thread para armazenar os frames de invocação
de métodos.

Por padrão, em um ambiente **64bits**, a JVM da Oracle aloca **1 mb** para a Thread Stack. Isso significa que nossa 
aplicação estava consumindo algo próximo a **3 gb** para as threads.

Se reduzimos o tamanho da Stack para 512 kb economizamos 1,5 gb, que era mais ou menos o que precisávamos. Depois de ver
que a aplicação se comportava bem com esse tamanho (nenhum `StackOverflow` aconteceu), resolvemos reduzir ainda mais
(para 256 kb) e mantivemos nesse tamanho, embora talvez ainda fosse possível reduzir mais.

Com essa mudança reduzimos o consumo de memória em **2,25 gb**.
