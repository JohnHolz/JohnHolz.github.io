---
layout: post
title: "5. Cross Validation"
categories: EDA
author:
  - João Holz
meta: "Ufes - IC 1 - Departamento de Estatística"
---

Vamos utilizar um k-fold como forma de validção, dividiremos em 10. K-folds funciona separando o dataset em k subsets de dados, e como temos 10 partições agora, podemos treinar em k-1 e testamos em k, e repetiremos esse processo k vezes. Assim teremos métricas mais confiáveis.

    "daí que a universalidade empírica é uma extensão arbitraria de validade"

Sabendo que existem callbacks eu não adicionei pois tive de aguardar pacientemente pelo treinamento dos modelos. Depois de 2 bitcoins minerados pelo tensorflow chegamos aos seguintes resultadossw

**Kfold**

**fn**: Número de falsos negativos, queremos que seja 0  
**fp**: Número de falsos positivos, apenas como metrica de desempate  
**pha_y**: Número de positivos no dataset para ser previsto  
**thr**: nível de significância que estamos utilizando pra classificar o asteroide como potencialmente perigoso (Threshold)

Utilizando a biblioteca sklearn dividimos em 10 o dataset e a cada iteração salvamos uma pequena sequencia de dados, depois de algumas horas de espera obtivemos os seguintes dados.

<table>
<tr><th> Ada </th><th> Random Fores  </th><th> Tensorflow  </th></tr>
<tr><td>

<table><tr><td>fn</td><td>fp</td><td>pha_Y</td><td>thr</td></tr><tr><td>2</td><td>2</td><td>207</td><td>0.5</td></tr><tr><td>3</td><td>5</td><td>207</td><td>0.5</td></tr><tr><td>6</td><td>0</td><td>207</td><td>0.5</td></tr><tr><td>3</td><td>3</td><td>207</td><td>0.5</td></tr><tr><td>2</td><td>1</td><td>207</td><td>0.5</td></tr><tr><td>2</td><td>3</td><td>206</td><td>0.5</td></tr><tr><td>2</td><td>3</td><td>206</td><td>0.5</td></tr><tr><td>5</td><td>7</td><td>206</td><td>0.5</td></tr><tr><td>3</td><td>3</td><td>206</td><td>0.5</td></tr><tr><td>4</td><td>3</td><td>207</td><td>0.5</td></tr><tr><td>0</td><td>93026</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>93027</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>93026</td><td>207</td><td>0.05</td></tr></table>

</td><td>

<table><tr><td>fn</td><td>fp</td><td>pha_Y</td><td>thr</td></tr><tr><td>2</td><td>2</td><td>207</td><td>0.5</td></tr><tr><td>4</td><td>5</td><td>207</td><td>0.5</td></tr><tr><td>5</td><td>0</td><td>207</td><td>0.5</td></tr><tr><td>3</td><td>2</td><td>207</td><td>0.5</td></tr><tr><td>4</td><td>0</td><td>207</td><td>0.5</td></tr><tr><td>1</td><td>2</td><td>206</td><td>0.5</td></tr><tr><td>2</td><td>3</td><td>206</td><td>0.5</td></tr><tr><td>7</td><td>7</td><td>206</td><td>0.5</td></tr><tr><td>2</td><td>5</td><td>206</td><td>0.5</td></tr><tr><td>5</td><td>2</td><td>207</td><td>0.5</td></tr><tr><td>0</td><td>105</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>155</td><td>207</td><td>0.05</td></tr><tr><td>1</td><td>149</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>240</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>125</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>157</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>204</td><td>206</td><td>0.05</td></tr><tr><td>2</td><td>170</td><td>206</td><td>0.05</td></tr><tr><td>2</td><td>150</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>157</td><td>207</td><td>0.05</td></tr></table>

</td><td>

<table><tr><td>fn</td><td>fp</td><td>pha_Y</td><td>thr</td></tr><tr><td>52</td><td>9</td><td>207</td><td>0.5</td></tr><tr><td>4</td><td>62</td><td>207</td><td>0.5</td></tr><tr><td>54</td><td>5</td><td>207</td><td>0.5</td></tr><tr><td>35</td><td>1</td><td>207</td><td>0.5</td></tr><tr><td>99</td><td>0</td><td>207</td><td>0.5</td></tr><tr><td>75</td><td>5</td><td>206</td><td>0.5</td></tr><tr><td>29</td><td>20</td><td>206</td><td>0.5</td></tr><tr><td>15</td><td>38</td><td>206</td><td>0.5</td></tr><tr><td>28</td><td>11</td><td>206</td><td>0.5</td></tr><tr><td>17</td><td>12</td><td>207</td><td>0.5</td></tr><tr><td>0</td><td>102</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>226</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>106</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>105</td><td>207</td><td>0.05</td></tr><tr><td>6</td><td>27</td><td>207</td><td>0.05</td></tr><tr><td>0</td><td>50</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>129</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>183</td><td>206</td><td>0.05</td></tr><tr><td>3</td><td>136</td><td>206</td><td>0.05</td></tr><tr><td>0</td><td>126</td><td>207</td><td>0.05</td></tr></table>

</td></tr></table>

# Conclusão

Vemos que as métricas foram muito boas, apontando apenas os asteroides problemativos que já estavamos de olho antes. A cada interação do k-folds tem mais dados do que utilizamos na escolha dos modelos, o que mostra que fizemos um bom trabalho. Conseguimos um nível de qualidade de modelos muito bom, otimizamos a nossa métrica de falsos negativos, chegamos em 0 e nosso caso que mais erramos no k-folds erramos pouquissimos dados.

Achei que no final seriamos derrotados pelo asteroide invísivel desfarçado de bonzinho mas conseguimos fazer os modelos acusarem.

<!-- | fn  | fp    | pha_Y | thr  |
| --- | ----- | ----- | ---- |
| 2   | 2     | 207   | 0.5  |
| 3   | 5     | 207   | 0.5  |
| 6   | 0     | 207   | 0.5  |
| 3   | 3     | 207   | 0.5  |
| 2   | 1     | 207   | 0.5  |
| 2   | 3     | 206   | 0.5  |
| 2   | 3     | 206   | 0.5  |
| 5   | 7     | 206   | 0.5  |
| 3   | 3     | 206   | 0.5  |
| 4   | 3     | 207   | 0.5  |
| 0   | 93026 | 207   | 0.05 |
| 0   | 93027 | 207   | 0.05 |
| 0   | 93027 | 207   | 0.05 |
| 0   | 93027 | 207   | 0.05 |
| 0   | 93027 | 207   | 0.05 |
| 0   | 93027 | 206   | 0.05 |
| 0   | 93027 | 206   | 0.05 |
| 0   | 93027 | 206   | 0.05 |
| 0   | 93027 | 206   | 0.05 |
| 0   | 93026 | 207   | 0.05 | -->

<!-- | fn  | fp  | pha_Y | thr  |
| --- | --- | ----- | ---- |
| 2   | 2   | 207   | 0.5  |
| 4   | 5   | 207   | 0.5  |
| 5   | 0   | 207   | 0.5  |
| 3   | 2   | 207   | 0.5  |
| 4   | 0   | 207   | 0.5  |
| 1   | 2   | 206   | 0.5  |
| 2   | 3   | 206   | 0.5  |
| 7   | 7   | 206   | 0.5  |
| 2   | 5   | 206   | 0.5  |
| 5   | 2   | 207   | 0.5  |
| 0   | 105 | 207   | 0.05 |
| 0   | 155 | 207   | 0.05 |
| 1   | 149 | 207   | 0.05 |
| 0   | 240 | 207   | 0.05 |
| 0   | 125 | 207   | 0.05 |
| 0   | 157 | 206   | 0.05 |
| 0   | 204 | 206   | 0.05 |
| 2   | 170 | 206   | 0.05 |
| 2   | 150 | 206   | 0.05 |
| 0   | 157 | 207   | 0.05 | -->
