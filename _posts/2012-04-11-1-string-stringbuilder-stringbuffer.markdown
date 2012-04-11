---
layout: post
title: String X StringBuilder X StringBuffer
permalink: /string-string-builder-string-buffer.html
category: pitfalls
---

Caso bem comum que muita gente ainda discute. Devo usar [String][1], [StringBuilder][2] ou [StringBuffer][3]?

Só para lembrar:

* String é uma String imutável (consequentemente é thread-safe)
* StringBuilder é uma String mutável
* StringBuffer é uma String mutável thread-safe

Qual devo usar quando estiver programando? String.

A maior parte do tempo não faz a menor diferença qual você usa. E é bem mais legível `"a" + "b"` 
que `new StringBuilder("a").append("b")`.

Ah, mas o StringBuffer usa `synchronized`, então vai ser mais lento. Também não. [Escape Analysis][4] 
resolve esse problema, removendo o controle de lock se o StringBuffer for usado por apenas uma thread.

[1]: http://docs.oracle.com/javase/6/docs/api/java/lang/String.html
[2]: http://docs.oracle.com/javase/1.5.0/docs/api/java/lang/StringBuilder.html
[3]: http://docs.oracle.com/javase/1.5.0/docs/api/java/lang/StringBuffer.html
[4]: http://en.wikipedia.org/wiki/Escape_analysis
