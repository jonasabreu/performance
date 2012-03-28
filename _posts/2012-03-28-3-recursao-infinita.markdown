---
layout: post
title: Recursão Infinita
permalink: /recursao-infinita.html
category: pitfalls
---

Certa vez, minutos após o deploy em um cluster, as máquinas começaram a parar de responder.

O que acontecia é que a cada poucos minutos, um dos cores ficava em 100% e não descia mais. 

Isso acontecia até a máquina parar de responder. Como a [VisualVM](/visual-vm.html) não conectava,
entrei na máquina e rodei o [JStack](/jstack.html).

Um trecho do stacktrace de algumas threads era semelhante à esse:

	java.lang.Thread.State: RUNNABLE
		// Vários métodos diferentes
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		at meu.pacote.ClassSuspeita.metodo(ClasseSuspeita.java:180)
		// e continuava por vários outras chamadas

Esse é o stacktrace clássico de uma [recursão][1] infinita.

Recursão é uma técnica muito interessante e que permite simplificar extremamente alguns algoritmos,
mas como usamos menos no dia a dia, eventualmente acabamos errando a condição de parada dela e
ela nunca para.

Sabendo qual era o problema, desativamos a funcionalidade e depois de corrigir a condição de parada
fizemos um novo deploy estável.

[1]: http://en.wikipedia.org/wiki/Recursion#Recursion_in_computer_science
