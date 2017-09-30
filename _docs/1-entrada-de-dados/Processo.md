---
title: Processo
category: Entrada
order: 0
---

##### **Autor** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Nome do autor.

* * *

##### **Citacao** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Data da citação do réu. Utilizado como termo inicial para cômputo dos juros de mora conforme item 4.3.2 do Manual de Cálculos aprovado pela [Resolução nº 267/2013 do CJF](http://www.cjf.jus.br/phpdoc/sicom/arquivos/pdf/manual_de_calculos_revisado_ultima_versao_com_resolucao_e_apresentacao.pdf?PHPSESSID=cma4ju1fdhdhsi1ha8k4pqmp17)

* * *

##### **CriterioAlcada** `D15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesAlcada!A:A
~~~

> Selecionar o critério de alçada adotado pelo Magistrado:
* 1 - Soma das parcelas vencidas até a data do ajuizamento, somadas com 12 vincendas;
* 2 - Apenas parcelas vencidas até a data do ajuizamento.

* * *

##### **DER** `D10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/mm/yyyy
~~~


> Data da entrada do requerimento administrativo junto ao INSS.

* * *

##### **NaturezaAcao** `D11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesAcao!A:A
~~~

> Selecionar se trata-se de concessão ou revisão de benefício.
**Somente casos de revisão possibilitam lançamentos no benefício pago**

* * *

##### **Processo** `D5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Número do processo.

* * *

##### **Protocolo** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Data do protocolo inicial do processo.
Normalmente utilizado para contagem de prescrição.

* * *

##### **RenunciaOpcao** `D16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **Reu** `D7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Nome do réu.