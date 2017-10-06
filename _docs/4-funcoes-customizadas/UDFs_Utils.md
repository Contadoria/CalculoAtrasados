---
title: UDFs_Utils
category: Funções Customizadas
order: 1
---
{% highlight javascript linenos %}
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
  
  utils.diaSeguinte = function(d) {
    var novaData = new Date(d.getTime());
    novaData.setDate(d.getDate() + 1);
    return novaData;
  };

  utils.diaAnterior = function(d) {
    var novaData = new Date(d.getTime());
    novaData.setDate(d.getDate() - 1);
    return novaData;
  };
  
  utils.mesmaData = function(d1, d2) {
    return d1.getUTCFullYear() === d2.getUTCFullYear() && d1.getUTCMonth() === d2.getUTCMonth() && d1.getUTCDate() === d2.getUTCDate();
  };
  
  utils.dataDifMeses = function(inicial, final) {
    return (final.getMonth() - inicial.getMonth()) + ((final.getFullYear() - inicial.getFullYear()) * 12);
  };
  
  utils.calcularProporcaoInicial = function(dataInicial, dataFinal) {
    var totalCompetencias = utils.dataDifMeses(dataInicial, dataFinal) + 1;
    if (totalCompetencias === 1) {
      return ((Math.min(30, dataFinal.getDate()) - Math.min(dataInicial.getDate())) + 1) / 30
    }
    return Math.max(1, 30 - (dataInicial.getDate() - 1)) / 30;
  };

  utils.calcularProporcaoFinal = function(dataInicial, dataFinal) {
    var totalCompetencias = utils.dataDifMeses(dataInicial, dataFinal) + 1;
    if (totalCompetencias === 1) {
      return ((Math.min(30, dataFinal.getDate()) - Math.min(30, dataInicial.getDate())) + 1) / 30
    }
    // Regra especial para fevereiro
    if (dataFinal.getMonth() === 1 && dataFinal.getDate() > 27) {
      return 1;
    }
    return Math.min(30, dataFinal.getDate())/ 30;
  }; 

  utils.abonoMaior15Dias = function(dataInicial, dataFinal) {
    var totalCompetencias = utils.dataDifMeses(dataInicial, dataFinal) + 1;
    if (totalCompetencias === 1) {
      return dataFinal.getDate() - dataInicial() + 1 >= 15;
    }
    return true;
  }
  
  utils.calcularProporcaoAbono = function(dataInicial, dataFinal) {
    var totalCompetencias = utils.dataDifMeses(dataInicial, dataFinal) + 1;
    var subtrairCompetenciaInicial = dataInicial.getDate() > 16;
    var subtrairCompetenciaFinal = dataFinal.getDate() < 15;
    var competenciasEfetivas = totalCompetencias - (subtrairCompetenciaInicial ? 1 : 0) - (subtrairCompetenciaFinal ? 1 : 0);
    return competenciasEfetivas / 12;
  }  

  utils.testarCalculoRMA = function() {
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
  };
  
  utils.arredondarParaBaixo = function(valor, fator) {
    return (valor * fator).toString().replace(/(\d*\.\d{2})(\d*.)/, '$1');
  }

  return utils;

})(Utilidades || Object.create(null));


{% endhighlight %}