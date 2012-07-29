---
layout: post
title: Deixe seus XPaths mais rápidos
permalink: /xpath-mais-rapido.html
category: pitfalls
---

Recentemente tive novamente problemas com performance de [XPaths][1]. Basicamente, processamento de XPaths era responsável
por 25% do tempo da requisição.

Procurando sobre como [melhorar a performance de XPaths][2], encontrei uma pergunta muito interessante no 
[StackOverflow][7].

Basicamente [existe um bug][5] na implementação da [JAXP][3] da [Apache][4], que é a que usamos nessa aplicação (e que 
parece ser a [implementação distribuída com a JDK][6])

Para contornar esse bug, basta adicionar uma das seguintes flags (dependendo se você usa a implementação padrão ou 
um jar do Xalan):

	-Dorg.apache.xml.dtm.DTMManager=org.apache.xml.dtm.ref.DTMManagerDefault

ou

	-Dcom.sun.org.apache.xml.internal.dtm.DTMManager=com.sun.org.apache.xml.internal.dtm.ref.DTMManagerDefault

Em um benchmark muito ruim, apenas para verificar rapidamente se existia alguma diferença, obtive um tempo de processamento
50% menor que sem a flag.

Em produção, depois de colocarmos a flag, notamos uma redução de 40% do tempo de processamento de XPath, o que resultou em
uma melhoria perto de 10%. Nada mal para quase nenhum trabalho.


[1]: http://en.wikipedia.org/wiki/XPath
[2]: http://stackoverflow.com/questions/6340802/java-xpath-apache-jaxp-implementation-performance
[3]: http://en.wikipedia.org/wiki/Java_API_for_XML_Processing
[4]: http://xml.apache.org/xalan-j/
[5]: https://issues.apache.org/jira/browse/XALANJ-2540
[6]: http://jaxp.java.net/1.4/JAXP-FAQ.html
[7]: http://stackoverflow.com/
