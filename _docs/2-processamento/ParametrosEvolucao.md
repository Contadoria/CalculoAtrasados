---
title: ParametrosEvolucao
category: Processamento
order: 1
---

##### **AbonoMaior15Dias** `B23`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(LimitacaoCalculoAbono);LimitacaoCalculoAbono;DataFinalDiferencas)-DataReferenciaAbono>=15{% endhighlight %}


~~~
#,##0
~~~




* * *

##### **Adicional25PrimeiraCompetencia** `B34`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF((MONTH(DataInicioAdicional25)=MONTH(DIBDerivado))*(YEAR(DataInicioAdicional25)=YEAR(DIBDerivado));IF(DAY(DataInicioAdicional25)>=DAY(DIBDerivado);VLOOKUP(EOMONTH(DataInicioAdicional25;-1)+1;{Competencia\RendaApurada};2)*0,25/30*MAX(30-DAY(DataInicioAdicional25)+1;1);VLOOKUP(EOMONTH(DataInicioAdicional25;-1)+1;{Competencia\RendaInformadaLimitada};2)*0,25/30*(DAY(DIBDerivado)-DAY(DataInicioAdicional25))+VLOOKUP(EOMONTH(DataInicioAdicional25;-1)+1;{Competencia\RendaApurada};2)*0,25/30*MAX(30-DAY(DIBDerivado)+1;1));ROUNDDOWN(IF(DataInicioAdicional25;VLOOKUP(EOMONTH(DataInicioAdicional25;-1)+1;{Competencia\RendaApurada};2)/30;"")*MAX(30-DAY(DataInicioAdicional25)+1;1)*0,25;2)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **AlcadaAjuizamento** `E9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(Piso;LinhaProtocolo)*60{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor correspondente a sessenta salários-mínimos na data do ajuizamento da ação

* * *

##### **CalcularAbono** `B17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=AND(MID(EspecieOriginario;1;2)<>"87";MID(EspecieOriginario;1;2)<>"88";MID(EspecieOriginario;1;2)<>"95"){% endhighlight %}


~~~
0.00
~~~


> Verificação se deve ser calculado o abono para o benefício especificado

* * *

##### **CompetenciaFinal** `B3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MAX(DATE(YEAR(DataAtualizacao);MONTH(DataAtualizacao)-1;1);DATE(YEAR(DataFinalDiferencas);MONTH(DataFinalDiferencas);1)){% endhighlight %}


~~~
mm"/"yyyy
~~~


> Mês anterior à data da atualização (DataAtualizacao)
Possibilidade de serem incluídas competências posteriores ao mês anterior à data de atualização do cálculo (Alterado em 07/11/2017)

* * *

##### **CompetenciaInicial** `B2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DDA);DATE(YEAR(DDA);MONTH(DDA);1);IF(ISNUMBER(DIBOriginario);DATE(YEAR(DIBOriginario);MONTH(DIBOriginario);1);)){% endhighlight %}


~~~
mm"/"yyyy
~~~


> Mês referente à data do início do benefício originário (DIBOriginario) ou do direito adquirido (apenas se houver DDA)

* * *

##### **CompetenciasDiferencas** `B5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(EOMONTH(DataInicioDiferencas;-1)+1;EOMONTH(DataFinalDiferencas;-1)+1;"M")+1{% endhighlight %}



> Número de meses (competências)  entre a data de início das diferenças (DataInicioDiferencas) e final das diferenças (DataFinalDiferencas)
Retificação para comparar o dia primeiro do mês (alterado em 30/11/2017)

* * *

##### **DataInicioIPCAE** `B36`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DataInicioIPCAEInformada);IF(CompetenciaInicial>DataInicioIPCAEInformada;CompetenciaInicial;IF(DAY(DataInicioIPCAEInformada)=1;DataInicioIPCAEInformada;EOMONTH(DataInicioIPCAEInformada;0)+1));""){% endhighlight %}


~~~
dd/MM/yyyy
~~~




* * *

##### **DataReferenciaAbono** `B19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DataInicioDiferencas{% endhighlight %}


~~~
dd"/"mm"/"yyyy
~~~


> Termo inicial considerado para cálculo do abono

* * *

##### **FatorAtualizacaoHonorarios** `E25`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=PRODUCT(FILTER(IndiceCondenatorias;CompetenciaIndices>=HonorariosSucumbenciaisDataApuracao;CompetenciaIndices<DataAtualizacao)){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000)[Red];-
~~~




* * *

##### **HonorariosContratuaisExercicioCorrente** `E41`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=HonorariosContratuaisValorTotal-HonorariosContratuaisExerciciosAnteriores{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Parcela dos honorários correspondente ao exercício corrente

* * *

##### **HonorariosContratuaisExerciciosAnteriores** `E40`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ROUND((HonorariosContratuaisValorTotal/(MesesExerciciosAnteriores+MesesExercicioCorrente))*MesesExerciciosAnteriores;2){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Parcela dos honorários correspondente ao exercícios anteriores

* * *

##### **HonorariosContratuaisJuros** `E30`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=HonorariosContratuaisValorTotal-HonorariosContratuaisPrincipal{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor discriminado dos juros referente aos honorários contratuais

* * *

##### **HonorariosContratuaisPrincipal** `E29`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(HonorariosContratuaisLimite>0;MIN(ROUND(HonorariosContratuaisBasePrincipal*HonorariosContratuaisPercentual;2);ROUND(HonorariosContratuaisBasePrincipal*HonorariosContratuaisPercentual*HonorariosContratuaisPercentualLimite;2));ROUND(HonorariosContratuaisBasePrincipal*HonorariosContratuaisPercentual;2)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor discriminado do principal referente aos honorários contratuais

* * *

##### **HonorariosContratuaisValorTotal** `E31`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(HonorariosContratuaisLimite>0;MIN(ROUND((HonorariosContratuaisBasePrincipal+HonorariosContratuaisBaseJuros)*HonorariosContratuaisPercentual;2);HonorariosContratuaisLimite);ROUND((HonorariosContratuaisBasePrincipal+HonorariosContratuaisBaseJuros)*HonorariosContratuaisPercentual;2)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total referente aos honorários contratuais

* * *

##### **HonorariosSucumbenciaisTotal** `E24`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(OpcaoHonorarios;1;1)="3";HonorariosSucumbenciaisBaseIncidencia*FatorAtualizacaoHonorarios*HonorariosSucumbenciaisPercentual;IF(HonorariosSucumbenciaisLimite>0;MIN(HonorariosSucumbenciaisBaseIncidencia*HonorariosSucumbenciaisPercentual;HonorariosSucumbenciaisLimite);HonorariosSucumbenciaisBaseIncidencia*HonorariosSucumbenciaisPercentual)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor correspondente aos honorários sucumbenciais

* * *

##### **JurosAbonoSoma** `B47`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(JurosAbono){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total dos juros aplicados sobre os abonos

* * *

##### **JurosRendaSoma** `B46`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(JurosRenda){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total dos juros aplicados sobre as rendas mensais

* * *

##### **JurosTotalSoma** `B48`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalJuros){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total dos juros aplicados sobre rendas mensais e abonos

* * *

##### **LimitacaoCalculoAbono** `B20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MONTH(DataFinalDiferencas)=12;DataFinalDiferencas;IF(DIBDerivado;IF(ISNUMBER(DCBDerivado);DCBDerivado;"");IF(ISNUMBER(DCBOriginario);DCBOriginario;""))){% endhighlight %}


~~~
dd"/"mm"/"yyyy
~~~


> Limitação do cálculo do abono decorrente de cessação de benefício

* * *

##### **LinhaAtualizacao** `B9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(MATCH(EOMONTH(DataAtualizacao;-1)+1;Competencia;0));MATCH(EOMONTH(DataAtualizacao;-1)+1;Competencia;0);(MATCH(EOMONTH(CompetenciaFinal;-1)+1;Competencia;0))+1){% endhighlight %}


~~~
0.###############
~~~


> Criada linha da aba Evolução correspondente ao mês da atualização na coluna Competencias (criado em 08/11/2017)

* * *

##### **LinhaCitacao** `B7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(MATCH(EOMONTH(Citacao;-1)+1;Competencia;0));MATCH(EOMONTH(Citacao;-1)+1;Competencia;0);IF(EOMONTH(Citacao;-1)+1>=DataAtualizacao;TotalCompetencias+2;0)){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês da citação na coluna competências. 

* * *

##### **LinhaConversao** `B10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);MATCH(EOMONTH(DIBDerivado;-1)+1;Competencia;0);0){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **LinhaEquivalenciaSalarial** `B40`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IFERROR(MATCH(DATE(1992;1;1);Competencia;0);""){% endhighlight %}


~~~
0.###############
~~~


> Linha correspondente ao mês de aplicação da equivalência salarial (janeiro/92)

* * *

##### **LinhaInicialTabelaDescontos** `B13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaDescontos;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da tabela de descontos correspondente à competência inicial

* * *

##### **LinhaInicialTabelaIndices** `B11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaIndices;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da tabela de índices correspondente à competência inicial

* * *

##### **LinhaInicialTabelaModificadores** `B12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaModificadores;0){% endhighlight %}


~~~
0.###############
~~~


> Linha da tabela de modificadores correspondente à competência inicial

* * *

##### **LinhaPrimeiraCompetencia** `B26`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente à competência inicial

* * *

##### **LinhaPrimeiraDataBase** `B27`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISERR(MATCH(TRUE();Reajustar;0));;MATCH(TRUE();Reajustar;0)){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês do primeiro reajuste do benefício

* * *

##### **LinhaPrimeiroAbono** `B21`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
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

##### **LinhaReajusteLei8870** `B28`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ISNUMBER(IndiceTeto);DIBOriginario>=DATE(1991;4;5);DIBOriginario<=DATE(1993;12;31));IFERROR(MATCH(DATE(1994;4;1);Competencia;0);0);0){% endhighlight %}


~~~
0.###############
~~~


> Linha da aba Evolução correspondente ao mês de aplicação do índice de reposição ao que excedeu o teto conforme Lei 8.870/994 (abril/94)

* * *

##### **LinhaReajusteLei8880** `B29`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ISNUMBER(IndiceTeto);DIBOriginario>=DATE(1994;1;1));LinhaPrimeiraDataBase;0){% endhighlight %}



> Linha da aba Evolução correspondente ao mês de aplicação do índice de reposição ao que excedeu o teto conforme Lei 8.880/994 (primeiro reajuste do benefício)

* * *

##### **LinhaReferenciaAbono** `B18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(EOMONTH(DataInicioDiferencas;-1)+1;Competencia;0)-1{% endhighlight %}


~~~
#,##0
~~~


> Linha da aba Evolução correspondente ao termo inicial para cálculo do primeiro abono

* * *

##### **MesesExercicioCorrente** `E37`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=COUNTIFS(Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);PrincipalRenda;">0")+COUNTIFS(Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);PrincipalAbono;">0"){% endhighlight %}



> Número de meses considerados para efeito de RRA (exercício corrente)

* * *

##### **MesesExerciciosAnteriores** `E34`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
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

##### **ParcelaLiquidaExercicioCorrente** `E43`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=TotalExercicioCorrente-HonorariosContratuaisExercicioCorrente{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Parcela correspondente ao exercício corrente, descontados valores referentes aos honorários contratuais

* * *

##### **ParcelaLiquidaExerciciosAnteriores** `E42`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
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

##### **ParcelaRenunciaExerciciosAnteriores** `E35`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(YEAR(Protocolo)=YEAR(DataAtualizacao);0;ParcelaRenunciaAtualizada){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **PercentualVencidasAposRenuncia** `E11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(PrestacoesVencidasAjuizamento>0;MIN(1;PrestacoesVencidasAjuizamentoAposRenuncia/PrestacoesVencidasAjuizamento);1){% endhighlight %}


~~~
#,##0.00000;(#,##0.00000)[Red];-
~~~


> Correção da parte final da fórmula.
Substituição de "PrestacoesVincendasAjuizamento" por "PrestacoesVencidasAjuizamento"
Em 23/01/2018

Adicionada situação em que não há parcelas vencidas (evitando divisão por zero)
Em 08/02/2018

* * *

##### **PrestacoesVencidasAjuizamento** `E6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalAlcada){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor das prestações vencidas até o mês anterior à data do ajuizamento

* * *

##### **PrestacoesVencidasAjuizamentoAposRenuncia** `E10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AlcadaAjuizamento<PrestacoesVincendasAjuizamento;0;IF(ValorDaCausa>=AlcadaAjuizamento;IF(MID(CriterioAlcada;1;1)="2";AlcadaAjuizamento;AlcadaAjuizamento-PrestacoesVincendasAjuizamento);PrestacoesVencidasAjuizamento)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Adicionada condição para o caso do valor das prestações vincendas superar o valor de alçada
Em 23/01/2018

* * *

##### **PrestacoesVincendasAjuizamento** `E7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(NaturezaAcao;1;1)="2";(INDEX(RendaMensalDevida;LinhaProtocolo)-INDEX(DescontoRenda;LinhaProtocolo))*12;INDEX(RendaMensalDevida;LinhaProtocolo)*12){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor das doze parcelas vincendas (integralmente)

* * *

##### **PrincipalAbonoSoma** `B44`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalAbonoAtualizado){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total do principal referente aos abonos

* * *

##### **PrincipalRendaSoma** `B43`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalRendaAtualizado){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total do principal referente às rendas mensais

* * *

##### **PrincipalTotalSoma** `B45`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(PrincipalTotalAtualizado){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor total do principal referente às rendas mensais e abonos

* * *

##### **ProporcaoFinal** `B15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(TotalCompetenciasDiferencas=1;((MIN(30;DAY(DataFinalDiferencas))-DAY(DataInicioDiferencas))+1)/30;IF(MONTH(EOMONTH(DataFinalDiferencas;0))=2;IF(DAY(DataFinalDiferencas)>27;1;MIN(30;DAY(DataFinalDiferencas))/30);MIN(30;DAY(DataFinalDiferencas))/30)){% endhighlight %}


~~~
0.00
~~~


> Proporção da renda mensal referente ao último mês calculado

* * *

##### **ProporcaoInicial** `B14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(TotalCompetenciasDiferencas=1;((MIN(30;DAY(DataFinalDiferencas))-DAY(DataInicioDiferencas))+1)/30;MAX(1;30-(DAY(DataInicioDiferencas)-1))/30){% endhighlight %}


~~~
0.00
~~~


> Proporção da renda mensal referente ao primeiro mês calculado

* * *

##### **ProporcaoInicioBeneficioDerivado** `B16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);((MIN(30;DAY(DIBDerivado))/30)*IF(ISNUMBER(CoeficienteOriginario);CoeficienteOriginario;1))+((MAX(1;30-(DAY(DIBDerivado-1)))/30)*IF(ISNUMBER(CoeficienteDerivado);CoeficienteDerivado;1));1){% endhighlight %}


~~~
0.00
~~~


> Proporção da renda mensal referente ao mês da conversão em benefício derivado

* * *

##### **ProporcaoPrimeiroAbono** `B24`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MIN(1;(((LinhaPrimeiroAbono-LinhaReferenciaAbono)-IF(DAY(DataReferenciaAbono)<=16;0;1)-IF(LinhaPrimeiroAbono=UltimaLinhaAbono;IF(DAY(LimitacaoCalculoAbono)>=15;0;1);0))/12)*AbonoMaior15Dias){% endhighlight %}


~~~
#,##0.00
~~~


> Ajuste referente a quantos dias são necessários para computar o primeiro mês para efeito de décimo terceiro salário (alterado em 22/11/2017)

* * *

##### **ProporcaoUltimoAbono** `B25`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=((UltimaLinhaAbono-MAX(LARGE(filter(LinhasAbono;LinhasAbono<>UltimaLinhaAbono);1);LinhaReferenciaAbono)-IF(DAY(LimitacaoCalculoAbono)>=15;0;1))/12)*AbonoMaior15Dias{% endhighlight %}


~~~
#,##0.00
~~~


> Proporção referente ao último abono calculado

* * *

##### **RMA** `B35`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(IF(MID(CriterioReajuste;1;1)="1";RendaInformadaLimitada;RendaApurada);MATCH(EOMONTH(DataFinalDiferencas;-1)+1;Competencia;0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da renda mensal atual

* * *

##### **RMIDerivado** `B31`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);INDEX(RendaApurada;MATCH(EOMONTH(DIBDerivado;-1)+1;Competencia;0));""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Renda mensal inicial apurada do benefício derivado com base na evolução do salário-de-benefício e aplicado coeficiente de cálculo


* * *

##### **RMIOriginario** `B30`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(RendaMensalEfetiva;MATCH(EOMONTH(DIBOriginario;-1)+1;Competencia;0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Renda mensal inicial do benefício originário, observados limites mínimo e máximo

* * *

##### **RendaAtualArt58** `B39`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(EquivalenciaArt58);EquivalenciaArt58*INDEX(SalarioMinimo;MATCH(DATE(1991;12;1);CompetenciaIndices;0));""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da renda em dezembro/91, observada a equivalência salarial e o valor do salário-mínimo

* * *

##### **RendaNaConversao** `B32`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);IF(DAY(DIBDerivado)=1;RMIDerivado;(((INDEX(RendaInformadaLimitada;MATCH(EOMONTH(DIBDerivado;-1)+1;Competencia;0)))/30)*DAY(DCBOriginario))+((RMIDerivado/30)*MAX(30-DAY(DIBDerivado)+1;1)));""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor da renda mensal no mês da conversão de benefício, consideradas as proporções

* * *

##### **RendaNaConversaoProporcional** `B33`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF((MONTH(DataInicioDiferencas)=MONTH(DIBDerivado))*(YEAR(DataInicioDiferencas)=YEAR(DIBDerivado));IF(DAY(DataInicioDiferencas)>=DAY(DIBDerivado);
VLOOKUP(EOMONTH(DataInicioDiferencas;-1)+1;{Competencia\RendaApurada};2)/30*MAX(30-DAY(DataInicioDiferencas)+1;1);VLOOKUP(EOMONTH(DataInicioDiferencas;-1)+1;
{Competencia\RendaInformadaLimitada};2)/30*(DAY(DIBDerivado)-DAY(DataInicioDiferencas))+VLOOKUP(EOMONTH(DataInicioDiferencas;-1)+1;
{Competencia\RendaApurada};2)/30*MAX(30-DAY(DIBDerivado)+1;1));VLOOKUP(EOMONTH(DIBDerivado;-1)+1;
{Competencia\RendaMensalEfetiva};2)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RenunciaExerciciosAnteriores** `E35`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(YEAR(Protocolo)=YEAR(DataAtualizacao);0;ParcelaRenunciaAtualizada){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalAbonoSoma** `B50`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
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
{% highlight erlang %}=DATEDIF(EOMONTH(DataInicioDiferencas;-1)+1;EOMONTH(DataFinalDiferencas;-1)+1;"M")+1{% endhighlight %}



> Número de meses (competências)  entre a data de início das diferenças (DataInicioDiferencas) e final das diferenças (DataFinalDiferencas)
Retificação para comparar o dia primeiro do mês (alterado em 30/11/2017)

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

##### **TotalExercicioCorrente** `E39`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(RenunciaOpcao="Sim";SUMIF(Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);IF(ISNUMBER(PercentualAcordo);TotalMesAcordo;TotalMesAposRenuncia));SUMIF(Competencia;">="&DATE(YEAR(DataAtualizacao);1;1);IF(ISNUMBER(PercentualAcordo);TotalMesAcordo;TotalMes))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valores considerados para efeito de RRA (exercício corrente).
Computados valores negativos para (alteração em 30/10/17)

* * *

##### **TotalExerciciosAnteriores** `E36`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(RenunciaOpcao="Sim";SUMIF(Competencia;"<"&DATE(YEAR(DataAtualizacao);1;1);IF(ISNUMBER(PercentualAcordo);TotalMesAcordo;TotalMesAposRenuncia));SUMIF(Competencia;"<"&DATE(YEAR(DataAtualizacao);1;1);IF(ISNUMBER(PercentualAcordo);TotalMesAcordo;TotalMes))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valores considerados para efeito de RRA (exercícios anteriores).
Computados valores negativos para (alteração em 30/10/17)

* * *

##### **TotalGeral** `B51`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalMes){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Valor do total geral (principal e juros de mora das rendas mensais e abonos)

* * *

##### **TotalRendaSoma** `B49`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalRenda){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Soma dos valores principais e dos juros de mora referentes às rendas mensais

* * *

##### **UltimaLinhaAbono** `B22`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MAX(ARRAYFORMULA(IF(LinhasAbono>0;LinhasAbono;""))){% endhighlight %}


~~~
#,##0
~~~


> Linha da aba Evolução correspondente ao mês do último abono a ser calculado

* * *

##### **ValorCondenacaoAposRenuncia** `B52`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(TotalMesAposRenuncia){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **ValorDaCausa** `E8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(CriterioAlcada;1;1)="2";PrestacoesVencidasAjuizamento;IF(MID(CriterioAlcada;1;1)="3";PrestacoesVincendasAjuizamento;IF(MID(CriterioAlcada;1;1)="4";0;PrestacoesVincendasAjuizamento+PrestacoesVencidasAjuizamento))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


