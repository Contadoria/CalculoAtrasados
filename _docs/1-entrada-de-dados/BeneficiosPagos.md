---
title: BeneficiosPagos
category: Entrada
order: 4
---

##### **BeneficioRevisado** `H14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(MID(NaturezaAcao;1;1)="2";IF(AND(ISNUMBER(DIBBeneficioRevisado);ISNUMBER(RMIBeneficioRevisado);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBBeneficioRevisado;RMIBeneficioRevisado;DCBBeneficioRevisado;RMIBeneficioRevisadoDerivado;DCBBeneficioRevisadoDerivado;IndiceTetoBeneficioRevisado;EquivalenciaBeneficioRevisado;CalcularAbonoBeneficioRevisado<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)});{""\"";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **CalcularAbonoBeneficioRevisado** `I13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio1** `O13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio10** `AP13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio2** `R13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio3** `U13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio4** `X13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio5** `AA13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio6** `AD13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio7** `AG13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio8** `AJ13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio9** `AM13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoTutela** `L13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **DCBBeneficioRevisado** `I6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBBeneficioRevisadoDerivado** `I9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBDerivadoTutela** `L9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio1** `O6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio10** `AP6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio2** `R6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio3** `U6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio4** `X6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio5** `AA6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/mm/yyyy
~~~




* * *

##### **DCBOutroBeneficio6** `AD6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio7** `AG6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio8** `AJ6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio9** `AM6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado1** `O9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado10** `AP9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado2** `R9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado3** `U9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado4** `X9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado5** `AA9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado6** `AD9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado7** `AG9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado8** `AJ9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado9** `AM9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBTutela** `L6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBBeneficioRevisado** `I3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio1** `O3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio10** `AP3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio2** `R3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio3** `U3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio4** `X3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio5** `AA3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio6** `AD3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio7** `AG3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio8** `AJ3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio9** `AM3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBTutela** `L3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIPTutela** `L5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **EquivalenciaBeneficioRevisado** `I12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio1** `O12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio10** `AP12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio2** `R12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio3** `U12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio4** `X12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio5** `AA12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio6** `AD12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio7** `AG12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio8** `AJ12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio9** `AM12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaTutela** `L12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **IndiceTetoBeneficioRevisado** `I11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio1** `O11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio10** `AP11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio2** `R11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio3** `U11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio4** `X11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio5** `AA11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio6** `AD11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio7** `AG11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio8** `AJ11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio9** `AM11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoTutela** `L11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **OutroBeneficioPago1** `N14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio1);ISNUMBER(RMIOutroBeneficio1);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio1;RMIOutroBeneficio1;DCBOutroBeneficio1;RMIOutroBeneficioDerivado1;DCBOutroBeneficioDerivado1;IndiceTetoOutroBeneficio1;EquivalenciaOutroBeneficio1;CalcularAbonoOutroBeneficio1<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago10** `AO14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio10);ISNUMBER(RMIOutroBeneficio10);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio10;RMIOutroBeneficio10;DCBOutroBeneficio10;RMIOutroBeneficioDerivado10;DCBOutroBeneficioDerivado10;IndiceTetoOutroBeneficio10;EquivalenciaOutroBeneficio10;CalcularAbonoOutroBeneficio10<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago2** `Q14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio2);ISNUMBER(RMIOutroBeneficio2);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio2;RMIOutroBeneficio2;DCBOutroBeneficio2;RMIOutroBeneficioDerivado2;DCBOutroBeneficioDerivado2;IndiceTetoOutroBeneficio2;EquivalenciaOutroBeneficio2;CalcularAbonoOutroBeneficio2<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago3** `T14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio3);ISNUMBER(RMIOutroBeneficio3);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio3;RMIOutroBeneficio3;DCBOutroBeneficio3;RMIOutroBeneficioDerivado3;DCBOutroBeneficioDerivado3;IndiceTetoOutroBeneficio3;EquivalenciaOutroBeneficio3;CalcularAbonoOutroBeneficio3<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago4** `W14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio4);ISNUMBER(RMIOutroBeneficio4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio4;RMIOutroBeneficio4;DCBOutroBeneficio4;RMIOutroBeneficioDerivado4;DCBOutroBeneficioDerivado4;IndiceTetoOutroBeneficio4;EquivalenciaOutroBeneficio4;CalcularAbonoOutroBeneficio4<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago5** `Z14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio5);ISNUMBER(RMIOutroBeneficio5);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio5;RMIOutroBeneficio5;DCBOutroBeneficio5;RMIOutroBeneficioDerivado5;DCBOutroBeneficioDerivado5;IndiceTetoOutroBeneficio5;EquivalenciaOutroBeneficio5;CalcularAbonoOutroBeneficio5<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago6** `AC14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio6);ISNUMBER(RMIOutroBeneficio6);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio6;RMIOutroBeneficio6;DCBOutroBeneficio6;RMIOutroBeneficioDerivado6;DCBOutroBeneficioDerivado6;IndiceTetoOutroBeneficio6;EquivalenciaOutroBeneficio6;CalcularAbonoOutroBeneficio6<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago7** `AF14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio7);ISNUMBER(RMIOutroBeneficio7);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio7;RMIOutroBeneficio7;DCBOutroBeneficio7;RMIOutroBeneficioDerivado7;DCBOutroBeneficioDerivado7;IndiceTetoOutroBeneficio7;EquivalenciaOutroBeneficio7;CalcularAbonoOutroBeneficio7<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago8** `AI14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio8);ISNUMBER(RMIOutroBeneficio8);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio8;RMIOutroBeneficio8;DCBOutroBeneficio8;RMIOutroBeneficioDerivado8;DCBOutroBeneficioDerivado8;IndiceTetoOutroBeneficio8;EquivalenciaOutroBeneficio8;CalcularAbonoOutroBeneficio8<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago9** `AL14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(DIBOutroBeneficio9);ISNUMBER(RMIOutroBeneficio9);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOutroBeneficio9;RMIOutroBeneficio9;DCBOutroBeneficio9;RMIOutroBeneficioDerivado9;DCBOutroBeneficioDerivado9;IndiceTetoOutroBeneficio9;EquivalenciaOutroBeneficio9;CalcularAbonoOutroBeneficio9<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIBeneficioRevisado** `I4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIBeneficioRevisadoDerivado** `I8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIDerivadoTutela** `L8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio1** `O4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio10** `AP4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio2** `R4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio3** `U4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio4** `X4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio5** `AA4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio6** `AD4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio7** `AG4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio8** `AJ4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio9** `AM4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado1** `O8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado10** `AP8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado2** `R8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado3** `U8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado4** `X8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado5** `AA8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado6** `AD8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado7** `AG8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado8** `AJ8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado9** `AM8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMITutela** `L4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TutelaAntecipada** `K14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(L3);ISNUMBER(RMITutela);ISNUMBER(DIBTutela);ISNUMBER(DIPTutela);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";(jef_CALCULAR_RMA_COM_EVOLUCAO(DIBTutela;RMITutela;DCBTutela;RMIDerivadoTutela;DCBDerivadoTutela;IndiceTetoTutela;EquivalenciaTutela;CalcularAbonoTutela<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))*IF(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1)>=(EOMONTH(DIPTutela;-1)+1);1;0)-IF(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1)>=(EOMONTH(DIPTutela;-1)+1);OFFSET(H15:I15;0;0;COUNTA(CompetenciaIndices)-1);0))*{IF(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1)=(EOMONTH(DIPTutela;-1)+1);IF(EOMONTH(DIBTutela;0)=EOMONTH(DIPTutela;0);1;MAX(1;30-(DAY(L5)-1))/30);1)\SIGN(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1))}};{"Obrigatório:"\"DIB, RMI e DIP";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})

){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


