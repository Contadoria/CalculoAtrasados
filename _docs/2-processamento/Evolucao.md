---
title: Evolucao
category: Processamento
order: 0
---

##### **Abono** `AQ:AQ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Abono)=1;"Abono";IF(ROW(Abono)<=TotalCompetencias+1;RendaMensalEfetiva*ProporcaoAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores devidos calculados a título de abono

* * *

##### **AbonoNBPago** `AR:AR`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(AbonoNBPago)=1;"Abono Pago";IF(ROW(AbonoNBPago)<=TotalCompetencias+1;ValorQuotaNBPago*ProporcaoAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores devidos calculados a título de abono

* * *

##### **Coeficiente** `Z:Z`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Coeficiente)=1;"Coeficiente";IF(ROW(Coeficiente)<=TotalCompetencias+1;IF(ISNUMBER(CoeficienteModificado);CoeficienteModificado;IF(ISNUMBER(DIBDerivado);IF(Competencia>=EOMONTH(DIBDerivado;-1)+1;CoeficienteDerivado;CoeficienteOriginario);CoeficienteOriginario));""))){% endhighlight %}


~~~
0.00%
~~~


> Matriz correspondente aos coeficientes aplicados durante o período, observando os benefícios originário e derivado

* * *

##### **CoeficienteModificado** `AA:AA`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CoeficienteModificado)=1;"Modificador";IF(ROW(CoeficienteModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresCoeficiente;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}



> Modificador referente à matriz correspondente aos coeficientes aplicados durante o período

* * *

##### **CoeficienteModificadoNBPago** `AC:AC`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CoeficienteModificadoNBPago)=1;"Modificador";IF(ROW(CoeficienteModificadoNBPago)<=TotalCompetencias+1;{"";OFFSET(ModificadoresCoeficiente;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1)};""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **CoeficienteNBPago** `AB:AB`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CoeficienteNBPago)=1;"Coeficiente Pago";IF(ROW(CoeficienteNBPago)<=TotalCompetencias+1;IF(ISNUMBER(CoeficienteModificadoNBPago);CoeficienteModificadoNBPago;IF(ISNUMBER(DIBDerivado);IF(Competencia>=EOMONTH(DIBDerivado;-1)+1;CoeficienteDerivadoNBPago;CoeficienteOriginarioNBPago);CoeficienteOriginarioNBPago));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
0.00%
~~~


> Matriz correspondente aos coeficientes aplicados durante o período (benefícios pagos), observando os benefícios originário e derivado

* * *

##### **Competencia** `A:A`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Competencia)=1;"Competência";IF(ROW(Competencia)<=TotalCompetencias+1;EOMONTH(DIBOriginario;ROW(OFFSET(Competencia;0;0;TotalCompetencias+1))-3)+1;""))){% endhighlight %}


~~~
mm/yyyy
~~~


> Matriz ajustada com base no período de meses entre a data de início e a data final do cálculo.


* * *

##### **DescontoAbono** `AT:AT`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DescontoAbono)=1;"Desconto Abono";IF(ROW(DescontoAbono)<=TotalCompetencias+1;OFFSET(DescontosTotalAbonoValor;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+1)+(OFFSET(DescontosTotalAbonoPercentual;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+1)*OFFSET(Abono;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **DescontoRenda** `AS:AS`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DescontoRenda)=1;"Desconto Renda";IF(ROW(DescontoRenda)<=TotalCompetencias+1;OFFSET(DescontosTotalRendaValor;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+1)+(OFFSET(DescontosTotalRendaPercentual;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+1)*OFFSET(RendaMensalDevida;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **FatorAtualizacao** `BA:BA`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorAtualizacao)=1;"Fator Atualização";IF(ROW(FatorAtualizacao)<=TotalCompetencias+1;jef_INDICE_ACUMULADO(OFFSET(IndiceMensalAtualizacao;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
~~~


> Matriz correspondente aos fatores de atualização (índice acumulado)

* * *

##### **FatorAtualizacaoAlcada** `BO:BO`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorAtualizacaoAlcada)=1;"Fator Atual. Alçada";IF(ROW(FatorAtualizacaoAlcada)<=TotalCompetencias+1;IF(ROW(FatorAtualizacaoAlcada)>LinhaProtocolo-1;0;jef_INDICE_ACUMULADO(OFFSET(IndiceMensalAtualizacaoAlcada;0;0;TotalCompetencias+1)));""))){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000)[Red];-
~~~


> Matriz correspondente aos fatores de atualização até a data do ajuizamento da ação (índice acumulado)

* * *

##### **FatorReajuste** `Q:Q`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorReajuste)=1;"Fator Reajuste";IF(ROW(FatorReajuste)<=TotalCompetencias+1;IF(ISNUMBER(FatorReajusteModificado);FatorReajusteModificado;IF(Reajustar;ReajusteArt58*ReajusteLei8870*ReajusteLei8880*IndicesReajuste;1));""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz correspondente aos fatores de reajuste do benefício a serem aplicados (observando artigo 58 do ADCT, artigo 26 da Lei 8.870/94 e artigo 21, §3º da Lei 8.880/94)

* * *

##### **FatorReajusteModificado** `R:R`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorReajusteModificado)=1;"Modificador";IF(ROW(FatorReajusteModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresFatorReajuste;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}



> Modificador referente aos fatores de reajuste do benefício

* * *

##### **FatorReajusteModificadoNBPago** `T:T`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorReajusteModificadoNBPago)=1;"Modificador Pago";IF(ROW(FatorReajusteModificadoNBPago)<=TotalCompetencias+1;{"";OFFSET(ModificadoresFatorReajuste;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}





* * *

##### **FatorReajusteNBPago** `S:S`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorReajusteNBPago)=1;"Fator Reajuste Pago";IF(ROW(FatorReajusteNBPago)<=TotalCompetencias+1;IF(ISNUMBER(FatorReajusteModificadoNBPago);FatorReajusteModificadoNBPago;IF(Reajustar;ReajusteArt58NBPago*ReajusteLei8870NBPago*ReajusteLei8880NBPago*IndicesReajuste;1));""))){% endhighlight %}



> Matriz correspondente aos fatores de reajuste do benefício pago a serem aplicados

* * *

##### **IndiceMensalAtualizacao** `AX:AX`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacao)=1;"Índice";IF(ROW(IndiceMensalAtualizacao)<=TotalCompetencias+1;IF(ISNUMBER(IndiceMensalAtualizacaoModificado);IndiceMensalAtualizacaoModificado; IF(MID(CriterioCorrecao;1;1)="2";{"";OFFSET(IndiceRes134;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)};{"";OFFSET(IndiceAtualizacao;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)}));""))){% endhighlight %}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
~~~


> Matriz correspondente aos índices 
de atualização mensais conforme opção escolhida

* * *

##### **IndiceMensalAtualizacaoAjustado** `AZ:AZ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoAjustado)=1;"Índice Ajustado";IF(ROW(IndiceMensalAtualizacaoAjustado)<=TotalCompetencias+1;{"";OFFSET(AjusteMoeda;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)}*OFFSET(IndiceMensalAtualizacao;0;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
~~~


> Matriz correspondente aos índices 
de atualização mensais, considerando os ajustes de moeda

* * *

##### **IndiceMensalAtualizacaoAlcada** `BN:BN`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoAlcada)=1;"Indices Alçada";IF(ROW(IndiceMensalAtualizacaoAlcada)<=TotalCompetencias+1;IF(ROW(IndiceMensalAtualizacaoAlcada)>LinhaProtocolo-1;0;IndiceMensalAtualizacao);""))){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000)[Red];-
~~~




* * *

##### **IndiceMensalAtualizacaoModificado** `AY:AY`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoModificado)=1;"Modificador";IF(ROW(IndiceMensalAtualizacaoModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresIndiceMensalAtualizacao;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente aos índices 
de atualização mensais

* * *

##### **IndicesReajuste** `P:P`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndicesReajuste)=1;"Índices";IF(ROW(IndicesReajuste)<=TotalCompetencias+1;IF(ROW(IndicesReajuste)=LinhaPrimeiraDataBase;1+INDEX(FatorProporcional;LinhaInicialTabelaIndices);1+({"";OFFSET(FatorIntegral;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)}*Reajustar));""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz correspondente aos índices de reajuste do benefício a serem aplicados

* * *

##### **JurosAbono** `BI:BI`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosAbono)=1;"Juros Abono";IF(ROW(JurosAbono)<=TotalCompetencias+1;ROUND(PrincipalAbonoAtualizado*JurosAcumulados;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que corresponde aos valores de juros que incidem nas parcelas de abono

* * *

##### **JurosAbonoAlcada** `BS:BS`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosAbonoAlcada)=1;"Juros Abono Alçada";IF(ROW(JurosAbonoAlcada)<=TotalCompetencias+1;ROUND(TotalAbonoAlcada*0;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **JurosAcumulados** `BG:BG`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosAcumulados)=1;"Juros Acumulados";IF(ROW(JurosAcumulados)<=TotalCompetencias+1;jef_JUROS_ACUMULADOS(OFFSET(JurosTaxaMensal;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
0.00%
~~~


> Matriz correspondente aos juros acumulados aplicados sobre o valores mensais

* * *

##### **JurosRenda** `BH:BH`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosRenda)=1;"Juros Renda";IF(ROW(JurosRenda)<=TotalCompetencias+1;ROUND(PrincipalRendaAtualizado*JurosAcumulados;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de juros aplicados sobre os valores das rendas mensais

* * *

##### **JurosRendaAlcada** `BQ:BQ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosRendaAlcada)=1;"Juros Renda Alçada";IF(ROW(JurosRendaAlcada)<=TotalCompetencias+1;ROUND(TotalRendaAlcada*0;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **JurosTaxaMensal** `BE:BE`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosTaxaMensal)=1;"Taxa de Juros";IF(ROW(JurosTaxaMensal)<=TotalCompetencias+1;IF(ISNUMBER(JurosTaxaMensalModificada);JurosTaxaMensalModificada;(ROW(JurosTaxaMensal)>=LinhaCitacao)*IF(MID(CriterioJuros;1;1)="3";0,01;IF(MID(CriterioJuros;1;1)="2";0,005;{"";OFFSET(Juros;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)})));""))){% endhighlight %}


~~~
0.00%
~~~


> Matriz correspondente ao valor dos juros aplicados mês a mês de acordo com a opção escolhida

* * *

##### **JurosTaxaMensalModificada** `BF:BF`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosTaxaMensalModificada)=1;"Modificador";IF(ROW(JurosTaxaMensalModificada)<=TotalCompetencias+1;{"";OFFSET(ModificadoresJuros;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente ao valor dos juros aplicados mês a mês

* * *

##### **LinhasAbono** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(LinhasAbono)=1;"Linhas Abono";IF(ROW(LinhasAbono)<=TotalCompetencias+1;IF(CalcularAbono;1;0)*IF((MONTH(Competencia)=12)*(Competencia>=(EOMONTH(DataInicioDiferencas;-1)+1))*(Competencia<=DataFinalDiferencas);TRUE(); IF(ISNUMBER(LimitacaoCalculoAbono);IF(EOMONTH(Competencia;0)=EOMONTH(LimitacaoCalculoAbono;0);TRUE();FALSE())))*ROW(LinhasAbono);""))){% endhighlight %}


~~~
0;0;-
~~~


> Matriz com indicação das linhas que correspondem a meses que devem ser calculados abonos

* * *

##### **Piso** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Piso)=1;"Piso";IF(ROW(Piso)<=TotalCompetencias+1;IF(ISNUMBER(PisoModificado);PisoModificado;{"";OFFSET(SalarioMinimo;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)});""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores dos pisos a serem considerados mês a mês

* * *

##### **PisoModificado** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PisoModificado)=1;"Modificador";IF(ROW(PisoModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresPiso;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificadores referentes aos valores dos pisos a serem considerados mês a mês

* * *

##### **PrincipalAbono** `AV:AV`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalAbono)=1;"Principal Abono";IF(ROW(PrincipalAbono)<=TotalCompetencias+1;(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);EOMONTH(DataInicioDiferencas;-1)+1)))*(Abono)-(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);(EOMONTH(DataInicioDiferencas;-1)+1))))*IF(ISNUMBER(DescontoAbono);DescontoAbono;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal calculados a título de abono, observando as datas de início e cessação de benefício quando informado

* * *

##### **PrincipalAbonoAtualizado** `BC:BC`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalAbonoAtualizado)=1;"Princ. Abono Atual.";IF(ROW(PrincipalAbonoAtualizado)<=TotalCompetencias+1;IF(FatorAtualizacao<1;ROUND(PrincipalAbono;2);ROUND(PrincipalAbono*FatorAtualizacao;2));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal atualizados calculados a título de abono

* * *

##### **PrincipalAlcada** `BT:BT`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalAlcada)=1;"Principal Alçada";IF(ROW(PrincipalAlcada)<=TotalCompetencias+1;IF(FatorAtualizacaoAlcada=0;0;IF(FatorAtualizacaoAlcada<1;PrincipalTotal;TotalRendaAlcada+TotalAbonoAlcada));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **PrincipalRenda** `AU:AU`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalRenda)=1;"Principal Renda";IF(ROW(PrincipalRenda)<=TotalCompetencias+1;(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);(EOMONTH(DataInicioDiferencas;-1)+1))))*(RendaMensalDevida)-(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);(EOMONTH(DataInicioDiferencas;-1)+1))))*IF(ISNUMBER(DescontoRenda);DescontoRenda;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal calculados a título de renda mensal, observando as datas de início e cessação de benefício quando informado


* * *

##### **PrincipalRendaAtualizado** `BB:BB`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalRendaAtualizado)=1;"Princ. Renda Atual.";IF(ROW(PrincipalRendaAtualizado)<=TotalCompetencias+1;IF(FatorAtualizacao<1;ROUND(PrincipalRenda;2);ROUND(PrincipalRenda*FatorAtualizacao;2));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal atualizados calculados a título de renda mensal

* * *

##### **PrincipalTotal** `AW:AW`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalTotal)=1;"Principal Total";IF(ROW(PrincipalTotal)<=TotalCompetencias+1;PrincipalRenda+PrincipalAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal calculados a título de renda mensal e abono

* * *

##### **PrincipalTotalAtualizado** `BD:BD`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalTotalAtualizado)=1;"Principal Total Atual.";IF(ROW(PrincipalTotalAtualizado)<=TotalCompetencias+1;PrincipalRendaAtualizado+PrincipalAbonoAtualizado;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal atualizados calculados a título de renda mensal e abono

* * *

##### **PrincipalTotalAtualizadoAposRenuncia** `BV:BV`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalTotalAtualizadoAposRenuncia)=1;"Principal Total Atual com Renúncia";IF(ROW(PrincipalTotalAtualizadoAposRenuncia)<=TotalCompetencias+1;PrincipalTotalAtualizado*ProporcaoAposRenuncia;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **ProporcaoAbono** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ProporcaoAbono)=1;"Proporção Abono";IF(ROW(ProporcaoAbono)<=TotalCompetencias+1;IF(ROW(ProporcaoAbono)=LinhaPrimeiroAbono;ProporcaoPrimeiroAbono;IF(ROW(ProporcaoAbono)=UltimaLinhaAbono;ProporcaoUltimoAbono;IF(LinhasAbono<>0;1;0)));""))){% endhighlight %}


~~~
0.00
~~~


> Matriz referente às proporções  consideradas para apuração dos valores dos abonos

* * *

##### **ProporcaoAposRenuncia** `BU:BU`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ProporcaoAposRenuncia)=1;"Proporção Após Renúncia";IF(ROW(ProporcaoAposRenuncia)<=TotalCompetencias+1; IF(EOMONTH(Competencia;0)<EOMONTH(Protocolo;0);PercentualVencidasAposRenuncia;1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **ProporcaoRenda** `B:B`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ProporcaoRenda)=1;"Proporção Renda";IF(ROW(ProporcaoRenda)<=TotalCompetencias+1; IF(EOMONTH(Competencia;0)=EOMONTH(DataInicioDiferencas;0);ProporcaoInicial;IF(ROW(ProporcaoRenda)=MATCH(DataFinalDiferencas;Competencia);ProporcaoFinal;1));""))){% endhighlight %}


~~~
0.00
~~~


> Matriz correspondente às proporções das rendas mensais calculadas

* * *

##### **QuotaRendaMensal** `AM:AM`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(QuotaRendaMensal)=1;"Quota Percent.";IF(ROW(QuotaRendaMensal)<=TotalCompetencias+1;OFFSET(ModificadoresQuotaRendaMensal;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.00%
~~~


> Matriz referente aos valores das quotas lançadas na aba Modificadores

* * *

##### **Reajustar** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Reajustar)=1;"Reajustar";IF(ROW(Reajustar)<=TotalCompetencias+1;IF(ROW(Reajustar)=LinhaPrimeiraCompetencia;FALSE();IF(ROW(Reajustar)=LinhaReajusteLei8870;TRUE();{"";OFFSET(DataBase;LinhaInicialTabelaIndices-1;0;TotalCompetencias)}));""))){% endhighlight %}



> Matriz correspondente aos meses em que há aplicação de índice de reajuste do valor do benefício

* * *

##### **ReajusteArt58** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteArt58)=1;"Art. 58 ADCT";IF(ROW(ReajusteArt58)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58);IF(ROW(ReajusteArt58)<LinhaEquivalenciaSalarial;0;1);1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que zera os reajustes anteriores à aplicação do artigo 58 do ADCT

* * *

##### **ReajusteArt58NBPago** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteArt58NBPago)=1;"Art. 58 ADCT Pago";IF(ROW(ReajusteArt58NBPago)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58NBPago);IF(ROW(ReajusteArt58NBPago)<LinhaEquivalenciaSalarial;0;1);1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que zera os reajustes anteriores à aplicação do artigo 58 do ADCT (benefício pago)

* * *

##### **ReajusteLei8870** `L:L`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteLei8870)=1;"Art. 26 Lei 8.870";IF(ROW(ReajusteLei8870)<=TotalCompetencias+1;IF(ROW(ReajusteLei8870)=LinhaReajusteLei8870;IndiceTeto;1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que indica o reajuste a ser aplicado conforme artigo 26 da Lei 8.870/94

* * *

##### **ReajusteLei8870NBPago** `M:M`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteLei8870NBPago)=1;"Art. 26 Lei 8.870 Pago";IF(ROW(ReajusteLei8870NBPago)<=TotalCompetencias+1;IF(ROW(ReajusteLei8870NBPago)=LinhaReajusteLei8870;IndiceTetoNBPago;1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que indica o reajuste a ser aplicado conforme artigo 26 da Lei 8.870/94 (benefício pago)

* * *

##### **ReajusteLei8880** `N:N`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteLei8880)=1;"Art. 21 Lei 8.880";IF(ROW(ReajusteLei8880)<=TotalCompetencias+1; IF(ROW(ReajusteLei8880)=LinhaReajusteLei8880;IndiceTeto;1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que indica o reajuste a ser aplicado conforme artigo 21, § 3º da Lei 8.880/94

* * *

##### **ReajusteLei8880NBPago** `O:O`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteLei8880NBPago)=1;"Art. 21 Lei 8.880 Pago";IF(ROW(ReajusteLei8880NBPago)<=TotalCompetencias+1; IF(ROW(ReajusteLei8880NBPago)=LinhaReajusteLei8880;IndiceTetoNBPago;1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que indica o reajuste a ser aplicado conforme artigo 21, § 3º da Lei 8.880/94 (benefício pago)

* * *

##### **RendaApurada** `AD:AD`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaApurada)=1;"Renda Apurada";IF(ROW(RendaApurada)<=TotalCompetencias+1;SalarioBeneficioLimitado*Coeficiente;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica a evolução do valor do salário-de-benefício, com aplicação do coeficiente devido

* * *

##### **RendaApuradaNBPago** `AE:AE`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaApuradaNBPago)=1;"Renda Apurada Paga";IF(ROW(RendaApuradaNBPago)<=TotalCompetencias+1;SalarioBeneficioLimitadoNBPago*CoeficienteNBPago;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica a evolução do valor do salário-de-benefício, com aplicação do coeficiente (benefício pago)

* * *

##### **RendaInformadaLimitada** `AH:AH`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaInformadaLimitada)=1;"Renda Inform. Lim.";IF(ROW(RendaInformadaLimitada)<=TotalCompetencias+1;IF(RendaInformadaReajustada>Teto;Teto;IF(RendaInformadaReajustada<Piso;Piso;RendaInformadaReajustada));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores da renda mensal, observados os limites mínimo e máximo

* * *

##### **RendaInformadaLimitadaNBPago** `AI:AI`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaInformadaLimitadaNBPago)=1;"Renda Inform. Lim. Paga";IF(ROW(RendaInformadaLimitadaNBPago)<=TotalCompetencias+1;IF(RendaInformadaReajustadaNBPago=0;0;IF(RendaInformadaReajustadaNBPago>Teto;Teto;IF(RendaInformadaReajustadaNBPago<Piso;Piso;RendaInformadaReajustadaNBPago)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores da renda mensal, observados os limites mínimo e máximo (benefício pago)

* * *

##### **RendaInformadaReajustada** `AF:AF`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaInformadaReajustada)=1;"Renda Inform. Reaj.";IF(ROW(RendaInformadaReajustada)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58);IF(ROW(RendaInformadaReajustada)=2;RMIArt58;IF(ROW(RendaInformadaReajustada)<LinhaEquivalenciaSalarial-1;0;  jef_EVOLUCAO_RENDA(RendaAtualArt58;OFFSET(FatorReajuste;0;0;TotalCompetencias+1))));jef_EVOLUCAO_RENDA(RendaInformada;OFFSET(FatorReajuste;0;0;TotalCompetencias+1)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica a evolução do valor da RMI devida

* * *

##### **RendaInformadaReajustadaNBPago** `AG:AG`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaInformadaReajustadaNBPago)=1;"Renda Inform. Reaj. Paga";IF(ROW(RendaInformadaReajustadaNBPago)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58NBPago);IF(ROW(RendaInformadaReajustadaNBPago)=2;RMIArt58NBPago;IF(ROW(RendaInformadaReajustadaNBPago)<LinhaEquivalenciaSalarial-1;0;  jef_EVOLUCAO_RENDA(RendaAtualArt58NBPago;OFFSET(FatorReajusteNBPago;0;0;TotalCompetencias+1))));jef_EVOLUCAO_RENDA(RendaInformadaNBPago;OFFSET(FatorReajusteNBPago;0;0;TotalCompetencias+1)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica a evolução do valor da RMI paga

* * *

##### **RendaMensalDevida** `AL:AL`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaMensalDevida)=1;"Renda Devida";IF(ROW(RendaMensalDevida)<=TotalCompetencias+1;RendaMensalEfetiva*ProporcaoRenda;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores referentes às rendas mensais, bem como suas proporções

* * *

##### **RendaMensalEfetiva** `AJ:AJ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaMensalEfetiva)=1;"Renda Efetiva";IF(ROW(RendaMensalEfetiva)<=TotalCompetencias+1;IF(MID(CriterioReajuste;1;1)="1";RendaInformadaLimitada;IF(MID(CriterioReajuste;1;1)="2";RendaApurada;IF(Competencia<EOMONTH(DIBDerivado;-1)+1;RendaInformadaLimitada;IF(Competencia>EOMONTH(DIBDerivado;-1)+1;RendaApurada;RendaNaConversao))));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores das rendas mensais a serem consideradas, observando eventual conversão de benefício

* * *

##### **RendaMensalEfetivaNBPago** `AK:AK`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaMensalEfetivaNBPago)=1;"Renda Efetiva Paga";IF(ROW(RendaMensalEfetivaNBPago)<=TotalCompetencias+1;IF(MID(CriterioReajuste;1;1)="1";RendaInformadaLimitadaNBPago;IF(MID(CriterioReajuste;1;1)="2";RendaApuradaNBPago;IF(Competencia<EOMONTH(DIBDerivado;-1)+1;RendaInformadaLimitadaNBPago;IF(Competencia>EOMONTH(DIBDerivado;-1)+1;RendaApuradaNBPago;RendaNaConversaoNBPago))));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores das rendas mensais a serem consideradas, observando eventual conversão (benefício pago)

* * *

##### **RendaMensalNBPago** `AO:AO`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaMensalNBPago)=1;"Renda Paga";IF(ROW(RendaMensalNBPago)<=TotalCompetencias+1;RendaMensalEfetivaNBPago*ProporcaoRenda;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores referentes às rendas mensais pagas, bem como suas proporções

* * *

##### **RevisaoArt58** `U:U`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RevisaoArt58)=1;"Revisão Art. 58";IF(ROW(RevisaoArt58)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58);IF(Competencia=(EOMONTH(DIBArt58;-1)+1);RMIArt58;IF(Competencia=DATE(1991;12;1);RendaAtualArt58;IF(Competencia<DATE(1991;12;1);0;0))));""))){% endhighlight %}



> Matriz correspondente aos meses em que o benefício será recuperado pela equivalência salarial (dezembro/91)

* * *

##### **SalarioBeneficioLimitado** `X:X`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBeneficioLimitado)=1;"Sal. Limitado";IF(ROW(SalarioBeneficioLimitado)<=TotalCompetencias+1;IF(SalarioBeneficioReajustado>Teto;Teto;IF(SalarioBeneficioReajustado<Piso;Piso;SalarioBeneficioReajustado));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente ao valor do salário-de-benefício evoluído, observados os limites mínimo e máximo

* * *

##### **SalarioBeneficioLimitadoNBPago** `Y:Y`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBeneficioLimitadoNBPago)=1;"Sal. Limitado Pago";IF(ROW(SalarioBeneficioLimitadoNBPago)<=TotalCompetencias+1;IF(SalarioBeneficioReajustadoNBPago=0;0;IF(SalarioBeneficioReajustadoNBPago>Teto;Teto;IF(SalarioBeneficioReajustadoNBPago<Piso;Piso;SalarioBeneficioReajustadoNBPago)));""))){% endhighlight %}


~~~
0.00%
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente ao valor do salário-de-benefício evoluído, observados os limites mínimo e máximo (benefício pago)

* * *

##### **SalarioBeneficioReajustado** `V:V`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBeneficioReajustado)=1;"Sal. Reajustado";IF(ROW(SalarioBeneficioReajustado)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58);IF(ROW(SalarioBeneficioReajustado)=2;RMIArt58;IF(ROW(SalarioBeneficioReajustado)<LinhaEquivalenciaSalarial-1;0;  jef_EVOLUCAO_RENDA(RendaAtualArt58;OFFSET(FatorReajuste;0;0;TotalCompetencias+1))));jef_EVOLUCAO_RENDA(SalarioBeneficio;OFFSET(FatorReajuste;0;0;TotalCompetencias+1)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente ao valor do salário-de-benefício evoluído com base nos fatores de reajuste

* * *

##### **SalarioBeneficioReajustadoNBPago** `W:W`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBeneficioReajustadoNBPago)=1;"Sal. Reajustado Pago";IF(ROW(SalarioBeneficioReajustadoNBPago)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58NBPago);IF(ROW(SalarioBeneficioReajustadoNBPago)=2;RMIArt58NBPago;IF(ROW(SalarioBeneficioReajustadoNBPago)<LinhaEquivalenciaSalarial-1;0;  jef_EVOLUCAO_RENDA(RendaAtualArt58NBPago;OFFSET(FatorReajusteNBPago;0;0;TotalCompetencias+1))));jef_EVOLUCAO_RENDA(SalarioBeneficioNBPago;OFFSET(FatorReajusteNBPago;0;0;TotalCompetencias+1)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente ao valor do salário-de-benefício pago evoluído com base nos fatores de reajuste

* * *

##### **Teto** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Teto)=1;"Teto";IF(ROW(Teto)<=TotalCompetencias+1;IF(ISNUMBER(TetoModificado);TetoModificado;{"";OFFSET(TetoBeneficio;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)});""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores dos tetos a serem considerados mês a mês

* * *

##### **TetoModificado** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TetoModificado)=1;"Modificador";IF(ROW(TetoModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresTeto;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificadores referentes aos valores dos tetos a serem considerados mês a mês

* * *

##### **TotalAbono** `BL:BL`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalAbono)=1;"Total Abono";IF(ROW(TotalAbono)<=TotalCompetencias+1;PrincipalAbonoAtualizado+JurosAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de principal e juros sobre parcelas de abonos

* * *

##### **TotalAbonoAlcada** `BR:BR`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalAbonoAlcada)=1;"Total Abono Alçada";IF(ROW(TotalAbonoAlcada)<=TotalCompetencias+1;ROUND(PrincipalAbono*FatorAtualizacaoAlcada;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalJuros** `BJ:BJ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalJuros)=1;"Total Juros";IF(ROW(TotalJuros)<=TotalCompetencias+1;JurosRenda+JurosAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de juros sobre parcelas de rendas mensais e abonos

* * *

##### **TotalJurosAposRenuncia** `BW:BW`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalJurosAposRenuncia)=1;"Juros Total Atualizado com Renúncia";IF(ROW(TotalJurosAposRenuncia)<=TotalCompetencias+1;TotalJuros*ProporcaoAposRenuncia;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalMes** `BM:BM`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalMes)=1;"Total Mês";IF(ROW(TotalMes)<=TotalCompetencias+1;TotalRenda+TotalAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de principal e juros sobre parcelas de rendas mensais e abonos

* * *

##### **TotalMesAposRenuncia** `BX:BX`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalMesAposRenuncia)=1;"Total Mês Após Renúncia";IF(ROW(TotalMesAposRenuncia)<=TotalCompetencias+1;PrincipalTotalAtualizadoAposRenuncia+TotalJurosAposRenuncia;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores mensais atualizados até a data do ajuizamento da ação

* * *

##### **TotalRenda** `BK:BK`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalRenda)=1;"Total Renda";IF(ROW(TotalRenda)<=TotalCompetencias+1;PrincipalRendaAtualizado+JurosRenda;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de principal e juros sobre parcelas de renda mensal

* * *

##### **TotalRendaAlcada** `BP:BP`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalRendaAlcada)=1;"Total Renda Alçada";IF(ROW(TotalRendaAlcada)<=TotalCompetencias+1;ROUND(PrincipalRenda*FatorAtualizacaoAlcada;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **ValorQuota** `AN:AN`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ValorQuota)=1;"Valor da Quota";IF(ROW(ValorQuota)<=TotalCompetencias+1;RendaMensalDevida*IF(ISNUMBER(QuotaRendaMensal);QuotaRendaMensal;1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores referentes às rendas devidas, com aplicação de quota percentual

* * *

##### **ValorQuotaNBPago** `AP:AP`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ValorQuotaNBPago)=1;"Valor da Quota Paga";IF(ROW(ValorQuotaNBPago)<=TotalCompetencias+1;(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);ProporcaoInicial)))*(RendaMensalNBPago)*IF(ISNUMBER(QuotaRendaMensal);QuotaRendaMensal;1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores referentes às rendas devidas, com aplicação de quota percentual (benefício pago)