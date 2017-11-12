---
title: BeneficiosPagos
category: Entrada
order: 3
---

##### **BeneficioRevisado** `H14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(MID(NaturezaAcao;1;1)="2";IF(AND(ISNUMBER(I3);ISNUMBER(I4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(I3;I4;I6;I8;I9;I11;I12;I13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)});{""\"";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


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

##### **CalcularAbonoOutroBeneficio1** `L13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio2** `O13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio3** `R13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio4** `U13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **CalcularAbonoOutroBeneficio5** `X13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


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

##### **DCBOutroBeneficio1** `L6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio2** `O6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio3** `R6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio4** `U6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficio5** `X6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado1** `L9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado2** `O9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado3** `R9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado4** `U9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DCBOutroBeneficioDerivado5** `X9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBBeneficioRevisado** `I3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio1** `L3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio2** `O3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio3** `R3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio4** `U3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DIBOutroBeneficio5** `X3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **EquivalenciaBeneficioRevisado** `I12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio1** `L12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio2** `O12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio3** `R12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio4** `U12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **EquivalenciaOutroBeneficio5** `X12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **IndiceTetoBeneficioRevisado** `I11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio1** `L11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio2** `O11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio3** `R11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio4** `U11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **IndiceTetoOutroBeneficio5** `X11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.0000
~~~




* * *

##### **OutroBeneficioPago1** `N14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(O3);ISNUMBER(O4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(O3;O4;O6;O8;O9;O11;O12;O13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago10** `AO14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(AP3);ISNUMBER(AP4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(AP3;AP4;AP6;AP8;AP9;AP11;AP12;AP13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago2** `Q14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(R3);ISNUMBER(R4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(R3;R4;R6;R8;R9;R11;R12;R13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago3** `T14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(U3);ISNUMBER(U4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(U3;U4;U6;U8;U9;U11;U12;U13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago4** `W14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(X3);ISNUMBER(X4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(X3;X4;X6;X8;X9;X11;X12;X13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago5** `Z14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(AA3);ISNUMBER(AA4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(AA3;AA4;AA6;AA8;AA9;AA11;AA12;AA13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago6** `AC14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(AD3);ISNUMBER(AD4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(AD3;AD4;AD6;AD8;AD9;AD11;AD12;AD13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago7** `AF14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(AG3);ISNUMBER(AG4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(AG3;AG4;AG6;AG8;AG9;AG11;AG12;AG13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago8** `AI14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(AJ3);ISNUMBER(AJ4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(AJ3;AJ4;AJ6;AJ8;AJ9;AJ11;AJ12;AJ13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **OutroBeneficioPago9** `AL14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(AM3);ISNUMBER(AM4);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";jef_CALCULAR_RMA_COM_EVOLUCAO(AM3;AM4;AM6;AM8;AM9;AM11;AM12;AM13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))};{"Obrigatório:"\"DIB e RMI";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})){% endhighlight %}


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

##### **RMIOutroBeneficio1** `L4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio2** `O4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio3** `R4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio4** `U4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficio5** `X4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado1** `L8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado2** `O8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado3** `R8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado4** `U8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMIOutroBeneficioDerivado5** `X8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TutelaAntecipada** `K14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(AND(ISNUMBER(L3);ISNUMBER(L4);ISNUMBER(L5);ISNUMBER(DataAtualizacao));{"Renda"\"Abono";(jef_CALCULAR_RMA_COM_EVOLUCAO(L3;L4;L6;L8;L9;L11;L12;L13<>"Não";DataAtualizacao;OFFSET(A15:F15;0;0;COUNTA(CompetenciaIndices)-1))*IF(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1)>=(EOMONTH(L5;-1)+1);1;0)-IF(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1)>=(EOMONTH(L5;-1)+1);OFFSET(H15:I15;0;0;COUNTA(CompetenciaIndices)-1);0))*{IF(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1)=(EOMONTH(L5;-1)+1);IF(EOMONTH(L3;0)=EOMONTH(L5;0);1;MAX(1;30-(DAY(L5)-1))/30);1)\SIGN(OFFSET(A15;0;0;COUNTA(CompetenciaIndices)-1))}};{"Obrigatório:"\"DIB, RMI e DIP";(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)\(OFFSET(CompetenciaIndices;1;0;COUNTA(CompetenciaIndices)-1)*0)})

){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


