---
title: Desdobro
category: Entrada
order: 5
---

##### **DIBBeneficioDesdobrado** `D7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(OpcaoBeneficioDesdobrado;1;1)="2";DIBOriginario;IF(MID(OpcaoBeneficioDesdobrado;1;1)="3";DIBDerivado;"")){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **DataDesdobro1** `F5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DataDesdobro2** `F6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DataDesdobro3** `F7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DataDesdobro4** `F8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DataDesdobro5** `F9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **OpcaoBeneficioDesdobrado** `D5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesDesdobro!A:A
~~~



* * *

##### **QuotaDevida1** `G5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaDevida2** `G6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaDevida3** `G7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~




* * *

##### **QuotaDevida4** `G8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaDevida5** `G9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaPaga1** `H5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaPaga2** `H6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaPaga3** `H7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaPaga4** `H8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaPaga5** `H9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
# ?/?
~~~




* * *

##### **QuotaProporcional1** `I5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DataDesdobro1=DIBBeneficioDesdobrado;QuotaDevida1-QuotaPaga1;
(((DAY(DataDesdobro1)-1)/30))+((MAX(30-DAY(DataDesdobro1)+1;1)/30)*(QuotaDevida1-QuotaPaga1))){% endhighlight %}


~~~
# ?/?
~~~




* * *

##### **QuotaProporcional2** `I6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DAY(DataDesdobro2)=1;QuotaDevida2-QuotaPaga2;
(((DAY(DataDesdobro2)-1)/30)*(QuotaDevida1-QuotaPaga1))+((MAX(30-DAY(DataDesdobro2)+1;1)/30)*(QuotaDevida2-QuotaPaga2))){% endhighlight %}


~~~
# ?/?
~~~




* * *

##### **QuotaProporcional3** `I7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DAY(DataDesdobro3)=1;QuotaDevida3-QuotaPaga3;
(((DAY(DataDesdobro3)-1)/30)*(QuotaDevida2-QuotaPaga2))+((MAX(30-DAY(DataDesdobro3)+1;1)/30)*(QuotaDevida3-QuotaPaga3))){% endhighlight %}


~~~
# ?/?
~~~




* * *

##### **QuotaProporcional4** `I8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DAY(DataDesdobro4)=1;QuotaDevida4-QuotaPaga4;
(((DAY(DataDesdobro4)-1)/30)*(QuotaDevida3-QuotaPaga3))+((MAX(30-DAY(DataDesdobro4)+1;1)/30)*(QuotaDevida4-QuotaPaga4))){% endhighlight %}


~~~
# ?/?
~~~




* * *

##### **QuotaProporcional5** `I9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DAY(DataDesdobro5)=1;QuotaDevida5-QuotaPaga5;
(((DAY(DataDesdobro5)-1)/30)*(QuotaDevida4-QuotaPaga4))+((MAX(30-DAY(DataDesdobro5)+1;1)/30)*(QuotaDevida5-QuotaPaga5))){% endhighlight %}


~~~
# ?/?
~~~


