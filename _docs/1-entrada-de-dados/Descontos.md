---
title: Descontos
category: Entrada
order: 4
---

##### **CompetenciaDescontos** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Competência";CompetenciaIndices)){% endhighlight %}


~~~
mm/yyyy
~~~


> Matriz correspondente aos meses em que poderão ser efetuados descontados valores

* * *

##### **DescontosBeneficioRevisadoAbono** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~




* * *

##### **DescontosBeneficioRevisadoRenda** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=OFFSET(BeneficioRevisado;0;0;COUNTA(CompetenciaIndices);2){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **DescontosConsignacao** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Percentual da renda mensal a ser deduzido (consignação)

* * *

##### **DescontosNB1** `O4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB1Abono** `P:P`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB1Renda** `O:O`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB2** `Q4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB2Abono** `R:R`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB2Renda** `Q:Q`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB3** `S4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB3Abono** `T:T`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB3Renda** `S:S`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB4** `U4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB4Abono** `V:V`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB4Renda** `U:U`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosNB5** `W4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Número de benefício pago inacumulável

* * *

##### **DescontosNB5Abono** `X:X`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Abono recebido por benefício inacumulável

* * *

##### **DescontosNB5Renda** `W:W`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Número de benefício pago inacumulável
Renda mensal recebida por benefício inacumulável

* * *

##### **DescontosOutrosAbonoPercentual** `L:L`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
0.###############
~~~


> Percentual do abono a ser deduzido (outros descontos)

* * *

##### **DescontosOutrosAbonoValor** `M:M`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Valor do abono a ser descontado (outros descontos)

* * *

##### **DescontosOutrosBeneficiosAbono** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~




* * *

##### **DescontosOutrosBeneficiosRenda** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}={"Renda"\"Abono";ARRAYFORMULA(OFFSET(OutroBeneficioPago1;1;0;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago2;1;0;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago3;1;0;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago4;1;0;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago5;1;0;COUNTA(CompetenciaIndices)-1;1))\ARRAYFORMULA(OFFSET(OutroBeneficioPago1;1;1;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago2;1;1;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago3;1;1;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago4;1;1;COUNTA(CompetenciaIndices)-1;1)+OFFSET(OutroBeneficioPago5;1;1;COUNTA(CompetenciaIndices)-1;1))}{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **DescontosOutrosObservacoes** `N:N`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%;(0.00%)[Red];-
0.###############
#,##0.00;(#,##0.00)[Red];-
~~~


> Identificação dos descontos efetuados (outros descontos)

* * *

##### **DescontosOutrosRendaPercentual** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Percentual da renda mensal a ser deduzido (outros descontos)

* * *

##### **DescontosOutrosRendaValor** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Valor da renda mensal a ser descontado (outros descontos)

* * *

##### **DescontosRendaExcluida** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Percentual da renda mensal a ser deduzido

* * *

##### **DescontosTotalAbonoPercentual** `AB:AB`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Perc. Abono";OFFSET(DescontosOutrosAbonoPercentual;4;0;ROWS(CompetenciaIndices))+0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Percentual total a ser deduzido do abono

* * *

##### **DescontosTotalAbonoValor** `Z:Z`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Valor Abono";OFFSET(DescontosNB1Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB2Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB3Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB4Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB5Abono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosBeneficioRevisadoAbono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosBeneficiosAbono;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosAbonoValor;4;0;ROWS(CompetenciaIndices)))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Somatória dos valores a serem descontados do abono

* * *

##### **DescontosTotalRendaPercentual** `AA:AA`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Perc. Renda";OFFSET(DescontosRendaExcluida;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosConsignacao;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosRendaPercentual;4;0;ROWS(CompetenciaIndices)))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Percentual total a ser deduzido da renda

* * *

##### **DescontosTotalRendaValor** `Y:Y`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Valor Renda";OFFSET(DescontosNB1Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB2Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB3Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB4Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosNB5Renda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosBeneficioRevisadoRenda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosBeneficiosRenda;4;0;ROWS(CompetenciaIndices))+OFFSET(DescontosOutrosRendaValor;4;0;ROWS(CompetenciaIndices)))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.###############
~~~


> Somatória dos valores a serem descontados da renda