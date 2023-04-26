---
layout: post
title: "Analise Descritiva do Dataset"
categories: EDA
author:
- João Holz
meta: "Ufes - IC 1 - Departamento de Estatística"
---

Utilizando o Dataset do inca PRODES, temos as seguintes limitações. Ano inicial é 1988, e o ano final 2021. Então Faremos uma comparação quase que historica das proporções desmatadas em cada um dos estados onde está presente a amazônia legal

## Nossos Dados
Nossos dados são uma série histórica do total de kilometros quadrados (km²) desmatados. Com Index sendo o ano e as colunas a quantidade desmatada no estado. 

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Ano/Estados</th>
      <th>AC</th>
      <th>AM</th>
      <th>AP</th>
      <th>MA</th>
      <th>MT</th>
      <th>PA</th>
      <th>RO</th>
      <th>RR</th>
      <th>TO</th>
      <th>AMZ LEGAL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1988</th>
      <td>620</td>
      <td>1510</td>
      <td>60</td>
      <td>2450</td>
      <td>5140</td>
      <td>6990</td>
      <td>2340</td>
      <td>290</td>
      <td>1650</td>
      <td>21050</td>
    </tr>
    <tr>
      <th>1989</th>
      <td>540</td>
      <td>1180</td>
      <td>130</td>
      <td>1420</td>
      <td>5960</td>
      <td>5750</td>
      <td>1430</td>
      <td>630</td>
      <td>730</td>
      <td>17770</td>
    </tr>
    <tr>
      <th>1990</th>
      <td>550</td>
      <td>520</td>
      <td>250</td>
      <td>1100</td>
      <td>4020</td>
      <td>4890</td>
      <td>1670</td>
      <td>150</td>
      <td>580</td>
      <td>13730</td>
    </tr>
    <tr>
      <th>1991</th>
      <td>380</td>
      <td>980</td>
      <td>410</td>
      <td>670</td>
      <td>2840</td>
      <td>3780</td>
      <td>1110</td>
      <td>420</td>
      <td>440</td>
      <td>11030</td>
    </tr>
    <tr>
      <th>1992</th>
      <td>400</td>
      <td>799</td>
      <td>36</td>
      <td>1135</td>
      <td>4674</td>
      <td>3787</td>
      <td>2265</td>
      <td>281</td>
      <td>409</td>
      <td>13786</td>
    </tr>
  </tbody>
</table>
</div>

## Proporções

Nesse primeiro momento de analise descritiva não vou padronizar ou dividir pelo tamanho do estado. Vamos comparar o desmatado total por estado comparando a primeira decada de coleta com o todo, para ver se algum estado se mostra muito discrepante recentemente nesse quesito.     
Os Estados tem tamanhos muito diferentes, a quantidade desmatada vai ser muito influenciada por isso. Isso está nos itens de melhora nos próximos passos.    

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_3_0.png)

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_4_0.png)


## Serie Histórica

Vemos nas series historicas.

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_5_0.png)

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_6_0.png)


## Mapa

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_10_0.png)

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_11_0.png)


<div>
<div class="box">
    <img src="https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_11_0.png"/>
    <span> Primeiros 10 anos </span>
</div>
<div class="box">
    <img src="https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_10_0.png"/>
    <span> Total </span>
</div>
</div>




## Conclusão

Aparentemente o desmatamento reduziu muito pós 2000, e faz uma parabola começando a subir de novo pro fim da segunda decada de dados. Podem ser muitos motivos como politicas anti desmatamento dos estados envolvidos, do governo federal. 

## Próximos Passos
Adicionar na analise o tamanho do estado do Brasil.
