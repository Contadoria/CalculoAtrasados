---
title: Modificadores
category: Entrada
order: 5
---

##### **CompetenciaModificadores** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Competência";CompetenciaIndices)){% endhighlight %}


~~~
mm/yyyy
0.###############
~~~


> Matriz correspondente aos meses em que poderão ser lançados modificadores diversos

* * *

##### **ModificadoresCoeficiente** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00%;(#,##0.00%);-
0.###############
~~~


> Modificadores dos coeficientes, inserção manual

* * *

##### **ModificadoresFatorReajuste** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
0.###############
~~~


> Modificadores dos fatores mensais de reajuste do valor do benefício, inserção manual

* * *

##### **ModificadoresIndiceMensalAtualizacao** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
0.###############
~~~


> Modificadores dos índices de atualização acumulados, inserção manual

* * *

##### **ModificadoresJuros** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00%;(#,##0.00%);-
0%
~~~


> Modificadores dos índices de juros mensais, inserção manual

* * *

##### **ModificadoresObservacoes** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
0.###############
~~~


> Campo para inserção de observações

* * *

##### **ModificadoresPiso** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
00,000.00;(00,000.00)[Red];-
0.###############
~~~


> Modificadores dos pisos a serem considerados, inserção manual

* * *

##### **ModificadoresQuotaRendaMensal** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
0.###############
~~~


> Modificadores das quotas a serem consideradas, inserção manual

* * *

##### **ModificadoresTeto** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
00,000.00;(00,000.00)[Red];-
0.###############
~~~


> Modificadores dos tetos a serem considerados, inserção manual