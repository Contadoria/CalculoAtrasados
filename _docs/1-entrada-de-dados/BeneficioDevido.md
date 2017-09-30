---
title: BeneficioDevido
category: Entrada
order: 2
---

##### **CoeficienteDerivado** `I9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(SBModificado);IF(ISNUMBER(CoeficienteDerivadoModificado);CoeficienteDerivadoModificado;1);1){% endhighlight %}


~~~
0.00%
~~~


> Coeficiente do benefício derivado

* * *

##### **CoeficienteDerivadoModificado** `J9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Modificador referente ao coeficiente do benefício derivado, inserção manual

* * *

##### **CoeficienteOriginario** `I8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(SBModificado);IF(ISNUMBER(CoeficienteOriginarioModificado);CoeficienteOriginarioModificado;1);1){% endhighlight %}


~~~
0.00%
~~~


> Coeficiente do benefício originário

* * *

##### **CoeficienteOriginarioModificado** `J8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Modificador referente ao coeficiente do benefício originário, inserção manual

* * *

##### **DCBDerivado** `D20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Data da cessação do benefício derivado

* * *

##### **DCBOriginario** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
d/m/yyyy
~~~


~~~
DATE_IS_VALID_DATE 
~~~



* * *

##### **DDA** `D13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


~~~
DATE_IS_VALID_DATE 
~~~

> Data do direito adquirido para evolução de benefício concedido em "DIB fictícia"

* * *

##### **DIBArt58** `I12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBArt58Modificada);DIBArt58Modificada;IF(AND(ISNUMBER(DIBDerivado);DIBDerivado<DATE(1988;10;5));DIBDerivado;IF(DIBOriginario<DATE(1988;10;5);DIBOriginario;""))){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Data de início do benefício é informada caso tenha sido concedido antes de 05/10/1988 (para efeito de aplicação do artigo 58 do ADCT)

* * *

##### **DIBArt58Modificada** `J12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Modificador referente à data de início do benefício (para efeito de aplicação do artigo 58 do ADCT)

* * *

##### **DIBDerivado** `D19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOriginario** `D7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


~~~
DATE_IS_VALID_DATE 
~~~



* * *

##### **DataFinalDiferencas** `I6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DataFinalDiferencasModificada);DataFinalDiferencasModificada;IF(DIBDerivado;IF(ISNUMBER(DCBDerivado);DCBDerivado;EOMONTH(DataAtualizacao;-1));IF(ISNUMBER(DCBOriginario);DCBOriginario;EOMONTH(DataAtualizacao;-1)))){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Data final das diferenças a serem calculadas, considerando a data de cessação de benefícios ou mês anterior à data da atualização

* * *

##### **DataFinalDiferencasModificada** `J6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Modificador referente à data final das diferenças, inserção manual

* * *

##### **DataInicioDiferencas** `I5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DataInicioDiferencasModificada);DataInicioDiferencasModificada;IF(ISNUMBER(DIBOriginario);DIBOriginario)){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Data inicial das diferenças a serem calculadas

* * *

##### **DataInicioDiferencasModificada** `J5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Modificador referente à data inicial das diferenças, inserção manual

* * *

##### **EquivalenciaArt58** `I14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(EquivalenciaArt58Modificada);EquivalenciaArt58Modificada;IF(ISNUMBER(RMIArt58);RMIArt58/INDEX(SalarioMinimo;MATCH(EOMONTH(DIBArt58;-1)+1;CompetenciaIndices;0));"")){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Equivalência correspondente à divisão da renda mensal inicial pelo valor do salário-mínimo na data de início do benefício

* * *

##### **EquivalenciaArt58Modificada** `J14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente à equivalência salarial utilizada para aplicação do artigo 58 do ADCT

* * *

##### **EspecieDerivado** `D18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!A:A
~~~

> Código referente à espécie do benefício derivado

* * *

##### **EspecieOriginario** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!A:A
~~~

> Código referente à espécie do benefício originário

* * *

##### **MarcoPrescricional** `I11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(MarcoPrescricionalModificado);MarcoPrescricionalModificado;IF(ISNUMBER(Protocolo);EDATE(Protocolo;-60);)){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Termo inicial para apuração de diferenças, considerando a prescrição quinquenal contada desde a data do ajuizamento da ação

* * *

##### **MarcoPrescricionalModificado** `J11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Modificador referente ao termo inicial para apuração da prescrição

* * *

##### **NBDerivado** `D17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Número do benefício derivado

* * *

##### **NBOriginario** `D5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Número do benefício originário

* * *

##### **RMDDA** `D14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)
~~~


> Valor da renda mensal inicial para evolução de benefício concedido em "DIB fictícia"

* * *

##### **RMIArt58** `I13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(RMIArt58Modificada);RMIArt58Modificada;IF(DIBOriginario<DATE(1988;10;5);RMIInformada;"")){% endhighlight %}


~~~
#,##0.00
~~~


> Renda mensal inicial utilizada para fins de aplicação do artigo 58 do ADCT

* * *

##### **RMIArt58Modificada** `J13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente à renda mensal inicial utilizada para fins de aplicação do artigo 58 do ADCT

* * *

##### **RMIInformada** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da RMI informada

* * *

##### **RendaInformada** `I10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(RendaInformadaModificada);RendaInformadaModificada;IF(ISNUMBER(RMDDA);RMDDA;RMIInformada)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Valor da renda mensal inicial informada

* * *

##### **RendaInformadaModificada** `J10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente ao valor da RMI

* * *

##### **SalarioBeneficio** `I7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(SalarioBeneficioModificado);SalarioBeneficioModificado;IF(ISNUMBER(RMDDA);RMDDA;RMIInformada)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Valor do salário-de-benefício (deve ser informado ou corresponderá ao valor da RMI). É utilizado como base para conversões de benefícios

* * *

##### **SalarioBeneficioModificado** `J7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor do salário-de-benefício informado