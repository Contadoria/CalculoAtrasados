---
title: UDFs
category: Funções Customizadas
order: 0
---
{% highlight javascript linenos %}
'use strict';

/**
* Retorna matriz com os índices acumulados a partir de uma matriz de índices, desprezando os índices de valor 'zero'.
*
* @param {array} indices Matriz com os índices, em ordem cronológica crescente.
* @return {array} A matriz com os índices acumulados, observando a ordem dos dados de entrada.
*
* @customfunction
*/
function jef_INDICE_ACUMULADO(indices) {
  
  if (!Array.isArray(indices)) { 
    throw new Error('Dado de entrada não é matriz.'); 
  }
  
  var PRECISAO = 1000000000000;
  
  return indices.map(function(indice, idx, arr){
    return arr.slice(idx).reduce(function(anterior, atual){
      if (isNaN(anterior) || parseFloat(anterior) === 0) { 
        return atual; 
      }
      if (isNaN(atual) || parseFloat(atual) === 0 ) { 
        return anterior; 
      }
      
      return (Math.floor(parseFloat(anterior) * PRECISAO) * Math.floor(parseFloat(atual) * PRECISAO)) / (PRECISAO * PRECISAO);
    },1);
  });
}

/**
* Retorna matriz com as taxas de juros simples acumuladas a partir de uma matriz de taxas mensais de juros.
*
* @param {array} taxasMensais Matriz com as taxas mensais de juros, em ordem cronológica crescente.
* @return {array} A matriz com as taxas acumuladas (juros simples), observando a ordem dos dados de entrada.
*
* @customfunction
*/
function jef_JUROS_ACUMULADOS(taxasMensais) {
  
  if (!Array.isArray(taxasMensais)) { 
    throw new Error ('Dado de entrada não é matriz.'); 
  }
  
  var PRECISAO = 1000000000000;
  
  return taxasMensais.map(function(taxaMensal,index,arr){
    
    return arr.slice(index).reduce(function(anterior, atual){
      if (isNaN(anterior)) { 
        return atual; 
      }
      if (isNaN(atual)) { 
        return anterior; 
      }

      return (Math.floor(parseFloat(anterior) * PRECISAO) + Math.floor(parseFloat(atual) * PRECISAO)) / PRECISAO;
    },0);
  });
}

/**
* Retorna matriz com as rendas mensais reajustadas a partir de uma renda mensal inicial e de uma matriz de fatores de reajuste.
*
* @param {number} valorInicial Valor correspondente à renda mensal inicial.
* @param {array} fatores Matriz com os fatores de reajuste, em ordem cronológica crescente.
* @return {array} A matriz com as rendas mensais reajustadas, observando a ordem dos dados de entrada.
*
* @customfunction
*/
function jef_EVOLUCAO_RENDA(valorInicial, fatores) {
  
  if (!Array.isArray(fatores)) { 
    throw new Error('Dado de entrada "fatores" não é matriz.'); 
  }
  
  if (isNaN(valorInicial)) { 
    throw new Error ('A renda inicial informada não é numérica.'); 
  }
  
  var PRECISAO = 1000000000000;
  
  var valorAtual = valorInicial;
  
  return fatores.map(function(fator){
    if (isNaN(fator)) {
      return valorAtual; 
    }
    valorAtual = (Math.floor(valorAtual * PRECISAO) * Math.floor(fator * PRECISAO)) / (PRECISAO * PRECISAO);
    return valorAtual;
  });
}

/**
* Retorna matriz com o resultado da soma dos valores em cada linha de uma matriz fornecida.
*
* @param {array} intervalo Matriz com os valores a serem somados.
* @return {array} A matriz com os resultados das somas, observando a ordem dos dados de entrada.
*
* @customfunction
*/
function jef_SOMAR_LINHAS(intervalo) {
  
  if (!Array.isArray(intervalo)) { 
    throw new Error('Dado de entrada não é matriz.'); 
  }
  
  return intervalo.map(function(linha) {
    return linha.reduce(function(anterior, atual) {
      
      atual = isNaN(parseFloat(atual)) ? 0 :parseFloat(atual); 
      anterior = isNaN(parseFloat(anterior)) ? 0 :parseFloat(anterior); 
      
      return anterior + atual;
    }, 0);
  });
}

/**
* Conta os valores numéricos em uma matriz linha a linha.
*
* @param {array} intervalo Matriz com os valores a serem verificados.
* @return {array<number>} A matriz com os resultados da contagem.
*
* @customfunction
*/
function jef_CONT_NUM_POR_LINHA(intervalo) {
  
  if (!Array.isArray(intervalo)) { 
    throw new Error('Dado de entrada não é matriz.'); 
  }
  
  return intervalo.map(function(linha) {
    return linha.reduce(function(anterior, atual) {
      
      atual = isNaN(parseFloat(atual)) ? 0 : parseFloat(atual) > 0 ? 1 : 0; 
      anterior = isNaN(parseFloat(anterior)) ? 0 : parseFloat(anterior); 
      
      return anterior + atual;
    }, 0);
  });
}
{% endhighlight %}