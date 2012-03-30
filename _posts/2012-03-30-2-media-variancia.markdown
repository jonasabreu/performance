---
layout: post
title: Médias são inúteis sem o desvio padrão
permalink: /medias-inuteis-sem-desvio-padrao.html
category: conceitos
---

<a href="http://www.smbc-comics.com/index.php?db=comics&id=2560">
<img src="http://www.smbc-comics.com/comics/20120325.gif"></a>

Essa tirinha do [Zack Weiner][1] resume bem o que tenho para dizer.

Não importa quão boa seja a sua média. Você precisa ter um [desvio padrão][2] pequeno. Pensem no seguinte caso:

Para uma determinada página, você recebe 10 requisições que são processadas em 100 ms e outras 5 que são 
processadas em 1000 ms. Sua média é 400ms o que parece muito bom, mas o seu desvio padrão é de quase 440ms.

Esses 5 (33%) usuários que tiveram que esperar 1 segundo para sua página carregar não vão ficar muito felizes.

Então você precisa otimizar também o seu desvio padrão. 

Isso não quer dizer que você não deve otimizar a sua média. Apenas que otimizar apenas ela não vai te ajudar muito.


[1]: http://www.smbc-comics.com/
[2]: http://en.wikipedia.org/wiki/Standard_deviation
