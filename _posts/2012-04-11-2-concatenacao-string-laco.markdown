---
layout: post
title: Concatenação de Strings em Laços
permalink: /concatenacao-string-laco.html
category: pitfalls
---

No post sobre [String, StringBuffer e StringBuilder][1], comentei que em geral não faz diferença você usar
qualquer um deles. 

Conheço um caso em que isso pode não ser verdade.

Vejam o seguinte código inocente:

	String a = "";
	for (int i = 0; i < 100000; i++) {
		a += "a";
	}


E comparem com a versão que usa StringBuider:

	StringBuilder a = new StringBuilder("");
	for (int i = 0; i < 100000; i++) {
		a.append("a");
	}

Na minha máquina, q primeira demora `28595ms` para rodar, enquanto que a segunda roda em `27ms`. Uma diferença 
de mais de 1000 vezes.

Olhando o bytecode do primeiro exemplo, entendemos o problema.

	 0:	ldc	#25; //String 
	 2:	astore_1
	 3:	iconst_0
	 4:	istore_2
	 5:	goto	31
	 8:	new	#27; //class java/lang/StringBuilder
	11:	dup
	12:	aload_1
	13:	invokestatic	#29; //Method java/lang/String.valueOf:(Ljava/lang/Object;)Ljava/lang/String;
	16:	invokespecial	#35; //Method java/lang/StringBuilder."<init>":(Ljava/lang/String;)V
	19:	ldc	#38; //String a
	21:	invokevirtual	#40; //Method java/lang/StringBuilder.append:(Ljava/lang/String;)Ljava/lang/
																					StringBuilder;
	24:	invokevirtual	#44; //Method java/lang/StringBuilder.toString:()Ljava/lang/String;
	27:	astore_1
	28:	iinc	2, 1
	31:	iload_2
	32:	ldc	#48; //int 100000
	34:	if_icmplt	8
	37:	return

As linhas interessantes são as identificadas por 16, 21 e 24, que compõe parte da concatenação de strings 
dentro do laço.

A 16 é a invocação do construtor de um `StringBuilder`. Depois é chamado o método `append` e enfim é chamado o
`toString`.

Mas não existia nenhuma referência à `StringBuilder` no primeiro exemplo. Ele aparece aí porque o compilador Java,
quando encontra uma concatenação de strings, converte para um StringBuilder automaticamente.

Na maioria das vezes isso funciona bem. O problema é que nesse caso a otimização do compilador não ajudou.

Isso significa que você não vai mais concatenar strings dentro de laço sem usar `StringBuilder`? Não. Caso
apareça no seu [profiler][2] esse problema, daí sim vale a pena trocar para um `StringBuilder`.

[1]: /string-string-builder-string-buffer.html
[2]: /visual-vm.html
