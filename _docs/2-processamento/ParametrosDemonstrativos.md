---
title: ParametrosDemonstrativos
category: Processamento
order: 3
---

##### **DadosObrigatoriosFaltantes** `A45`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(ISNUMBER(Protocolo);"";"Protocolo#")& IF(ISNUMBER(Citacao);"";"Citação#")&IF(ISNUMBER(DIBOriginario);"";"DIB#")&IF(ISNUMBER(RMIInformada);"";"RMI#")&IF(ISNUMBER(DataAtualizacao);"";"Data da Atualização#"){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Indica os dados obrigatórios não alimentados na planilha

* * *

##### **ModeloSumulaAtrasados** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}

+ **Formato**:
~~~
0.###############
~~~


> Dados utilizados para Súmula (data de início do pagamento, atrasados, data de atualização e honorários sucumbenciais)

* * *

##### **ModeloSumulaBeneficio** `D2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}

+ **Formato**:
~~~
0.###############
~~~


> Dados utilizados para Súmula (espécie, RMI, RMA, DIB e DCB)

* * *

##### **ObservacoesDescontos** `A24:B31`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=JOIN(CHAR(10);FILTER(OFFSET(DescontosOutrosObservacoes;6;0);OFFSET(DescontosOutrosObservacoes;6;0)<>"")){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Engloba as observações feitas na planilha "Descontos".



* * *

##### **TextoObservacoes** `A34`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(MostrarObservacoesAutomaticas="Sim";IF(ISTEXT(CONCATENATE(Observacoes1));"Modificadores:"&CHAR(10)&CONCATENATE(Observacoes1)&CHAR(10)&CHAR(10);"")&IF(ISTEXT(CONCATENATE(ObservacoesDescontos));"Descontos:"&CHAR(10)&CONCATENATE(ObservacoesDescontos)&CHAR(10)&CHAR(10);"");"")&IF(ISTEXT(CONCATENATE(ObservacoesFinais));"Observações finais:"&CHAR(10)&ObservacoesFinais;""){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Selecionada a opção de mostrar observações automáticas (configuração), engloba todas as observações efetuadas:
-observações finais
-observações descontos
-observações modificadores

* * *

##### **TextoSumula** `D34`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(ISTEXT(CONCATENATE(TextoSumulaOriginario));CONCATENATE(TextoSumulaOriginario)&CHAR(10);"")&IF(ISTEXT(CONCATENATE(TextoSumulaDerivado));CONCATENATE(TextoSumulaDerivado)&CHAR(10);"")&IF(ISTEXT(CONCATENATE(TextoSumulaAtrasados));CONCATENATE(TextoSumulaAtrasados);""){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Consolida os dados das Súmulas (benefício originário, benefício derivado e atrasados).

* * *

##### **TextoSumulaAtrasados** `D28`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(CONCATENATE(ModeloSumulaAtrasados);"${DIP}";DataFinalDiferencas+1);"${TotalAtrasados}";TotalGeral);"${DataCalculo}";DataAtualizacao);"${TotalHonorarios}";HonorariosSucumbenciaisTotal){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Extrai dados de valores apurados para compor a Súmula.


* * *

##### **TextoSumulaDerivado** `D21`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);"BENEFÍCIO DERIVADO:"&CHAR(10)& SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(CONCATENATE(ModeloSumulaBeneficio);"${Especie}";EspecieDerivado&" - "&INDEX(ListaBeneficios!A:B;MATCH(EspecieDerivado;ListaBeneficios!A:A;0);2);1);"${RMI}";RMIDerivado);"${RMA}";RMA);"${DIB}";DIBDerivado);"${DCB}";DCBDerivado);""){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Extrai dados do benefício derivado para compor a Súmula.

* * *

##### **TextoSumulaOriginario** `D14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(ISNUMBER(DIBDerivado);"BENEFÍCIO ORIGINÁRIO:"&CHAR(10);"")& SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(CONCATENATE(ModeloSumulaBeneficio);"${Especie}";EspecieOriginario&" - "&INDEX(ListaBeneficios!A:B;MATCH(EspecieOriginario;ListaBeneficios!A:A;0);2);1);"${RMI}";RMIOriginario);"${RMA}";IF(ISNUMBER(DIBDerivado);"";RMA));"${DIB}";DIBOriginario);"${DCB}";DCBOriginario){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Extrai dados do benefício originário para compor a Súmula.

* * *

##### **TotalLinhasAbono** `B3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=COUNTIF(DemonstrativoAbono;TRUE()){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~




* * *

##### **TotalLinhasAbonoalcada** `B4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=COUNTIF(OFFSET(DemonstrativoAbonoPrincipalAtualizadoAlcada;1;0;TotalCompetencias);">0"){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~




* * *

##### **TotalLinhasRenda** `B2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=COUNTIF(DemonstrativoRenda;TRUE()){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~

