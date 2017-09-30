---
title: Descontos
category: Entrada
order: 5
---

##### **CompetenciaDescontos** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Competência";CompetenciaIndices)){% endhighlight %}


~~~
mm/yyyy
~~~


> Matriz correspondente aos meses em que poderão ser efetuados descontados valores

* * *

##### **DescontosBeneficioPagoAbono** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Abono";IF(ROW(CompetenciaIndices)<MATCH(CompetenciaInicial;CompetenciaIndices;0);0;IF(ROW(CompetenciaIndices)>MATCH(CompetenciaFinal;CompetenciaIndices;0);0;IF(MID(NaturezaAcao;1;1)="2";IFERROR(VLOOKUP(OFFSET(CompetenciaDescontos;4;0);OFFSET(Competencia;0;0;ROWS(Competencia);COLUMN(AbonoNBPago));COLUMN(AbonoNBPago);TRUE);0);0))))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~




* * *

##### **DescontosBeneficioPagoRenda** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Renda";IF(ROW(CompetenciaIndices)<MATCH(CompetenciaInicial;CompetenciaIndices;0);0;IF(ROW(CompetenciaIndices)>MATCH(CompetenciaFinal;CompetenciaIndices;0);0;IF(MID(NaturezaAcao;1;1)="2";IFERROR(VLOOKUP(OFFSET(CompetenciaDescontos;4;0);OFFSET(Competencia;0;0;ROWS(Competencia);COLUMN(ValorQuotaNBPago));COLUMN(ValorQuotaNBPago);TRUE);0);0))))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **DescontosConsignacao** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Percentual da renda mensal a ser deduzido (consignação)

* * *

##### **DescontosNB1** `M4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB1Abono** `N:N`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB1Renda** `M:M`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB2** `O4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB2Abono** `P:P`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB2Renda** `O:O`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB3** `Q4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB3Abono** `R:R`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB3Renda** `Q:Q`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB4** `S4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB4Abono** `T:T`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB4Renda** `S:S`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB5** `U4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB5Abono** `V:V`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB5Renda** `U:U`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosOutrosAbonoPercentual** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
0.###############
~~~


> Percentual do abono a ser deduzido (outros descontos)

* * *

##### **DescontosOutrosAbonoValor** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Valor do abono a ser descontado (outros descontos)

* * *

##### **DescontosOutrosObservacoes** `L:L`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%;(0.00%)[Red];-
0.###############
#,##0.00;(#,##0.00)[Red];-
~~~


> Identificação dos descontos efetuados (outros descontos)

* * *

##### **DescontosOutrosRendaPercentual** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Percentual da renda mensal a ser deduzido (outros descontos)

* * *

##### **DescontosOutrosRendaValor** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Valor da renda mensal a ser descontado (outros descontos)

* * *

##### **DescontosRendaExcluida** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Percentual da renda mensal a ser deduzido

* * *

##### **DescontosTotalAbonoPercentual** `Z:Z`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Perc. Abono";OFFSET(DescontosOutrosAbonoPercentual;4;0;ROWS(CompetenciaIndices))+0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Percentual total a ser deduzido do abono

* * *

##### **DescontosTotalAbonoValor** `X:X`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Valor Abono";OFFSET(DescontosNB1Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB2Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB3Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB4Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB5Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosBeneficioPagoAbono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosAbonoValor;4;0;ROWS(CompetenciaIndices)))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Somatória dos valores a serem descontados do abono

* * *

##### **DescontosTotalRendaPercentual** `Y:Y`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Perc. Renda";OFFSET(DescontosRendaExcluida;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosConsignacao;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosRendaPercentual;4;0;ROWS(CompetenciaIndices)))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Percentual total a ser deduzido da renda

* * *

##### **DescontosTotalRendaValor** `W:W`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Valor Renda";OFFSET(DescontosNB1Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB2Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB3Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB4Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB5Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosBeneficioPagoRenda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosRendaValor;4;0;ROWS(CompetenciaIndices)))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Somatória dos valores a serem descontados da renda