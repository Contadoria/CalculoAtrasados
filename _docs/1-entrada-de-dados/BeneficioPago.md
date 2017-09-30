---
title: BeneficioPago
category: Entrada
order: 3
---

##### **CoeficienteDerivadoModificadoNBPago** `J7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Modificador referente ao coeficiente do benefício derivado pago, inserção manual

* * *

##### **CoeficienteDerivadoNBPago** `I7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(SalarioBeneficioModificadoNBPago);IF(ISNUMBER(CoeficienteDerivadoModificadoNBPago);CoeficienteDerivadoModificadoNBPago;1);1){% endhighlight %}


~~~
0.00%
~~~


> Coeficiente do benefício derivado pago

* * *

##### **CoeficienteOriginarioModificadoNBPago** `J6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente ao coeficiente do benefício originário pago, inserção manual

* * *

##### **CoeficienteOriginarioNBPago** `I6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(SalarioBeneficioModificadoNBPago);IF(ISNUMBER(CoeficienteOriginarioModificadoNBPago);CoeficienteOriginarioModificadoNBPago;1);1){% endhighlight %}


~~~
0.00%
~~~


> Coeficiente do benefício originário pago

* * *

##### **EquivalenciaArt58ModificadaNBPago** `J10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente à equivalência salarial paga para aplicação do artigo 58 do ADCT

* * *

##### **EquivalenciaArt58NBPago** `I10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(EquivalenciaArt58ModificadaNBPago);EquivalenciaArt58ModificadaNBPago;IF(ISNUMBER(RMIArt58NBPago);RMIArt58NBPago/INDEX(SalarioMinimo;MATCH(EOMONTH(DIBArt58;-1)+1;CompetenciaIndices;0));"")){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Equivalência correspondente à divisão da renda mensal inicial paga pelo valor do salário-mínimo na data de início do benefício

* * *

##### **IndiceTetoNBPago** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
DATE_IS_VALID_DATE 
~~~

> Indica o índice de limitação ao teto do salário de benefício (pago), a ser reposto no termo da Lei nº 8.870/94 ou Lei nº 8.880/94.

* * *

##### **RMDDANBPago** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)
~~~


> Valor da renda mensal inicial para evolução de benefício concedido em "DIB fictícia" (benefício pago)

* * *

##### **RMIArt58ModificadaNBPago** `J9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente à renda mensal inicial utilizada para fins de aplicação do artigo 58 do ADCT (benefício pago)

* * *

##### **RMIArt58NBPago** `I9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(RMIArt58ModificadaNBPago);RMIArt58ModificadaNBPago;IF(DIBOriginario<DATE(1988;10;5);RMIInformadaNBPago;"")){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Renda mensal inicial utilizada para fins de aplicação do artigo 58 do ADCT (benefício pago)

* * *

##### **RMIInformadaNBPago** `D5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~


> Valor da RMI informada (benefício pago)

* * *

##### **RendaInformadaModificadaNBPago** `J8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Modificador referente ao valor da RMI

* * *

##### **RendaInformadaNBPago** `I8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(RendaInformadaModificadaNBPago);RendaInformadaModificadaNBPago;IF(ISNUMBER(RMDDANBPago);RMDDANBPago;RMIInformadaNBPago)){% endhighlight %}


~~~
#,##0.00
~~~


> Valor da renda mensal inicial informada

* * *

##### **SalarioBeneficioModificadoNBPago** `J5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~


> Valor do salário-de-benefício ago informado 

* * *

##### **SalarioBeneficioNBPago** `I5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(SalarioBeneficioModificadoNBPago);SalarioBeneficioModificadoNBPago;IF(ISNUMBER(RMDDANBPago);RMDDANBPago;RMIInformadaNBPago)){% endhighlight %}


~~~
#,##0.00
~~~


> Valor do salário-de-benefício pago (deve ser informado ou corresponderá ao valor da RMI). É utilizado como base para conversões de benefícios