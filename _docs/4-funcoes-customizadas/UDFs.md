---
title: UDFs
category: Funções Customizadas
order: 0
---
{% highlight javascript linenos %}
'use strict';

/**
* Retorna o url da planilha.
*
* @param {Array} dummy Parâmetro fajuto, apenas para forçar a atualização.
* @return {string} O url. 
*
* @customfunction
*/
function jef_URL(dummy) {
  return SpreadsheetApp.getActiveSpreadsheet().getUrl();
}

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
*
* Alterado em 21/09/2017 - No lugar da técnica da PRECISAO, utilizamos a conversão em string
*                          para tornar possível o arredondamento para baixo em cada etapa do cálculo.
*
*/
function jef_EVOLUCAO_RENDA(valorInicial, fatores) {
  
  if (!Array.isArray(fatores)) { 
    throw new Error('Dado de entrada "fatores" não é matriz.'); 
  }
  
  if (isNaN(valorInicial)) { 
    throw new Error ('A renda inicial informada não é numérica.'); 
  }
  
  var valorAtual = valorInicial;
  
  return fatores.map(function(fator){
    if (isNaN(fator)) {
      return valorAtual; 
    }
    valorAtual = parseFloat((valorAtual * fator).toString().replace(/(\d*\.\d{2})(\d*.)/, '$1'))
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

/**
* Calcula RMA a partir dos dados fornecidos, retornando toda a evolução da renda mensal.
*
* @param {Date} DIBOriginario Data de início do benefício originário.
* @param {Number} RMIOriginario Renda mensal inicial do benefício originário.
* @param {Date} DCBOriginario Data de cessação do benefício originário.
* @param {Number} RMIDerivado Renda mensal inicial do benefício derivado.
* @param {Date} DCBDerivado Data de cessação do benefício derivado.
* @param {Number} indiceReposicaoTeto Índice de reposicao do teto. Se não fornecido, será fixado em 1.
* @param {Number} equivalenciaSalarial Número de salários mínimos correspondentes à RMI. Se a DIBOriginario >= 05/10/1988, será ignorado.
* @param {Boolean} calcularAbono Determina se haverá cálculo do abono. Se omitida a variável, o abono será calculado.
* @param {Date} dataAtualizacao Data de atualização da planilha.
* @param {Array} tabelaReajuste Matriz com seis colunas: 
*                 - competência;
*                 - índice proporcional;
*                 - índice integral;
*                 - data-base;
*                 - piso;
*                 - teto.
* @return {array} Retorna uma matriz de duas colunas com os valores da renda e do abono evoluídos desde a DIB do benefício originário.
*
* @customfunction
*
* Função criada em 04/10/2017
*
*/
function jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOriginario, RMIOriginario, DCBOriginario, RMIDerivado, DCBDerivado, indiceReposicaoTeto, equivalenciaSalarial, calcularAbono, dataAtualizacao, tabelaReajuste) {
  
  var Utilidades = (function(utils) {
    
    // https://toddmotto.com/understanding-javascript-types-and-reliable-type-checking/
    utils.isDate = function(elem) {
      return Object.prototype.toString.call(elem).slice(8, -1) === 'Date';
    };
    
    utils.isNumber = function(elem) {
      return Object.prototype.toString.call(elem).slice(8, -1) === 'Number';
    };
    
    utils.primeiroDiaDoMes = function(d, m) {
      m = utils.isNumber(m) ? m : 0;
      var ano = d.getUTCFullYear();
      var mes = d.getUTCMonth(); 
      var dia = 1; 
      return new Date(ano, mes + m, dia);
    };
    
    utils.ultimoDiaDoMes = function(d, m) {
      m = utils.isNumber(m) ? m : 0;
      var ano = d.getUTCFullYear();
      var mes = d.getUTCMonth() + 1; 
      var dia = 0; 
      return new Date(ano, mes + m, dia);
    };  
    
    utils.dataDifMeses = function(inicial, final) {
      return (final.getMonth() - inicial.getMonth()) + ((final.getFullYear() - inicial.getFullYear()) * 12);
    };
    
    return utils;
    
  })(Utilidades || Object.create(null));

  /*
  *
  * BLOCO DE VALIDAÇÃO
  *
  **/
  
  if (!Utilidades.isDate(DIBOriginario)) { 
    throw new Error('DIB do benefício originário irregular.'); 
  }
  
  if (!Utilidades.isNumber(RMIOriginario)) { 
    throw new Error('RMI do benefício originário irregular.'); 
  }
  
  if (!Utilidades.isDate(dataAtualizacao)) { 
    throw new Error('Data de atualização irregular.'); 
  }
  
  if (!Utilidades.isDate(DCBOriginario)) { 
    DCBOriginario = null; 
  }
  
  if (!Utilidades.isNumber(RMIDerivado)) { 
    RMIDerivado = null; 
  }
  
  if (!Utilidades.isDate(DCBDerivado)) { 
    DCBDerivado = null; 
  }
  
  if (!Array.isArray(tabelaReajuste) || tabelaReajuste[0].length < 6) { 
    throw new Error('Tabela de índices irregular. Você deve fornecer, nesta ordem: competência, índice proporcional, índice integral, data-base, piso e teto'); 
  }
  
  if (!Utilidades.isNumber(indiceReposicaoTeto) || indiceReposicaoTeto < 1) {
    indiceReposicaoTeto = 1;
  }
  
  if (!Utilidades.isNumber(equivalenciaSalarial) || equivalenciaSalarial < 0) {
    equivalenciaSalarial = null;
  }
  
  calcularAbono = (calcularAbono === false) ? false : true;
  
  /*
  *
  * BLOCO DE CÁLCULO
  *
  **/
  
  var temDerivado = Utilidades.isNumber(RMIDerivado) && Utilidades.isDate(DCBOriginario);

  /*
  * Nos termos do art. 58 do ADCT, o referido dispositivo se aplica aos benefícios mantidos NA data de promulgação
  * da CF/88, ou seja, 05/10/1988. Assim, se o benefício foi concedido até essa data, inclusive, a equivalência
  * salarial deve ser aplicada.
  **/
  var aplicarArt58 = Utilidades.isNumber(equivalenciaSalarial) && DIBOriginario.valueOf() < new Date(1988, 9, 6)
  
  /*
  * No caso de aplicação do art. 58 do ADCT, adota-se como termo inicial a competência 12/1991
  * porque foi a partir de 01/01/1992 que deixou de vigorar a equivalência salarial
  **/
  var dataInicialDiferencas = aplicarArt58 ? new Date(1991, 11, 1) : new Date(DIBOriginario.getTime());
  var dataFinalDiferencas = temDerivado 
  ? Utilidades.isDate(DCBDerivado) ? DCBDerivado : dataAtualizacao
  : Utilidades.isDate(DCBOriginario) ? DCBOriginario : dataAtualizacao;
  
  var competenciaInicial = Utilidades.primeiroDiaDoMes(dataInicialDiferencas, 0);
  var competenciaFinal = Utilidades.primeiroDiaDoMes(dataFinalDiferencas, 0);
  var totalCompetencias = Utilidades.dataDifMeses(competenciaInicial, competenciaFinal) + 1;
  
  var proporcaoInicial = (totalCompetencias === 1)
  ? ((Math.min(30, dataFinalDiferencas.getDate()) - Math.min(dataInicialDiferencas.getDate())) + 1) / 30
  : Math.max(1, 30 - (dataInicialDiferencas.getDate() - 1)) / 30;
  
  var proporcaoFinal = (totalCompetencias === 1)
  ? ((Math.min(30, dataFinalDiferencas.getDate()) - Math.min(30, dataInicialDiferencas.getDate())) + 1) / 30
  : dataFinalDiferencas.getMonth() === 1 && dataFinalDiferencas.getDate() > 27 ? 1 : Math.min(30, dataFinalDiferencas.getDate())/ 30;
  
  var abonoMaior15Dias = (totalCompetencias === 1) ? dataFinalDiferencas.getDate() - dataInicialDiferencas.getDate() + 1 >= 15 : true;
  
  calcularAbono = calcularAbono && abonoMaior15Dias;
  
  if (calcularAbono) {
    
    var primeiroAno = dataInicialDiferencas.getFullYear();
    var ultimoAno = dataFinalDiferencas.getFullYear();
    
    if (temDerivado && Utilidades.isDate(DCBDerivado)) {
      var dataUltimoAbono = new Date(DCBDerivado.getTime());
    } else if (!temDerivado && Utilidades.isDate(DCBOriginario)) {
      var dataUltimoAbono = new Date(DCBOriginario.getTime());
    } else if (dataFinalDiferencas.getMonth === 11 || primeiroAno === ultimoAno) {
      var dataUltimoAbono = new Date(dataFinalDiferencas.getTime);
    } else {
      var dataUltimoAbono = null;
    }

    function calcularProporcaoAbono(dataInicial, dataFinal) {
      var totalCompetencias = Utilidades.dataDifMeses(dataInicial, dataFinal) + 1;
      var subtrairCompetenciaInicial = dataInicial.getDate() > 16;
      var subtrairCompetenciaFinal = dataFinal.getDate() < 15;
      var competenciasEfetivas = totalCompetencias - (subtrairCompetenciaInicial ? 1 : 0) - (subtrairCompetenciaFinal ? 1 : 0);
      return competenciasEfetivas / 12;
    }
    
    if (primeiroAno === ultimoAno) {
      var dataPrimeiroAbono = dataUltimoAbono;
      var proporcaoPrimeiroAbono = 0;
      var proporcaoUltimoAbono = calcularProporcaoAbono(dataInicialDiferencas, dataUltimoAbono);
    } else {
      var dataPrimeiroAbono = new Date(primeiroAno, 11, 1);
      var proporcaoPrimeiroAbono = calcularProporcaoAbono(dataInicialDiferencas, new Date(primeiroAno, 11, 31));
      if (Utilidades.isDate(dataUltimoAbono)) {
        var proporcaoUltimoAbono = calcularProporcaoAbono(new Date(ultimoAno, 0, 1), dataUltimoAbono);
      } else {
        var proporcaoUltimoAbono = 0;
        
      }
    }
  }
  
  var datasBase = tabelaReajuste.filter(function(linha) {
    return (linha[0].valueOf() > competenciaInicial.valueOf() && linha[0].valueOf() <= competenciaFinal.valueOf() && linha[3] === true);
  });
  
  var primeiraDataBase = datasBase.length > 0 ? datasBase[0][0] : null;
  var linhaIndiceProporcional = tabelaReajuste.filter(function(linha) {
    return linha[0].valueOf() === competenciaInicial.valueOf();
  });
  var indiceProporcional = linhaIndiceProporcional.length > 0 ? linhaIndiceProporcional[0][1] : 1;
  
  if (aplicarArt58) {
    var linhaCompetenciaInicial = tabelaReajuste.filter(function(linha) {
      return linha[0].valueOf() === competenciaInicial.valueOf();
    });
    var salarioMinimo = linhaCompetenciaInicial[0][4]; // O salário mínimo está na quinta coluna da tabela
    var RMA = salarioMinimo * equivalenciaSalarial;
    
  } else {
    var RMA = RMIOriginario;
  }
  
  return tabelaReajuste.map(function(linha, idx) {
    
    var competencia = linha[0];
    var indiceIntegral = linha[2];
    var dataBase = linha[3];
    var piso = linha[4];
    var teto = linha[5];
    
    if (competencia.valueOf() >= competenciaInicial.valueOf() && competencia.valueOf() <= competenciaFinal.valueOf()) {
      
      if (dataBase === true) {
        
        if (competencia.valueOf() === primeiraDataBase.valueOf() && !aplicarArt58) {
          
          var renda = parseFloat(RMA * indiceProporcional * indiceReposicaoTeto).toString().replace(/(\d*\.\d{2})(\d*.)/, '$1');
          
        } else {
          
          var renda = parseFloat(RMA * indiceIntegral).toString().replace(/(\d*\.\d{2})(\d*.)/, '$1');
          
        }
        
      } else {
        
        var renda = RMA;
        
      }
      
      if (temDerivado && competencia.valueOf() === Utilidades.primeiroDiaDoMes(DCBOriginario).valueOf() && (!aplicarArt58 || DCBOriginario.valueOf() >= new Date(1992, 1, 1).valueOf())) {
        /*
        * Na primeira competência do benefício derivado, é necessário aplicar a proporcionalidade
        **/
        var renda = ((renda / 30) * DCBOriginario.getDate()) + ((RMIDerivado / 30) * Math.max(30 - (DCBOriginario.getDate()), 1));
        RMA = RMIDerivado;
      } else {
        /*
        * Esse critério de aplicação dos limites mínimo e máximo, aparentemente incosistente
        * tenta refletir o modo como o próprio INSS evolui a renda mensal, ou seja:
        * - se o benefíco é inferior ao mínimo, o valor original é preservado e há apenas a elevação ao mínimo
        *   mês a mês
        * - se o benefício é superior ao teto, a própria renda mensal é limitada e o valor excedente é descartado
        **/
        if (renda < piso) {
          RMA = renda;
          renda = piso;
        } else {
          renda = Math.min(teto, renda);
          RMA = renda;
        }
      }
      
      var calcularAbonoNaCompetencia = (competencia.getMonth() === 11) || (Utilidades.isDate(dataUltimoAbono) && competencia.valueOf() === Utilidades.primeiroDiaDoMes(dataUltimoAbono, 0).valueOf());
      
      if (calcularAbono && calcularAbonoNaCompetencia) {
        if (Utilidades.isDate(dataUltimoAbono) && competencia.valueOf() === Utilidades.primeiroDiaDoMes(dataUltimoAbono).valueOf()) {
          var abono = renda * proporcaoUltimoAbono;
        } else if (competencia.valueOf() === Utilidades.primeiroDiaDoMes(dataPrimeiroAbono).valueOf()) {
          var abono = renda * proporcaoPrimeiroAbono;
        } else {
          var abono = renda;
        }
      } else {
        var abono = 0;
      }      
      
      if (competencia.valueOf() === competenciaInicial.valueOf()) {
        renda = renda * proporcaoInicial;
      }
      
      if (competencia.valueOf() === competenciaFinal.valueOf()) {
        renda = renda * proporcaoFinal;
      }
      
      return [renda, abono]
      
    } else {
      
      return [0, 0];      
    }
    
  });
}


function testarCalculoRMA() {
  try {
    var planilha = SpreadsheetApp.getActiveSpreadsheet();
    var pagina = planilha.getSheetByName('BeneficiosPagos');
    var DIBOriginario = pagina.getRange('H3').getValue();
    var RMIOriginario = pagina.getRange('H4').getValue();
    var DCBOriginario = pagina.getRange('H5').getValue();
    var RMIDerivado = pagina.getRange('H7').getValue();
    var DCBDerivado = pagina.getRange('H8').getValue();
    var indiceReposicao = pagina.getRange('H10').getValue();
    var equivalencia = pagina.getRange('H11').getValue(); 
    var abono = true;
    var dataAtualizacao = planilha.getRangeByName('DataAtualizacao').getValue();
    var tabela = pagina.getRange('A13:F13').offset(0, 0, 636).getValues();
    try {
      var resultado = jef_CALCULAR_RMA_COM_EVOLUCAO(DIBOriginario,RMIOriginario,DCBOriginario,RMIDerivado,DCBDerivado, indiceReposicao, equivalencia, abono, dataAtualizacao, tabela);
      Logger.log(resultado)
    } catch (e) {
      Logger.log(e)
    }
    
  } catch (e) {
    Logger.log(e.message)
    Logger.log(e.stack)
  }
}
{% endhighlight %}