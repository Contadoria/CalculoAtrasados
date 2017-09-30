---
title: Atualizacao
category: Entrada
order: 1
---

##### **CriterioCorrecao** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesCorrecao!A:A
~~~

> Seleciona o critério de atualização adotado pelo Magistrado.

* * *

##### **CriterioJuros** `D10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesJuros!A:A
~~~

> Seleciona o critério de apuração dos juros de mora adotado pelo Magistrado.

* * *

##### **CriterioReajuste** `D5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesReajuste!A:A
~~~

> Seleciona a base de cálculo inicial para incidência dos reajustes da renda mensal do benefício.

* * *

##### **DataAtualizacao** `D11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
d/m/yyyy
~~~


~~~
DATE_IS_VALID_DATE 
~~~

> Indica a data de atualização do cálculo.

* * *

##### **HonorariosContratuaisBaseJuros** `I14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosContratuaisBaseJurosModificada);HonorariosContratuaisBaseJurosModificada;SUMIFS(TotalJuros;Competencia;"<"&EOMONTH(HonorariosContratuaisDataApuracao;-1)+1)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Base de cálculo formada pela soma dos juros de mora para apuração dos honorários contratuais. 
A função "FIMMÊS(HonorariosContratuaisDataApuração;-1)" permite apurar valores até o último dia do mês anterior a data da apuração. 

* * *

##### **HonorariosContratuaisBaseJurosModificada** `J14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Indica valor diverso do total apurado como base de juros, inserido manualmente.

* * *

##### **HonorariosContratuaisBasePrincipal** `I13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosContratuaisBasePrincipalModificada);HonorariosContratuaisBasePrincipalModificada;SUMIFS(PrincipalTotalAtualizado;Competencia;"<"&EOMONTH(HonorariosContratuaisDataApuracao;-1)+1)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Base de cálculo formada pela soma dos valores principais para apuração dos honorários contratuais. 
A função "FIMMÊS(HonorariosContratuaisDataApuração;-1)" permite apurar valores até o último dia do mês anterior à data da apuração. 


* * *

##### **HonorariosContratuaisBasePrincipalModificada** `J13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Indica valor diverso do total apurado como base do principal, inserido manualmente.

* * *

##### **HonorariosContratuaisDataApuracao** `I12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosContratuaisDataApuracaoModificada);HonorariosContratuaisDataApuracaoModificada;DataAtualizacao){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Indica a data de apuração dos honorários contratuais, caso não haja modificadores assume a data da atualização do cálculo.

* * *

##### **HonorariosContratuaisDataApuracaoModificada** `J12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


~~~
DATE_IS_VALID_DATE 
~~~

> Indica data diversa da atualização do cálculo para apuração dos honorários contratuais, inserida manualmente.

* * *

##### **HonorariosContratuaisLimite** `I15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosContratuaisLimiteModificado);HonorariosContratuaisLimiteModificado;0){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Assume limite de honorários contratuais quando indicado no campo modificadores

* * *

##### **HonorariosContratuaisLimiteModificado** `J15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Indica teto fixado como limite de honorários contratuais, inserido manualmente.

* * *

##### **HonorariosContratuaisPercentual** `I11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosContratuaisPercentualModificado);HonorariosContratuaisPercentualModificado;0){% endhighlight %}


~~~
0.00%;(0.00%)[Red];-
~~~


> Assume o percentual a ser aplicado na apuração dos honorários contratuais, quando indicado no campo modificadores


* * *

##### **HonorariosContratuaisPercentualModificado** `J11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Inserir manualmente o percentual a ser aplicado na apuração dos honorários contratuais.

* * *

##### **HonorariosSucumbenciaisBaseIncidencia** `I7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosSucumbenciaisBaseIncidenciaModificada);HonorariosSucumbenciaisBaseIncidenciaModificada;SUMIFS(TotalMes;Competencia;"<"&EOMONTH(HonorariosSucumbenciaisDataApuracao;-1)+1)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Somatória dos totais (principal atualizado + juros de mora) apurados por mês de competência.
A função "FIMMÊS(HonorariosSucumbenciaisDataApuração;-1)" permite apurar valores até o último dia do mês anterior à data da apuração. 


* * *

##### **HonorariosSucumbenciaisBaseIncidenciaModificada** `J7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Indica valor diverso do total apurado como base de incidência, inserido manualmente.

* * *

##### **HonorariosSucumbenciaisDataApuracao** `I6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosSucumbenciaisDataApuracaoModificada);HonorariosSucumbenciaisDataApuracaoModificada;DataAtualizacao){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Indica a data de apuração dos honorários sucumbenciais, caso não haja modificadores assume a data da atualização do cálculo.

* * *

##### **HonorariosSucumbenciaisDataApuracaoModificada** `J6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


~~~
DATE_IS_VALID_DATE 
~~~

> Indica data diversa da atualização do cálculo para apuração dos honorários sucumbenciais, inserida manualmente.

* * *

##### **HonorariosSucumbenciaisLimite** `I8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosSucumbenciaisLimiteModificado);HonorariosSucumbenciaisLimiteModificado;0){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Assume limite de honorários sucumbenciais quando indicado no campo modificadores

* * *

##### **HonorariosSucumbenciaisLimiteModificado** `J8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Indica teto fixado como limite de honorários sucumbenciais, inserido manualmente.

* * *

##### **HonorariosSucumbenciaisPercentual** `I5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(HonorariosSucumbenciaisPercentualModificado);HonorariosSucumbenciaisPercentualModificado;0){% endhighlight %}


~~~
0.00%;(0.00%)[Red];-
~~~


> Assume o percentual a ser aplicado na apuração dos honorários sucumbenciais, quando indicado no campo modificadores

* * *

##### **HonorariosSucumbenciaisPercentualModificado** `J5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Inserir manualmente o percentual a ser aplicado na apuração dos honorários sucumbenciais.

* * *

##### **IndiceTeto** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Indica o índice de limitação ao teto do salário de benefício, a ser reposto no termo da Lei nº 8.870/94 ou Lei nº 8.880/94.