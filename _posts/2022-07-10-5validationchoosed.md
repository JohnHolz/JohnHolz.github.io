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

fn: Número de falsos negativos, queremos que seja 0
fp: Número de falsos positivos, apenas como metrica de desempate
pha_y: Número de positivos no dataset para ser previsto
thr: nível de significância que estamos utilizando pra classificar o asteroide como potencialmente perigoso (Threshold)

Utilizando a biblioteca sklearn dividimos em 10 o dataset e a cada iteração salvamos uma pequena sequencia de dados, depois de algumas horas de espera obtivemos os seguintes dados.

<table>
<tr><th> Ada </th><th> Random Fores  </th><th> Tensorflow  </th></tr>
<tr><td>

| fn  | fp    | pha_Y | thr  |
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
| 0   | 93026 | 207   | 0.05 |

</td><td>

| fn  | fp  | pha_Y | thr  |
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
| 0   | 157 | 207   | 0.05 |

</td><td>

| fn  | fp  | pha_Y | thr  |
| --- | --- | ----- | ---- |
| 52  | 9   | 207   | 0.5  |
| 4   | 62  | 207   | 0.5  |
| 54  | 5   | 207   | 0.5  |
| 35  | 1   | 207   | 0.5  |
| 99  | 0   | 207   | 0.5  |
| 75  | 5   | 206   | 0.5  |
| 29  | 20  | 206   | 0.5  |
| 15  | 38  | 206   | 0.5  |
| 28  | 11  | 206   | 0.5  |
| 17  | 12  | 207   | 0.5  |
| 0   | 102 | 207   | 0.05 |
| 0   | 226 | 207   | 0.05 |
| 0   | 106 | 207   | 0.05 |
| 0   | 105 | 207   | 0.05 |
| 6   | 27  | 207   | 0.05 |
| 0   | 50  | 206   | 0.05 |
| 0   | 129 | 206   | 0.05 |
| 0   | 183 | 206   | 0.05 |
| 3   | 136 | 206   | 0.05 |
| 0   | 126 | 207   | 0.05 |

</td></tr></table>

# Conclusão

Vemos que as métricas incrivelmente melhoraram, pois em cada interação do k-folds tem mais dados do que utilizamos na escolha dos modelos, o que mostra que fizemos um bom trabalho. Conseguimos um nível de qualidade de modelos muito bom,
otimizamos a nossa métrica de falsos negativos, chegamos em 0 e nosso caso que mais erramos no k-folds erramos pouquissimos dados.

Achei que no final seriamos derrotados pelo asteroide invísivel desfarçado de bonzinho mas conseguimos fazer os modelos acusarem.
