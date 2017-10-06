---
title: ColunasDemonstrativos
category: Processamento
order: 2
---

##### **DemonstrativoAbono** `B:B`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbono)=1;"Linhas Abono";IF(ROW(DemonstrativoAbono)<=TotalCompetencias+1;IF(Competencia<(EOMONTH(MarcoPrescricional;-1)+1);FALSE();IF(LinhasAbono>0;TRUE();IF(DescontoAbono>0;TRUE();FALSE())));""))){% endhighlight %}


~~~
0;0;-
~~~


> Fórmula Matriz (ArrayFormula) identifica por "verdadeiro" ou "falso" as linhas onde há valores a título de abono, selecionando, a partir do marco prescricional, as linhas indicadas na planilha "evolução" coluna G.

* * *

##### **DemonstrativoAbonoAlcada** `X:X`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoAlcada)=1;"Linhas Alçada";IF(ROW(DemonstrativoAbonoAlcada)<=TotalCompetencias+1;IF(Competencia>=Protocolo;FALSE();IF(DemonstrativoAbono=TRUE();TRUE();FALSE()));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
mm"/"yyyy
~~~




* * *

##### **DemonstrativoAbonoCompetencias** `N:N`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoCompetencias)=1;"Competências Abono";IF(ROW(DemonstrativoAbonoCompetencias)<=TotalCompetencias+1;IF(DemonstrativoAbono;Competencia;FALSE());""))){% endhighlight %}


~~~
mm/yyyy
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá valores de abono, indicadas por "verdadeiro" na coluna "DemonstrativoAbono", mantendo "falso" para as demais.

* * *

##### **DemonstrativoAbonoDescontos** `Q:Q`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoDescontos)=1;"Desconto Abono";IF(ROW(DemonstrativoAbonoDescontos)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;DescontoAbono;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá descontos de abono, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna AT.

* * *

##### **DemonstrativoAbonoJuros** `T:T`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoJuros)=1;"Juros Abono";IF(ROW(DemonstrativoAbonoJuros)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;JurosAbono;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá juros sobre abono, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna BI.

* * *

##### **DemonstrativoAbonoJurosAlcada** `AD:AD`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoJurosAlcada)=1;"Juros Abono Alçada";IF(ROW(DemonstrativoAbonoJurosAlcada)<=TotalCompetencias + 1;IF(DemonstrativoDiferencas;0;0);""))){% endhighlight %}


~~~
mm/yyyy
#,##0.00;(#,##0.00);-
~~~




* * *

##### **DemonstrativoAbonoPrincipal** `R:R`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoPrincipal)=1;"Principal Abono";IF(ROW(DemonstrativoAbonoPrincipal)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;PrincipalAbono;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá diferença de abono, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna AV.

* * *

##### **DemonstrativoAbonoPrincipalAtualizado** `S:S`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoPrincipalAtualizado)=1;"Principal Abono Atualizado";IF(ROW(DemonstrativoAbonoPrincipalAtualizado)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;PrincipalAbonoAtualizado;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá diferença atualizada de abono, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna BC.

* * *

##### **DemonstrativoAbonoPrincipalAtualizadoAlcada** `AC:AC`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoPrincipalAtualizadoAlcada)=1;"Principal Abono Atualizado Alçada";IF(ROW(DemonstrativoAbonoPrincipalAtualizadoAlcada)<=TotalCompetencias + 1;IF(DemonstrativoAlcada;TotalAbonoAlcada;0);""))){% endhighlight %}


~~~
mm/yyyy
#,##0.00;(#,##0.00);-
~~~




* * *

##### **DemonstrativoAbonoProporcao** `O:O`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoProporcao)=1;"Proporção Abono";IF(ROW(DemonstrativoAbonoProporcao)<=TotalCompetencias+1;IF(DemonstrativoAbono;IF(ProporcaoAbono=1;"Integral";ProporcaoAbono);0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá abono proporcional, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando a proporção correspondentes na planilha "evolução" coluna H.
Proporção igual a "1" assume "integral".

* * *

##### **DemonstrativoAbonoTotal** `U:U`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoTotal)=1;"Total Abono";IF(ROW(DemonstrativoAbonoTotal)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;TotalAbono;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá valores totais de abono, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna BL.

* * *

##### **DemonstrativoAbonoValor** `P:P`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAbonoValor)=1;"Valor Abono";IF(ROW(DemonstrativoAbonoValor)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;Abono;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá diferença principal  abono, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna AQ.

* * *

##### **DemonstrativoAlcada** `W:W`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoAlcada)=1;"Linhas Alçada";IF(ROW(DemonstrativoAlcada)<=TotalCompetencias+1;IF(Competencia>=Protocolo;FALSE();IF(DemonstrativoRenda=TRUE();TRUE();FALSE()));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
mm"/"yyyy
~~~




* * *

##### **DemonstrativoDiferencas** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoDiferencas)=1;"Linhas Diferenças";IF(ROW(DemonstrativoDiferencas)<=TotalCompetencias+1;IF(Competencia>DataFinalDiferencas;FALSE();IF(DemonstrativoRenda=TRUE();TRUE();FALSE()));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica por "verdadeiro" ou "falso" as linhas onde há valores a título de diferenças, selecionadas a partir do marco prescricional.

* * *

##### **DemonstrativoFatorAtualizacao** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoFatorAtualizacao)=1;"Fator Atualização";IF(ROW(DemonstrativoFatorAtualizacao)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;FatorAtualizacao;0);""))){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000);-
~~~


> Fórmula Matriz (ArrayFormula) identifica o fator de atualização, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os índices correspondentes na planilha "evolução" coluna BA.

* * *

##### **DemonstrativoFatorAtualizacaoAlcada** `Y:Y`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoFatorAtualizacaoAlcada)=1;"Fator Atualização Alçada";IF(ROW(DemonstrativoFatorAtualizacaoAlcada)<=TotalCompetencias + 1;IF(DemonstrativoAlcada;FatorAtualizacaoAlcada;0);""))){% endhighlight %}


~~~
mm/yyyy
#,##0.00000000;(#,##0.00000000);-
~~~




* * *

##### **DemonstrativoFatorReajuste** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoFatorReajuste)=1;"Reajuste";IF(ROW(DemonstrativoFatorReajuste)<=TotalCompetencias+1;IF(DemonstrativoRenda;IF(FatorReajuste<>1;FatorReajuste;0));""))){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000)[Red];-
#,##0.0000
~~~


> Fórmula Matriz (ArrayFormula) identifica o fator de reajuste, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoRenda", buscando os índices correspondentes na planilha "evolução" coluna Q.

* * *

##### **DemonstrativoJurosPercentual** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoJurosPercentual)=1;"Percentual Juros de Mora";IF(ROW(DemonstrativoJurosPercentual)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;JurosAcumulados;0);""))){% endhighlight %}


~~~
0.00%
~~~


> Fórmula Matriz (ArrayFormula) identifica o percentual de juros de mora, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os percentuais correspondentes na planilha "evolução" coluna BG.

* * *

##### **DemonstrativoJurosPercentualAlcada** `AA:AA`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoJurosPercentualAlcada)=1;"Percentual Juros de Mora Alçada";IF(ROW(DemonstrativoJurosPercentualAlcada)<=TotalCompetencias + 1;IF(DemonstrativoAlcada;0;0);""))){% endhighlight %}


~~~
mm/yyyy
#,##0.00;(#,##0.00);-
~~~




* * *

##### **DemonstrativoRenda** `A:A`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRenda)=1;"Linhas Renda";IF(ROW(DemonstrativoRenda)<=TotalCompetencias+1;IF(ROW(DemonstrativoRenda)=2;TRUE();IF(ISNUMBER(RendaAtualArt58);IF(Competencia=DATE(1991;12;1);TRUE();IF(Competencia<DATE(1992;1;1);FALSE();IF(Competencia<(EOMONTH(MarcoPrescricional;-1)+1);Reajustar;TRUE())));IF(Competencia<(EOMONTH(MAX(MarcoPrescricional;DataInicioDiferencas);-1)+1);Reajustar;TRUE())));""))){% endhighlight %}


~~~
#,##0.0000000000;(#,##0.0000000000)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) identifica por "verdadeiro" ou "falso" as linhas onde há valores de renda, selecionando, a partir do marco prescricional, observando também:
- competências anteriores ao marco prescricional quando do reajustamento da renda, correspondente na planilha "evolução" coluna I.



* * *

##### **DemonstrativoRendaCompetencias** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaCompetencias)=1;"Competências Renda";IF(ROW(DemonstrativoRendaCompetencias)<=TotalCompetencias+1;IF(DemonstrativoRenda;Competencia;FALSE());""))){% endhighlight %}


~~~
mm/yyyy
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá valores de renda, indicadas por "verdadeiro" na coluna "DemonstrativoRenda",
buscando as competências correspondentes na planilha "evolução" coluna A.

* * *

##### **DemonstrativoRendaDescontos** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaDescontos)=1;"Desconto Renda";IF(ROW(DemonstrativoRendaDescontos)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;DescontoRenda;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá desconto na renda, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna AS.

* * *

##### **DemonstrativoRendaJuros** `L:L`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaJuros)=1;"Juros Renda";IF(ROW(DemonstrativoRendaJuros)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;JurosRenda;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá juros sobre a renda, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna BH.

* * *

##### **DemonstrativoRendaJurosAlcada** `AB:AB`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaJurosAlcada)=1;"Juros Renda Alçada";IF(ROW(DemonstrativoRendaJurosAlcada)<=TotalCompetencias +1;IF(DemonstrativoAlcada;0;0);""))){% endhighlight %}


~~~
mm/yyyy
#,##0.00;(#,##0.00);-
~~~




* * *

##### **DemonstrativoRendaMensal** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaMensal)=1;"Renda Mensal";IF(ROW(DemonstrativoRendaMensal)<=TotalCompetencias+1;IF(DemonstrativoRenda;RendaMensalEfetiva;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica a renda mensal, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoRenda", buscando os valores correspondentes na planilha "evolução" coluna AJ.

* * *

##### **DemonstrativoRendaPrincipal** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaPrincipal)=1;"Principal Renda";IF(ROW(DemonstrativoRendaPrincipal)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;PrincipalRenda;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica o principal da renda mensal, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna AU.

* * *

##### **DemonstrativoRendaPrincipalAtualizado** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaPrincipalAtualizado)=1;"Principal Renda Atualizado";IF(ROW(DemonstrativoRendaPrincipalAtualizado)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;PrincipalRendaAtualizado;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica o principal da renda mensal atualizada, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna BB.

* * *

##### **DemonstrativoRendaPrincipalAtualizadoAlcada** `Z:Z`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaPrincipalAtualizadoAlcada)=1;"Principal Renda Atualizado Alçada";IF(ROW(DemonstrativoRendaPrincipalAtualizadoAlcada)<=TotalCompetencias + 1;IF(DemonstrativoAlcada;TotalRendaAlcada;0);""))){% endhighlight %}


~~~
mm/yyyy
#,##0.00;(#,##0.00);-
~~~




* * *

##### **DemonstrativoRendaTotal** `M:M`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoRendaTotal)=1;"Total Renda";IF(ROW(DemonstrativoRendaTotal)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;TotalRenda;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) identifica o total da renda mensal, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna BK.

* * *

##### **DemonstrativoTotalMes** `V:V`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoTotalMes)=1;"Total Mês";IF(ROW(DemonstrativoTotalMes)<=TotalCompetencias+1;IF(DemonstrativoDiferencas;TotalMes;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica o total apurado no mês, selecionando as competências indicadas por "verdadeiro" na coluna "DemonstrativoDiferenças", buscando os valores correspondentes na planilha "evolução" coluna BM.

* * *

##### **DemonstrativoTotalMesAlcada** `AE:AE`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(DemonstrativoTotalMesAlcada)=1;"Total Mês Alçada";IF(ROW(DemonstrativoTotalMesAlcada)<=TotalCompetencias + 1;IF(DemonstrativoAlcada;PrincipalAlcada;0);""))){% endhighlight %}


~~~
mm/yyyy
#,##0.00;(#,##0.00);-
~~~


> Fórmula Matriz (ArrayFormula) identifica as competências onde haverá valores de renda, indicadas por "verdadeiro" na coluna "DemonstrativoRenda",
buscando as competências correspondentes na planilha "evolução" coluna A.