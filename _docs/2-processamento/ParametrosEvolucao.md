---
title: ParametrosEvolucao
category: Processamento
order: 1
---

##### **AbonoMaior15Dias** `B21`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(LimitacaoCalculoAbono);LimitacaoCalculoAbono;DataFinalDiferencas)-DataReferenciaAbono>=15{% endhighlight %}


~~~
#,##0
~~~




* * *

##### **AlcadaAjuizamento** `E9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(Piso;LinhaProtocolo)*60{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor correspondente a sessenta salários-mínimos na data do ajuizamento da ação

* * *

##### **CalcularAbono** `B15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=AND(MID(EspecieOriginario;1;2)<>"87";MID(EspecieOriginario;1;2)<>"88";MID(EspecieOriginario;1;2)<>"95"){% endhighlight %}


~~~
0.00
~~~


> Verificação se deve ser calculado o abono para o benefício especificado

* * *

##### **CompetenciaFinal** `B3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATE(YEAR(DataAtualizacao);MONTH(DataAtualizacao)-1;1){% endhighlight %}


~~~
mm"/"yyyy
~~~


> Mês anterior à data da atualização (DataAtualizacao)

* * *

##### **CompetenciaInicial** `B2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DDA);DATE(YEAR(DDA);MONTH(DDA);1);IF(ISNUMBER(DIBOriginario);DATE(YEAR(DIBOriginario);MONTH(DIBOriginario);1);)){% endhighlight %}


~~~
mm"/"yyyy
~~~


> Mês referente à data do início do benefício originário (DIBOriginario) ou do direito adquirido (apenas se houver DDA)

* * *

##### **CompetenciasDiferencas** `B5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(DataInicioDiferencas;DataFinalDiferencas;"M")+1{% endhighlight %}



> Número de meses (competências)  entre a data de início das diferenças (DataInicioDiferencas) e final das diferenças (DataFinalDiferencas)

* * *

##### **DataReferenciaAbono** `B17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DataInicioDiferencas{% endhighlight %}


~~~
dd"/"mm"/"yyyy
~~~


> Termo inicial considerado para cálculo do abono

* * *

##### **HonorariosContratuaisExercicioCorrente** `E36`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=HonorariosContratuaisValorTotal-HonorariosContratuaisExerciciosAnteriores{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Parcela dos honorários correspondente ao exercício corrente

* * *

##### **HonorariosContratuaisExerciciosAnteriores** `E35`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ROUND((HonorariosContratuaisValorTotal/(MesesExerciciosAnteriores+MesesExercicioCorrente))*MesesExerciciosAnteriores;2){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Parcela dos honorários correspondente ao exercícios anteriores

* * *

##### **HonorariosContratuaisJuros** `E25`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=HonorariosContratuaisValorTotal-HonorariosContratuaisPrincipal{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor discriminado dos juros referente aos honorários contratuais

* * *

##### **HonorariosContratuaisPrincipal** `E24`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(HonorariosContratuaisLimite>0;MIN(ROUND(HonorariosContratuaisBasePrincipal*HonorariosContratuaisPercentual;2);ROUND(HonorariosContratuaisBasePrincipal*HonorariosContratuaisPercentual*HonorariosContratuaisPercentualLimite;2));ROUND(HonorariosContratuaisBasePrincipal*HonorariosContratuaisPercentual;2)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor discriminado do principal referente aos honorários contratuais

* * *

##### **HonorariosContratuaisValorTotal** `E26`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(HonorariosContratuaisLimite>0;MIN(ROUND((HonorariosContratuaisBasePrincipal+HonorariosContratuaisBaseJuros)*HonorariosContratuaisPercentual;2);HonorariosContratuaisLimite);ROUND((HonorariosContratuaisBasePrincipal+HonorariosContratuaisBaseJuros)*HonorariosContratuaisPercentual;2)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total referente aos honorários contratuais

* * *

##### **HonorariosSucumbenciaisTotal** `E20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(HonorariosSucumbenciaisLimite>0;MIN(HonorariosSucumbenciaisBaseIncidencia*HonorariosSucumbenciaisPercentual;HonorariosSucumbenciaisLimite);HonorariosSucumbenciaisBaseIncidencia*HonorariosSucumbenciaisPercentual){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor correspondente aos honorários sucumbenciais

* * *

##### **JurosAbonoSoma** `B42`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(JurosAbono){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total dos juros aplicados sobre os abonos

* * *

##### **JurosRendaSoma** `B41`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(JurosRenda){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total dos juros aplicados sobre as rendas mensais

* * *

##### **JurosTotalSoma** `B43`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalJuros){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total dos juros aplicados sobre rendas mensais e abonos

* * *

##### **LimitacaoCalculoAbono** `B18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DIBDerivado;IF(ISNUMBER(DCBDerivado);DCBDerivado;"");IF(ISNUMBER(DCBOriginario);DCBOriginario;"")){% endhighlight %}


~~~
dd"/"mm"/"yyyy
~~~


> Limitação do cálculo do abono decorrente de cessação de benefício

* * *

##### **LinhaCitacao** `B7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(MATCH(EOMONTH(Citacao;-1)+1;Competencia;0));MATCH(EOMONTH(Citacao;-1)+1;Competencia;0);IF(EOMONTH(Citacao;-1)+1>=DataAtualizacao;TotalCompetencias+2;0)){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês da citação na coluna competências. 

* * *

##### **LinhaEquivalenciaSalarial** `B35`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IFERROR(MATCH(DATE(1992;1;1);Competencia;0);""){% endhighlight %}


~~~
0.###############
~~~


> Linha correspondente ao mês de aplicação da equivalência salarial (janeiro/92)

* * *

##### **LinhaInicialTabelaDescontos** `B11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaDescontos;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da tabela de descontos correspondente à competência inicial

* * *

##### **LinhaInicialTabelaIndices** `B9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaIndices;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da tabela de índices correspondente à competência inicial

* * *

##### **LinhaInicialTabelaModificadores** `B10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaModificadores;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da tabela de modificadores correspondente à competência inicial

* * *

##### **LinhaPrimeiraCompetencia** `B24`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente à competência inicial

* * *

##### **LinhaPrimeiraDataBase** `B25`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISERR(MATCH(TRUE();Reajustar;0));;MATCH(TRUE();Reajustar;0)){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês do primeiro reajuste do benefício

* * *

##### **LinhaPrimeiroAbono** `B19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MIN(ARRAYFORMULA(IF(LinhasAbono>0;LinhasAbono;""))){% endhighlight %}


~~~
#,##0
~~~


> Linha da aba Evolução correspondente ao mês do primeiro abono a ser calculado

* * *

##### **LinhaProtocolo** `B8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(EOMONTH(Protocolo;-1)+1;Competencia;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês do ajuizamento na coluna competências. 

* * *

##### **LinhaReajusteLei8870** `B26`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ISNUMBER(IndiceTeto);DIBOriginario>=DATE(1991;4;5);DIBOriginario<=DATE(1993;12;31));IFERROR(MATCH(DATE(1994;4;1);Competencia;0);0);0){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês de aplicação do índice de reposição ao que excedeu o teto conforme Lei 8.870/994 (abril/94)

* * *

##### **LinhaReajusteLei8880** `B27`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ISNUMBER(IndiceTeto);DIBOriginario>=DATE(1994;1;1));LinhaPrimeiraDataBase;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês de aplicação do índice de reposição ao que excedeu o teto conforme Lei 8.880/994 (primeiro reajuste do benefício)

* * *

##### **LinhaReferenciaAbono** `B16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(EOMONTH(DataInicioDiferencas;-1)+1;Competencia;0)-1{% endhighlight %}


~~~
#,##0
~~~


> Linha da aba Evolução correspondente ao termo inicial para cálculo do primeiro abono

* * *

##### **MesesExercicioCorrente** `E32`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=COUNTIFS(Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);PrincipalRenda;">0")+COUNTIFS(Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);PrincipalAbono;">0"){% endhighlight %}



> Número de meses considerados para efeito de RRA (exercício corrente)

* * *

##### **MesesExerciciosAnteriores** `E29`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=COUNTIFS(Competencia;"<"&DATE(YEAR(DataAtualizacao);1;1);PrincipalRenda;">0")+COUNTIFS(Competencia;"<"&DATE(YEAR(DataAtualizacao);1;1);PrincipalAbono;">0"){% endhighlight %}



> Número de meses considerados para efeito de RRA (exercícios anteriores)

* * *

##### **ParcelaExcedenteSobreTotal** `E14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(PrestacoesVencidasAjuizamento+PrestacoesVincendasAjuizamento-AlcadaAjuizamento>0;PrestacoesVencidasAjuizamento+PrestacoesVincendasAjuizamento-AlcadaAjuizamento;0){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor que excede a alçada na data do ajuizamento (consideradas as prestações vencidas + 12 vincendas)

* * *

##### **ParcelaExcedenteSobreTotalAtualizada** `E15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ParcelaExcedenteSobreTotal*INDEX(FatorAtualizacao;LinhaProtocolo;0)*(1+INDEX(JurosAcumulados;LinhaProtocolo;0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Atualização do valor que excede a alçada na data do ajuizamento (consideradas as prestações vencidas + 12 vincendas)

* * *

##### **ParcelaExcedenteSobreVencidas** `E12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(PrestacoesVencidasAjuizamento-AlcadaAjuizamento>0;PrestacoesVencidasAjuizamento-AlcadaAjuizamento;0){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor que excede a alçada na data do ajuizamento (consideradas apenas as prestações vencidas)

* * *

##### **ParcelaExcedenteSobreVencidasAtualizada** `E13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ParcelaExcedenteSobreVencidas*INDEX(FatorAtualizacao;LinhaProtocolo;0)*(1+INDEX(JurosAcumulados;LinhaProtocolo;0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Atualização do valor que excede a alçada na data do ajuizamento (consideradas apenas as prestações vencidas)

* * *

##### **ParcelaLiquidaExercicioCorrente** `E38`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=TotalExercicioCorrente-HonorariosContratuaisExercicioCorrente{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Parcela correspondente ao exercício corrente, descontados valores referentes aos honorários contratuais

* * *

##### **ParcelaLiquidaExerciciosAnteriores** `E37`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=TotalExerciciosAnteriores-HonorariosContratuaisExerciciosAnteriores{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Parcela correspondente aos exercícios anteriores, descontados valores referentes aos honorários contratuais

* * *

##### **ParcelaRenunciaAjuizamento** `E16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(CriterioAlcada;1;1)="1";ParcelaExcedenteSobreTotal;ParcelaExcedenteSobreVencidas){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor de renúncia na data do ajuizamento, considerando o critério escolhido

* * *

##### **ParcelaRenunciaAtualizada** `E17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(CriterioAlcada;1;1)="1";TotalGeral-ValorCondenacaoAposRenuncia;ParcelaExcedenteSobreVencidasAtualizada){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor de renúncia atualizado, considerando o critério escolhido

* * *

##### **ParcelaRenunciaExerciciosAnteriores** `E30`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(YEAR(Protocolo)=YEAR(DataAtualizacao);0;ParcelaRenunciaAtualizada){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **PercentualVencidasAposRenuncia** `E11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MIN(1;PrestacoesVencidasAjuizamentoAposRenuncia/PrestacoesVencidasAjuizamento){% endhighlight %}


~~~
#,##0.00000;(#,##0.00000)[Red];-
~~~




* * *

##### **PrestacoesVencidasAjuizamento** `E6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalAlcada){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor das prestações vencidas até o mês anterior à data do ajuizamento

* * *

##### **PrestacoesVencidasAjuizamentoAposRenuncia** `E10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ValorDaCausa>=AlcadaAjuizamento;AlcadaAjuizamento-PrestacoesVincendasAjuizamento;PrestacoesVincendasAjuizamento){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **PrestacoesVincendasAjuizamento** `E7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(NaturezaAcao;1;1)="1";INDEX(RendaMensalDevida;LinhaProtocolo)*12;INDEX(PrincipalRenda;LinhaProtocolo)*12){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor das doze parcelas vincendas (integralmente)

* * *

##### **PrincipalAbonoSoma** `B39`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalAbonoAtualizado){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total do principal referente aos abonos

* * *

##### **PrincipalRendaSoma** `B38`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalRendaAtualizado){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total do principal referente às rendas mensais

* * *

##### **PrincipalTotalSoma** `B40`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalTotalAtualizado){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total do principal referente às rendas mensais e abonos

* * *

##### **ProporcaoFinal** `B13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(TotalCompetenciasDiferencas=1;((MIN(30;DAY(DataFinalDiferencas))-DAY(DataInicioDiferencas))+1)/30;IF(MONTH(EOMONTH(DataFinalDiferencas;0))=2;IF(DAY(DataFinalDiferencas)>27;1;MIN(30;DAY(DataFinalDiferencas))/30);MIN(30;DAY(DataFinalDiferencas))/30)){% endhighlight %}


~~~
0.00
~~~


> Proporção da renda mensal referente ao último mês calculado

* * *

##### **ProporcaoInicial** `B12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(TotalCompetenciasDiferencas=1;((MIN(30;DAY(DataFinalDiferencas))-DAY(DataInicioDiferencas))+1)/30;MAX(1;30-(DAY(DataInicioDiferencas)-1))/30){% endhighlight %}


~~~
0.00
~~~


> Proporção da renda mensal referente ao primeiro mês calculado

* * *

##### **ProporcaoInicioBeneficioDerivado** `B14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);((MIN(30;DAY(DIBDerivado))/30)*IF(ISNUMBER(CoeficienteOriginario);CoeficienteOriginario;1))+((MAX(1;30-(DAY(DIBDerivado-1)))/30)*IF(ISNUMBER(CoeficienteDerivado);CoeficienteDerivado;1));1){% endhighlight %}


~~~
0.00
~~~


> Proporção da renda mensal referente ao mês da conversão em benefício derivado

* * *

##### **ProporcaoPrimeiroAbono** `B22`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MIN(1;(((LinhaPrimeiroAbono-LinhaReferenciaAbono)-IF(DAY(DataReferenciaAbono)<=15;0;1))/12)*AbonoMaior15Dias){% endhighlight %}


~~~
#,##0.00
~~~




* * *

##### **ProporcaoUltimoAbono** `B23`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=((UltimaLinhaAbono-MAX(LARGE(filter(LinhasAbono;LinhasAbono<>UltimaLinhaAbono);1);LinhaReferenciaAbono)-IF(DAY(LimitacaoCalculoAbono)>=15;0;1))/12)*AbonoMaior15Dias{% endhighlight %}


~~~
#,##0.00
~~~


> Proporção referente ao último abono calculado

* * *

##### **RMA** `B31`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(RendaMensalEfetiva;MATCH(EOMONTH(DataFinalDiferencas;-1)+1;Competencia;0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da renda mensal atual

* * *

##### **RMIDerivado** `B29`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);INDEX(RendaApurada;MATCH(EOMONTH(DIBDerivado;-1)+1;Competencia;0));""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Renda mensal inicial apurada do benefício derivado com base na evolução do salário-de-benefício e aplicado coeficiente de cálculo


* * *

##### **RMIDerivadoNBPago** `E43`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);INDEX(RendaApuradaNBPago;MATCH(EOMONTH(DIBDerivado;-1)+1;Competencia;0));""){% endhighlight %}


~~~
0.###############
~~~


> Renda mensal inicial apurada do benefício derivado com base na evolução do salário-de-benefício e aplicado coeficiente de cálculo (benefício pago)

* * *

##### **RMIOriginario** `B28`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(RendaMensalEfetiva;MATCH(EOMONTH(DIBOriginario;-1)+1;Competencia;0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Renda mensal inicial do benefício originário, observados limites mínimo e máximo

* * *

##### **RMIOriginarioNBPago** `E42`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(RendaMensalEfetivaNBPago;MATCH(EOMONTH(DIBOriginario;-1)+1;Competencia;0)){% endhighlight %}


~~~
0.###############
~~~


> Renda mensal inicial do benefício originário, observados limites mínimo e máximo (benefício pago)



* * *

##### **RendaAtualArt58** `B34`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(EquivalenciaArt58);EquivalenciaArt58*INDEX(SalarioMinimo;MATCH(DATE(1991;12;1);CompetenciaIndices;0));""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da renda em dezembro/91, observada a equivalência salarial e o valor do salário-mínimo

* * *

##### **RendaAtualArt58NBPago** `E41`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(EquivalenciaArt58NBPago);EquivalenciaArt58NBPago*INDEX(SalarioMinimo;MATCH(DATE(1991;12;1);CompetenciaIndices;0));""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da renda em dezembro/91, observada a equivalência salarial e o valor do salário-mínimo (benefício pago)

* * *

##### **RendaNaConversao** `B30`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);(((INDEX(RendaInformadaLimitada;MATCH(EOMONTH(DIBDerivado;-1)+1;Competencia;0)))/30)*DAY(DCBOriginario))+((RMIDerivado/30)*MAX(30-DAY(DIBDerivado)+1;1));""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da renda mensal no mês da conversão de benefício, consideradas as proporções

* * *

##### **RendaNaConversaoNBPago** `E44`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);(((INDEX(RendaInformadaLimitadaNBPago;MATCH(EOMONTH(DIBDerivado;-1)+1;Competencia;0)))/30)*DAY(DCBOriginario))+((RMIDerivadoNBPago/30)*MAX(30-DAY(DIBDerivado)+1;1));""){% endhighlight %}


~~~
0.###############
~~~


> Valor da renda mensal paga no mês da conversão de benefício, consideradas as proporções

* * *

##### **RenunciaExerciciosAnteriores** `E30`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(YEAR(Protocolo)=YEAR(DataAtualizacao);0;ParcelaRenunciaAtualizada){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalAbonoSoma** `B45`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalAbono){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Soma dos valores principais e dos juros de mora referentes aos abonos

* * *

##### **TotalCompetencias** `B4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(CompetenciaInicial;CompetenciaFinal;"M")+1{% endhighlight %}



> Número de meses (competências)  entre a Competência Inicial e Competência Final

* * *

##### **TotalCompetenciasDiferencas** `B5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(DataInicioDiferencas;DataFinalDiferencas;"M")+1{% endhighlight %}



> Número de meses (competências)  entre a data de início das diferenças (DataInicioDiferencas) e final das diferenças (DataFinalDiferencas)

* * *

##### **TotalCompetenciasDiferencasAlcada** `E3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(EOMONTH(CompetenciaInicial;-1)+1;EOMONTH(Protocolo;-1)+1;"M")+1{% endhighlight %}


~~~
#,##0;(#,##0)[Red];-
~~~




* * *

##### **TotalCompetenciasJuros** `B6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(Citacao;DataAtualizacao;"M")+1{% endhighlight %}



> Total de meses entre data da citação e data da atualização

* * *

##### **TotalExercicioCorrente** `E34`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(RenunciaOpcao="Sim";SUMIFS(TotalMesAposRenuncia;Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);PrincipalTotalAtualizado;">0");SUMIFS(TotalMes;Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);PrincipalTotalAtualizado;">0")){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valores considerados para efeito de RRA (exercício corrente)

* * *

##### **TotalExerciciosAnteriores** `E31`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(RenunciaOpcao="Sim";SUMIFS(TotalMesAposRenuncia;Competencia;"<"&DATE(YEAR(DataAtualizacao);1;1);PrincipalTotalAtualizado;">0");SUMIFS(TotalMes;Competencia;"<"&DATE(YEAR(DataAtualizacao);1;1);PrincipalTotalAtualizado;">0")){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valores considerados para efeito de RRA (exercícios anteriores)

* * *

##### **TotalGeral** `B46`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalMes){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor do total geral (principal e juros de mora das rendas mensais e abonos)

* * *

##### **TotalRendaSoma** `B44`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalRenda){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Soma dos valores principais e dos juros de mora referentes às rendas mensais

* * *

##### **UltimaLinhaAbono** `B20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MAX(ARRAYFORMULA(IF(LinhasAbono>0;LinhasAbono;""))){% endhighlight %}


~~~
#,##0
~~~


> Linha da aba Evolução correspondente ao mês do último abono a ser calculado

* * *

##### **ValorCondenacaoAposRenuncia** `B47`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalMesAposRenuncia){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **ValorDaCausa** `E8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(CriterioAlcada;1;1)="2";PrestacoesVencidasAjuizamento;IF(MID(CriterioAlcada;1;1)="3";PrestacoesVincendasAjuizamento;PrestacoesVincendasAjuizamento+PrestacoesVencidasAjuizamento)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


