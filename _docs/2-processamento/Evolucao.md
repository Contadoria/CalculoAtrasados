---
title: Evolucao
category: Processamento
order: 0
---

##### **Abono** `AH:AH`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Abono)=1;"Abono";IF(ROW(Abono)<=TotalCompetencias+1;(RendaMensalEfetiva*QuotaRendaMensal)*ProporcaoAbono+IF(ProporcaoAbono>0;IF(DataInicioAdicional25;IF(Competencia>DataInicioAdicional25;ROUNDDOWN(RendaMensalEfetiva*0,25*ProporcaoAbono;2);0);0);0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores devidos calculados a título de abono

* * *

##### **Adicional25** `Y:Y`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Adicional25)=1;"Adicional 25 Por Cento";IF(ROW(Adicional25)<=TotalCompetencias+2;IF(DataInicioAdicional25;IF(Competencia=EOMONTH(DataInicioAdicional25;-1)+1;Adicional25PrimeiraCompetencia;IF(Competencia>DataInicioAdicional25;ROUNDDOWN(RendaMensalEfetiva*0,25*ProporcaoRenda;2);0));0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **Coeficiente** `S:S`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Coeficiente)=1;"Coeficiente";IF(ROW(Coeficiente)<=TotalCompetencias+2;IF(ISNUMBER(CoeficienteModificado);CoeficienteModificado;IF(TemDerivado;IF(Competencia>=EOMONTH(DIBDerivado;-1)+1;CoeficienteDerivado;CoeficienteOriginario);CoeficienteOriginario));""))){% endhighlight %}


~~~
0.00%
~~~


> Matriz correspondente aos coeficientes aplicados durante o período, observando os benefícios originário e derivado

* * *

##### **CoeficienteModificado** `T:T`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CoeficienteModificado)=1;"Modificador";IF(ROW(CoeficienteModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresCoeficiente;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}



> Modificador referente à matriz correspondente aos coeficientes aplicados durante o período

* * *

##### **Competencia** `A:A`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Competencia)=1;"Competência";IF(ROW(Competencia)<=TotalCompetencias+2;EOMONTH(DIBOriginario;ROW(OFFSET(Competencia;0;0;TotalCompetencias+2))-3)+1;""))){% endhighlight %}


~~~
mm/yyyy
~~~


> Matriz ajustada com base no período de meses entre a data de início e a data final do cálculo.


* * *

##### **DescontoAbono** `AJ:AJ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DescontoAbono)=1;"Desconto Abono";IF(ROW(DescontoAbono)<=TotalCompetencias+1;OFFSET(DescontosTotalAbonoValor;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+1)+(OFFSET(DescontosTotalAbonoPercentual;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+1)*OFFSET(Abono;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **DescontoRenda** `AI:AI`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DescontoRenda)=1;"Desconto Renda";IF(ROW(DescontoRenda)<=TotalCompetencias+2;OFFSET(DescontosTotalRendaValor;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+2)+(OFFSET(DescontosTotalRendaPercentual;LinhaInicialTabelaDescontos-2;0;TotalCompetencias+2)*OFFSET(RendaMensalDevida;0;0;TotalCompetencias+2));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **Desdobro1** `AA:AA`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Desdobro1)=1;"Desdobro1";IF(ROW(Desdobro1)>TotalCompetencias+2;"";IF(ISNUMBER(DIBBeneficioDesdobrado);IF(ISNUMBER(DataDesdobro1);IF(EOMONTH(DataDesdobro1;-1)+1=Competencia;QuotaProporcional1;IF(Competencia<EOMONTH(DataDesdobro1;-1)+1;0;IF(ISNUMBER(DataDesdobro2);IF(Competencia>=EOMONTH(DataDesdobro2;-1)+1;0;QuotaDevida1-QuotaPaga1);QuotaDevida1-QuotaPaga1)));0);0)))){% endhighlight %}


~~~
0.00%
~~~




* * *

##### **Desdobro2** `AB:AB`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Desdobro2)=1;"Desdobro2";IF(ROW(Desdobro2)>TotalCompetencias+2;"";IF(ISNUMBER(DIBBeneficioDesdobrado);IF(ISNUMBER(DataDesdobro2);IF(EOMONTH(DataDesdobro2;-1)+1=Competencia;QuotaProporcional2;IF(Competencia<EOMONTH(DataDesdobro2;-1)+1;0;IF(ISNUMBER(DataDesdobro3);IF(Competencia>=EOMONTH(DataDesdobro3;-1)+1;0;QuotaDevida2-QuotaPaga2);QuotaDevida2-QuotaPaga2)));0);0)))){% endhighlight %}


~~~
0.00%
~~~




* * *

##### **Desdobro3** `AC:AC`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Desdobro3)=1;"Desdobro3";IF(ROW(Desdobro3)>TotalCompetencias+2;"";IF(ISNUMBER(DIBBeneficioDesdobrado);IF(ISNUMBER(DataDesdobro3);IF(EOMONTH(DataDesdobro3;-1)+1=Competencia;QuotaProporcional3;IF(Competencia<EOMONTH(DataDesdobro3;-1)+1;0;IF(ISNUMBER(DataDesdobro4);IF(Competencia>=EOMONTH(DataDesdobro4;-1)+1;0;QuotaDevida3-QuotaPaga3);QuotaDevida3-QuotaPaga3)));0);0)))){% endhighlight %}


~~~
0.00%
~~~




* * *

##### **Desdobro4** `AD:AD`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Desdobro4)=1;"Desdobro4";IF(ROW(Desdobro4)>TotalCompetencias+2;"";IF(ISNUMBER(DIBBeneficioDesdobrado);IF(ISNUMBER(DataDesdobro4);IF(EOMONTH(DataDesdobro4;-1)+1=Competencia;QuotaProporcional4;IF(Competencia<EOMONTH(DataDesdobro4;-1)+1;0;IF(ISNUMBER(DataDesdobro5);IF(Competencia>=EOMONTH(DataDesdobro5;-1)+1;0;QuotaDevida4-QuotaPaga4);QuotaDevida4-QuotaPaga4)));0);0)))){% endhighlight %}


~~~
0.00%
~~~




* * *

##### **Desdobro5** `AE:AE`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Desdobro5)=1;"Desdobro5";IF(ROW(Desdobro5)>TotalCompetencias+2;"";IF(ISNUMBER(DIBBeneficioDesdobrado);IF(ISNUMBER(DataDesdobro5);IF(EOMONTH(DataDesdobro5;-1)+1=Competencia;QuotaProporcional5;IF(Competencia<EOMONTH(DataDesdobro5;-1)+1;0;QuotaDevida5-QuotaPaga5));0);0)))){% endhighlight %}


~~~
0.00%
~~~




* * *

##### **FatorAtualizacao** `AQ:AQ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorAtualizacao)=1;"Fator Atualização";IF(ROW(FatorAtualizacao)<=TotalCompetencias+1;jef_INDICE_ACUMULADO(OFFSET(IndiceMensalAtualizacaoAjustado;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
~~~


> Matriz correspondente aos fatores de atualização (índice acumulado)

* * *

##### **FatorAtualizacaoAlcada** `BE:BE`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorAtualizacaoAlcada)=1;"Fator Atual. Alçada";IF(ROW(FatorAtualizacaoAlcada)<=TotalCompetencias+1;IF(ROW(FatorAtualizacaoAlcada)>LinhaProtocolo-1;0;jef_INDICE_ACUMULADO(OFFSET(IndiceMensalAtualizacaoAlcada;0;0;TotalCompetencias+1)));""))){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000)[Red];-
~~~


> Matriz correspondente aos fatores de atualização até a data do ajuizamento da ação (índice acumulado)

* * *

##### **FatorReajuste** `N:N`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorReajuste)=1;"Fator Reajuste";IF(ROW(FatorReajuste)<=TotalCompetencias+2;IF(ISNUMBER(FatorReajusteModificado);FatorReajusteModificado;IF(Reajustar;IF(ReajusteArt58*ReajusteLei8870*ReajusteLei8880*IndicesReajuste=0;1;ReajusteArt58*ReajusteLei8870*ReajusteLei8880*IndicesReajuste);1));""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz correspondente aos fatores de reajuste do benefício a serem aplicados (observando artigo 58 do ADCT, artigo 26 da Lei 8.870/94 e artigo 21, §3º da Lei 8.880/94)

**17/10/2017**: introduzida nova condição para o caso de reajuste, a fim de transformar os "zeros" em "uns". Sem essa condição, não estava sendo possível calcular benefícios sujeitos à aplicação do art. 58 do ADCT, que ficavam todos abaixo do mínimo em virtude da multiplicação por zero.

* * *

##### **FatorReajusteModificado** `O:O`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorReajusteModificado)=1;"Modificador";IF(ROW(FatorReajusteModificado)<=TotalCompetencias+2;{"";OFFSET(ModificadoresFatorReajuste;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}



> Modificador referente aos fatores de reajuste do benefício

* * *

##### **IndiceMensalAtualizacao** `AN:AN`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacao)=1;"Índice";IF(ROW(IndiceMensalAtualizacao)<=TotalCompetencias+1;IF(ISNUMBER(IndiceMensalAtualizacaoModificado);IndiceMensalAtualizacaoModificado; IF(ISNUMBER(DataInicioIPCAE);{"";IF(DataInicioIPCAE>CompetenciaInicial;OFFSET(IF(MID(CriterioCorrecao;1;1)="2";IndiceRes134;IndiceAtualizacao);LinhaInicialTabelaIndices-1;0;DATEDIF(CompetenciaInicial;DataInicioIPCAE;"M"));OFFSET(IPCAE;MATCH(DataInicioIPCAE;CompetenciaIndices;0)-1;0;DATEDIF(EOMONTH(DataInicioIPCAE;-2)+1;CompetenciaFinal;"M")-IF(DataAtualizacao=CompetenciaFinal;1;0)));OFFSET(IPCAE;MATCH(DataInicioIPCAE;CompetenciaIndices;0)-1;0;DATEDIF(EOMONTH(DataInicioIPCAE;-2)+1;CompetenciaFinal;"M")-IF(DataAtualizacao=CompetenciaFinal;1;0));IF(DataAtualizacao=CompetenciaFinal;1)};{"";OFFSET(IF(MID(CriterioCorrecao;1;1)="2";IndiceRes134;IndiceAtualizacao);LinhaInicialTabelaIndices-1;0;TotalCompetencias-IF(DataAtualizacao=CompetenciaFinal;1;0));IF(DataAtualizacao=CompetenciaFinal;1)}));""))){% endhighlight %}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
~~~


> Matriz correspondente aos índices 
de atualização mensais conforme opção escolhida

* * *

##### **IndiceMensalAtualizacaoAjustado** `AP:AP`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoAjustado)=1;"Índice Ajustado";IF(ROW(IndiceMensalAtualizacaoAjustado)<=TotalCompetencias+1;OFFSET(AjusteMoeda;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)*IndiceMensalAtualizacao;""))){% endhighlight %}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
~~~


> Matriz correspondente aos índices 
de atualização mensais, considerando os ajustes de moeda

* * *

##### **IndiceMensalAtualizacaoAlcada** `BD:BD`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoAlcada)=1;"Indices Alçada";IF(ROW(IndiceMensalAtualizacaoAlcada)<=TotalCompetencias+1;IF(ROW(IndiceMensalAtualizacaoAlcada)>LinhaProtocolo-1;0;IndiceMensalAtualizacaoAjustado);""))){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000)[Red];-
~~~




* * *

##### **IndiceMensalAtualizacaoModificado** `AO:AO`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoModificado)=1;"Modificador";IF(ROW(IndiceMensalAtualizacaoModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresIndiceMensalAtualizacao;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificador referente aos índices 
de atualização mensais

* * *

##### **IndicesReajuste** `M:M`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndicesReajuste)=1;"Índices";IF(ROW(IndicesReajuste)<=TotalCompetencias+2;IF(ROW(IndicesReajuste)=LinhaPrimeiraDataBase;1+INDEX(FatorProporcional;LinhaInicialTabelaIndices);1+({"";OFFSET(FatorIntegral;LinhaInicialTabelaIndices-1;0;TotalCompetencias+2)}*Reajustar));""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz correspondente aos índices de reajuste do benefício a serem aplicados

* * *

##### **JurosAbono** `AY:AY`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosAbono)=1;"Juros Abono";IF(ROW(JurosAbono)<=TotalCompetencias+1;ROUND(PrincipalAbonoAtualizado*JurosAcumulados;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que corresponde aos valores de juros que incidem nas parcelas de abono

* * *

##### **JurosAbonoAlcada** `BI:BI`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosAbonoAlcada)=1;"Juros Abono Alçada";IF(ROW(JurosAbonoAlcada)<=TotalCompetencias+1;ROUND(TotalAbonoAlcada*0;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **JurosAcumulados** `AW:AW`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosAcumulados)=1;"Juros Acumulados";IF(ROW(JurosAcumulados)<=TotalCompetencias+1;jef_JUROS_ACUMULADOS(OFFSET(JurosTaxaMensal;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
0.00%
~~~


> Matriz correspondente aos juros acumulados aplicados sobre o valores mensais

* * *

##### **JurosRenda** `AX:AX`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosRenda)=1;"Juros Renda";IF(ROW(JurosRenda)<=TotalCompetencias+1;ROUND(PrincipalRendaAtualizado*JurosAcumulados;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de juros aplicados sobre os valores das rendas mensais

* * *

##### **JurosRendaAlcada** `BG:BG`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosRendaAlcada)=1;"Juros Renda Alçada";IF(ROW(JurosRendaAlcada)<=TotalCompetencias+1;ROUND(TotalRendaAlcada*0;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **JurosTaxaMensal** `AU:AU`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(JurosTaxaMensal)=1;"Taxa de Juros";IF(ROW(JurosTaxaMensal)<=TotalCompetencias+1;IF(ISNUMBER(JurosTaxaMensalModificada);JurosTaxaMensalModificada;IF(ISTEXT(CriterioJuros);(ROW(JurosTaxaMensal)>=LinhaCitacao)*(ROW(JurosTaxaMensal)<LinhaAtualizacao)*IF(MID(CriterioJuros;1;1)="3";0,01;IF(MID(CriterioJuros;1;1)="2";0,005;{"";OFFSET(Juros;LinhaInicialTabelaIndices;0;TotalCompetencias+1)}));0));""))){% endhighlight %}


~~~
0.00%
~~~


> Matriz correspondente ao valor dos juros aplicados mês a mês de acordo com a opção escolhida.
Busca da taxa de juros referente ao mês posterior à competência conforme Manual de Cálculos - item 4.3.2 (alterado em 23/10/2017)
Percentual calculado apenas até o mês anterior à data da atualização (alterado em 08/11/2017)

* * *

##### **JurosTaxaMensalModificada** `AV:AV`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
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
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Piso)=1;"Piso";IF(ROW(Piso)<=TotalCompetencias+2;IF(ISNUMBER(PisoModificado);PisoModificado;{"";OFFSET(SalarioMinimo;LinhaInicialTabelaIndices-1;0;TotalCompetencias+2)*IF(EspecieOriginario=36;0,5;1)});""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores dos pisos a serem considerados mês a mês
Incluída opção para auxílio-acidente (provisório) (alterado em 30/10/17)

* * *

##### **PisoModificado** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PisoModificado)=1;"Modificador";IF(ROW(PisoModificado)<=TotalCompetencias+1;{"";OFFSET(ModificadoresPiso;LinhaInicialTabelaModificadores-1;0;TotalCompetencias+1)};""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificadores referentes aos valores dos pisos a serem considerados mês a mês

* * *

##### **PrincipalAbono** `AL:AL`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalAbono)=1;"Principal Abono";IF(ROW(PrincipalAbono)<=TotalCompetencias+1;(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);EOMONTH(DataInicioDiferencas;-1)+1)))*(Abono)-(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);(EOMONTH(DataInicioDiferencas;-1)+1))))*IF(ISNUMBER(DescontoAbono);DescontoAbono;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal calculados a título de abono, observando as datas de início e cessação de benefício quando informado

* * *

##### **PrincipalAbonoAtualizado** `AS:AS`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalAbonoAtualizado)=1;"Princ. Abono Atual.";IF(ROW(PrincipalAbonoAtualizado)<=TotalCompetencias+1;IF(FatorAtualizacao<1;ROUND(PrincipalAbono;2);ROUND(PrincipalAbono*FatorAtualizacao;2));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal atualizados calculados a título de abono

* * *

##### **PrincipalAlcada** `BJ:BJ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalAlcada)=1;"Principal Alçada";IF(ROW(PrincipalAlcada)<=TotalCompetencias+1;IF(FatorAtualizacaoAlcada=0;0;IF(FatorAtualizacaoAlcada<1;PrincipalTotal;TotalRendaAlcada+TotalAbonoAlcada));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **PrincipalRenda** `AK:AK`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalRenda)=1;"Principal Renda";IF(ROW(PrincipalRenda)<=TotalCompetencias+1;(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);(EOMONTH(DataInicioDiferencas;-1)+1))))*(ValorQuota)-(Competencia<=(EOMONTH(DataFinalDiferencas;-1)+1))*(Competencia>=(MAX((EOMONTH(MarcoPrescricional;-1)+1);(EOMONTH(DataInicioDiferencas;-1)+1))))*IF(ISNUMBER(DescontoRenda);DescontoRenda;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal calculados a título de renda mensal, observando as datas de início e cessação de benefício quando informado


* * *

##### **PrincipalRendaAtualizado** `AR:AR`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalRendaAtualizado)=1;"Princ. Renda Atual.";IF(ROW(PrincipalRendaAtualizado)<=TotalCompetencias+1;IF(FatorAtualizacao<1;ROUND(PrincipalRenda;2);ROUND(PrincipalRenda*FatorAtualizacao;2));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal atualizados calculados a título de renda mensal

* * *

##### **PrincipalTotal** `AM:AM`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalTotal)=1;"Principal Total";IF(ROW(PrincipalTotal)<=TotalCompetencias+1;PrincipalRenda+PrincipalAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal calculados a título de renda mensal e abono

* * *

##### **PrincipalTotalAtualizado** `AT:AT`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalTotalAtualizado)=1;"Principal Total Atual.";IF(ROW(PrincipalTotalAtualizado)<=TotalCompetencias+1;PrincipalRendaAtualizado+PrincipalAbonoAtualizado;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz referente aos valores de principal atualizados calculados a título de renda mensal e abono

* * *

##### **PrincipalTotalAtualizadoAcordo** `BO:BO`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalTotalAtualizadoAcordo)=1;"Principal Total Atual Acordo";IF(ROW(PrincipalTotalAtualizadoAcordo)<=TotalCompetencias+1;ROUND(PercentualAcordo*IF(RenunciaOpcao="Sim";PrincipalTotalAtualizadoAposRenuncia;PrincipalTotalAtualizado);2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **PrincipalTotalAtualizadoAposRenuncia** `BL:BL`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PrincipalTotalAtualizadoAposRenuncia)=1;"Principal Total Atual com Renúncia";IF(ROW(PrincipalTotalAtualizadoAposRenuncia)<=TotalCompetencias+1;ROUND(PrincipalTotalAtualizado*ProporcaoAposRenuncia;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Arredondamento para duas casas (alterado em 15/02/18).

* * *

##### **ProporcaoAbono** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ProporcaoAbono)=1;"Proporção Abono";IF(ROW(ProporcaoAbono)<=TotalCompetencias+1;IF(ROW(ProporcaoAbono)=LinhaPrimeiroAbono;ProporcaoPrimeiroAbono;IF(ROW(ProporcaoAbono)=UltimaLinhaAbono;ProporcaoUltimoAbono;IF(LinhasAbono<>0;1;0)));""))){% endhighlight %}


~~~
0.00
~~~


> Matriz referente às proporções  consideradas para apuração dos valores dos abonos

* * *

##### **ProporcaoAposRenuncia** `BK:BK`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
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

##### **QuotaRendaMensal** `AF:AF`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(QuotaRendaMensal)=1;"Quota Percent.";IF(ROW(QuotaRendaMensal)>TotalCompetencias+2;"";IF(ISNUMBER(OFFSET(ModificadoresQuotaRendaMensal;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+2));OFFSET(ModificadoresQuotaRendaMensal;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+2);IF(Desdobro1+Desdobro2+Desdobro3+Desdobro4+Desdobro5=0;1;Desdobro1+Desdobro2+Desdobro3+Desdobro4+Desdobro5))))){% endhighlight %}


~~~
0.00%
~~~


> Matriz referente aos valores das quotas lançadas na aba Modificadores

* * *

##### **Reajustar** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Reajustar)=1;"Reajustar";IF(ROW(Reajustar)<=TotalCompetencias+2;IF(ROW(Reajustar)=LinhaPrimeiraCompetencia;FALSE();IF(ROW(Reajustar)=LinhaReajusteLei8870;TRUE();{"";OFFSET(DataBase;LinhaInicialTabelaIndices-1;0;TotalCompetencias+1)}));""))){% endhighlight %}



> Matriz correspondente aos meses em que há aplicação de índice de reajuste do valor do benefício

* * *

##### **ReajusteArt58** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteArt58)=1;"Art. 58 ADCT";IF(ROW(ReajusteArt58)<=TotalCompetencias+2;IF(ISNUMBER(RendaAtualArt58);IF(ROW(ReajusteArt58)<LinhaEquivalenciaSalarial;0;1);1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que zera os reajustes anteriores à aplicação do artigo 58 do ADCT

* * *

##### **ReajusteLei8870** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteLei8870)=1;"Art. 26 Lei 8.870";IF(ROW(ReajusteLei8870)<=TotalCompetencias+2;IF(ROW(ReajusteLei8870)=LinhaReajusteLei8870;IndiceTeto;1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que indica o reajuste a ser aplicado conforme artigo 26 da Lei 8.870/94

* * *

##### **ReajusteLei8880** `L:L`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ReajusteLei8880)=1;"Art. 21 Lei 8.880";IF(ROW(ReajusteLei8880)<=TotalCompetencias+2; IF(ROW(ReajusteLei8880)=LinhaReajusteLei8880;IndiceTeto;1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Matriz que indica o reajuste a ser aplicado conforme artigo 21, § 3º da Lei 8.880/94

* * *

##### **RendaApurada** `U:U`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaApurada)=1;"Renda Apurada";IF(ROW(RendaApurada)<=TotalCompetencias+2;ROUNDDOWN(SalarioBeneficioLimitado*Coeficiente;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica a evolução do valor do salário-de-benefício, com aplicação do coeficiente devido

* * *

##### **RendaInformadaLimitada** `W:W`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaInformadaLimitada)=1;"Renda Inform. Lim.";IF(ROW(RendaInformadaLimitada)<=TotalCompetencias+2;IF(RendaInformadaReajustada>Teto;Teto;IF(RendaInformadaReajustada<Piso;Piso;RendaInformadaReajustada));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores da renda mensal, observados os limites mínimo e máximo

* * *

##### **RendaInformadaReajustada** `V:V`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaInformadaReajustada)=1;"Renda Inform. Reaj.";IF(ROW(RendaInformadaReajustada)<=TotalCompetencias+2;IF(ISNUMBER(RendaAtualArt58);IF(ROW(RendaInformadaReajustada)=2;RMIArt58;IF(ROW(RendaInformadaReajustada)<LinhaEquivalenciaSalarial-1;0;  jef_EVOLUCAO_RENDA(RendaAtualArt58;OFFSET(FatorReajuste;0;0;TotalCompetencias+2))));jef_EVOLUCAO_RENDA(RendaInformada;OFFSET(FatorReajuste;0;0;TotalCompetencias+2)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica a evolução do valor da RMI devida

* * *

##### **RendaMensalDevida** `Z:Z`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaMensalDevida)=1;"Renda Devida";IF(ROW(RendaMensalDevida)<=TotalCompetencias+2;IF(ROW(RendaMensalDevida)=TotalCompetencias+2;RendaMensalEfetiva+Adicional25;IF(ROW(RendaMensalDevida)=LinhaConversao;RendaNaConversaoProporcional+Adicional25;(RendaMensalEfetiva*ProporcaoRenda)+Adicional25));"")))
{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores referentes às rendas mensais, bem como suas proporções

* * *

##### **RendaMensalEfetiva** `X:X`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RendaMensalEfetiva)=1;"Renda Efetiva";IF(ROW(RendaMensalEfetiva)<=TotalCompetencias+2;IF(MID(CriterioReajuste;1;1)="1";RendaInformadaLimitada;IF(MID(CriterioReajuste;1;1)="2";RendaApurada;IF(Competencia<EOMONTH(DIBDerivado;-1)+1;RendaInformadaLimitada;IF(Competencia>EOMONTH(DIBDerivado;-1)+1;RendaApurada;RendaNaConversao))));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores das rendas mensais a serem consideradas, observando eventual conversão de benefício

* * *

##### **RevisaoArt58** `P:P`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(RevisaoArt58)=1;"Revisão Art. 58";IF(ROW(RevisaoArt58)<=TotalCompetencias+1;IF(ISNUMBER(RendaAtualArt58);IF(Competencia=(EOMONTH(DIBArt58;-1)+1);RMIArt58;IF(Competencia=DATE(1991;12;1);RendaAtualArt58;IF(Competencia<DATE(1991;12;1);0;0))));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos meses em que o benefício será recuperado pela equivalência salarial (dezembro/91)

* * *

##### **SalarioBeneficioLimitado** `R:R`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBeneficioLimitado)=1;"Sal. Limitado";IF(ROW(SalarioBeneficioLimitado)<=TotalCompetencias+2;IF(SalarioBeneficioReajustado>Teto;Teto;IF(SalarioBeneficioReajustado<Piso;Piso;SalarioBeneficioReajustado));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente ao valor do salário-de-benefício evoluído, observados os limites mínimo e máximo

* * *

##### **SalarioBeneficioReajustado** `Q:Q`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBeneficioReajustado)=1;"Sal. Reajustado";IF(ROW(SalarioBeneficioReajustado)<=TotalCompetencias+2;IF(ISNUMBER(RendaAtualArt58);IF(ROW(SalarioBeneficioReajustado)=2;RMIArt58;IF(ROW(SalarioBeneficioReajustado)<LinhaEquivalenciaSalarial-1;0;  jef_EVOLUCAO_RENDA(RendaAtualArt58;OFFSET(FatorReajuste;0;0;TotalCompetencias+2))));jef_EVOLUCAO_RENDA(SalarioBeneficio;OFFSET(FatorReajuste;0;0;TotalCompetencias+2)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente ao valor do salário-de-benefício evoluído com base nos fatores de reajuste

* * *

##### **Teto** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Teto)=1;"Teto";IF(ROW(Teto)<=TotalCompetencias+2;IF(ISNUMBER(TetoModificado);TetoModificado;{"";OFFSET(TetoBeneficio;LinhaInicialTabelaIndices-1;0;TotalCompetencias+2)});""))){% endhighlight %}


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

##### **TotalAbono** `BB:BB`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalAbono)=1;"Total Abono";IF(ROW(TotalAbono)<=TotalCompetencias+1;PrincipalAbonoAtualizado+JurosAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de principal e juros sobre parcelas de abonos

* * *

##### **TotalAbonoAlcada** `BH:BH`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalAbonoAlcada)=1;"Total Abono Alçada";IF(ROW(TotalAbonoAlcada)<=TotalCompetencias+1;IF(ROW(FatorAtualizacaoAlcada)>LinhaProtocolo-1;0;IF(FatorAtualizacaoAlcada<1;ROUND(PrincipalAbono;2);ROUND(PrincipalAbono*FatorAtualizacaoAlcada;2)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Incluída restrição referente à redução do valor nominal (Alterado em 08/11/2017)
Incluída restrição referente às parcelas posteriores à data do protocolo (Alterado em 21/02/2018)

* * *

##### **TotalJuros** `AZ:AZ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalJuros)=1;"Total Juros";IF(ROW(TotalJuros)<=TotalCompetencias+1;JurosRenda+JurosAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de juros sobre parcelas de rendas mensais e abonos

* * *

##### **TotalJurosAcordo** `BP:BP`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalJurosAcordo)=1;"Juros Total Acordo";IF(ROW(TotalJurosAcordo)<=TotalCompetencias+1;ROUND(PercentualAcordo*IF(RenunciaOpcao="Sim";TotalJurosAposRenuncia;TotalJuros);2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalJurosAposRenuncia** `BM:BM`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalJurosAposRenuncia)=1;"Juros Total Atualizado com Renúncia";IF(ROW(TotalJurosAposRenuncia)<=TotalCompetencias+1;ROUND(TotalJuros*ProporcaoAposRenuncia;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalMes** `BC:BC`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalMes)=1;"Total Mês";IF(ROW(TotalMes)<=TotalCompetencias+1;TotalRenda+TotalAbono;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de principal e juros sobre parcelas de rendas mensais e abonos

* * *

##### **TotalMesAcordo** `BQ:BQ`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalMesAcordo)=1;"Total Mês Acordo";IF(ROW(TotalMesAcordo)<=TotalCompetencias+1;PrincipalTotalAtualizadoAcordo+TotalJurosAcordo;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalMesAposRenuncia** `BN:BN`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalMesAposRenuncia)=1;"Total Mês Após Renúncia";IF(ROW(TotalMesAposRenuncia)<=TotalCompetencias+1;PrincipalTotalAtualizadoAposRenuncia+TotalJurosAposRenuncia;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores mensais atualizados até a data do ajuizamento da ação

* * *

##### **TotalRenda** `BA:BA`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalRenda)=1;"Total Renda";IF(ROW(TotalRenda)<=TotalCompetencias+1;PrincipalRendaAtualizado+JurosRenda;""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz correspondente aos valores de principal e juros sobre parcelas de renda mensal

* * *

##### **TotalRendaAlcada** `BF:BF`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TotalRendaAlcada)=1;"Total Renda Alçada";IF(ROW(TotalRendaAlcada)<=TotalCompetencias+1;IF(ROW(FatorAtualizacaoAlcada)>LinhaProtocolo-1;0;IF(FatorAtualizacaoAlcada<1;ROUND(PrincipalRenda;2);ROUND(PrincipalRenda*FatorAtualizacaoAlcada;2)));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Incluída restrição referente à redução do valor nominal (Alterado em 08/11/2017)

* * *

##### **ValorQuota** `AG:AG`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ValorQuota)=1;"Valor da Quota";IF(ROW(ValorQuota)<=TotalCompetencias+2;RendaMensalDevida*IF(ISNUMBER(QuotaRendaMensal);QuotaRendaMensal;1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Matriz que indica os valores referentes às rendas devidas, com aplicação de quota percentual