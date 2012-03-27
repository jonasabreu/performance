---
layout: post
title: String.replaceAll(regex, content)
permalink: /string-replace-all-lento.html
category: pitfalls
---

Certa vez me deparei com o seguinte código:

	String temp;
	temp = entrada;

	temp = temp.replaceAll("[àãáâåäª]", "a");
	temp = temp.replaceAll("[ÀÃÁÂÅÄ]", "A");
	temp = temp.replaceAll("[èéêë]", "e");
	temp = temp.replaceAll("[ÈÉÊË]", "E");
	temp = temp.replaceAll("[íìîï]", "i");
	temp = temp.replaceAll("[ÌÍÎÏ]", "I");
	temp = temp.replaceAll("[òõóôøöº]", "o");
	temp = temp.replaceAll("[ÒÕÓÔØÖ]", "O");
	temp = temp.replaceAll("[ùúûüµ]", "u");
	temp = temp.replaceAll("[ÙÚÛÜ]", "U");
	temp = temp.replaceAll("æ", "ae");
	temp = temp.replaceAll("Æ", "Ae");
	temp = temp.replaceAll("ß", "ss");
	temp = temp.replaceAll("[ç¢]", "c");
	temp = temp.replaceAll("Ç", "C");
	temp = temp.replaceAll("Ð", "D");
	temp = temp.replaceAll("ð", "d");
	temp = temp.replaceAll("ñ", "n");
	temp = temp.replaceAll("Ñ", "N");
	temp = temp.replaceAll("Þ", "P");
	temp = temp.replaceAll("þ", "p");
	temp = temp.replaceAll("[ÿý]", "y");
	temp = temp.replaceAll("Ý", "Y");
	temp = temp.replaceAll("¹", "1");
	temp = temp.replaceAll("²", "2");
	temp = temp.replaceAll("³", "3");

O objetivo era trocar caracteres especiais para caracteres simples. O problema é que a chamada para esse método apareceu no profiler, 
porque o método era chamado algumas centenas de vezes por requisição.

RegEx em java costuma ser rápido o suficiente para não aparecer no profiler. Nesse caso específico o problema é que a cada chamada ao 
replaceAll a RegEx (primeiro parâmetro) é recompilada (processo que costuma ser um pouco mais caro). 

Temos 25 compilações vezes algumas centenas de vezes por requisição. Isso começa a consumir um tempo considerável.

Minha solução foi trocar isso para um switch bem feio mesmo, mas que rodava na metade do tempo.
