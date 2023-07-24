---
layout: post
title: "Projeto 2"
categories: Fonte
author:
  - João Holz
meta: "Ufes - IC 1 - Departamento de Estatística"
---

# Dados pessoais Netflix

Hoje com o mundo cada vez mais virtual, saimos da tv para o computador. Não sei se na tv conseguiriamos analisar tanto o usuário e seus interesses, mas certamente tentaremos procurar essas informações com apoio da Netflix. Veremos alguns padrões simples mas que nós trarão conclusões preciosas.

## Aquisição do dataset

Foi pedido o dataset pelo link de requisição. Estando logado você precisa apenas dar o aceite pelo email. Dentro do .Zip enviado temos:

| Titulo               | Descrição                                                                                |
| -------------------- | ---------------------------------------------------------------------------------------- |
| ACCOUNT              | Dados de login                                                                           |
| CONTENT_INTERACTION  | Dados de marketing e jornada de usuário                                                  |
| SURVEYS              | Pesquisas respondidas                                                                    |
| PROFILES             | Fotos de perfil e nomes                                                                  |
| MESSAGES             | Mensagens encaminhadas por email e notificação                                           |
| PAYTMANT             | Historico de Pagamento (Sem dados de cartão)                                             |
| GAMES                | dados relativos a serie jogo da netflix                                                  |
| DEVICES              | Equipamentos utilizados e acessos                                                        |
| IP_ADDRESSES         | Historico de IP de acessos                                                               |
| Folha de capa.pdf    | Descrição detalhada em portugues dos dados exportados                                    |
| Dados adicionais.pdf | Dados gerais faltantes do documento Folha de capa e informações adiquiridas de terceiros |

## Foco da Analise

Como temos muitos arquivos e muitos deles podem até ser metadata. Vamos focar em Views é a vizualicação do Vídeo. Clickstream a contagem de clicks e interações, e algumas informações por curiosidade.
Como os nomes dos perfils são meus familiares que dividem a conta vão aparecer muitas vezes vou tabelar quem é cada perfil pra ficar de mais facil referenciar depois.

Nome do Perfil|Parentesco
Ana Cecilia| Irmã
Luciana| Mãe
João|Eu
Pedro Henrique| Irmão
Infantil | Perfil utilizado por primos mais novos e subrinhas

---

## Analise Exploratória de Dados

Analisando os dados de pesquisa vi que tinham dados falanado de tipo de aparelho, esse é o mapa de calor de perfil x aparelho. Retirei o perfil Infantil pois estava poluindo muito o grafico.  
E a partir daqui conseguimos retirar varias informações valiosas que serão de grande ajuda nas suposições que levantaremos.  
Vemos abaixo que todos meus familiares, exceto eu, tem mais uso na SmartTV, quando a tv da sala não era smart, até quebrar. Meu irmão deixava o PS4 (Playstation4 - Video Game) na sala, o que justifica o alto uso pela minha irmã. Com a adoção da Smart TV isso diminui.  
Eu como assisto mais utilizando o computador, a partir de um monitor fica registrado como HTML5.
Outra observação interessante é que quase não tem uso pelo celular, um pouco visto por Iphone por Ana e um pouco visto por Android pelo Pedro.

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/heatmap_search.png)

O grafico abaixo é do dataset de clickstream, que tem dados do click/interação do usuário, a partir dessas informações podemos criar a hipotese dela ser a pessoa que mais pausa o video enquanto está assistindo. Por outro lado temos meu irmão que deve pausar pouco por utilizar o video game para acessar a netflix, então podemos criar outras suposições. Pode ser mais dificil interagir ou como o equipamento não é proprio, o sistema pode registrar um numero menor de dados.

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/pieplot_clickstream.png)

---

### Conteudo

Utilizando o dataset View, onde fica registrado o conteudo visualizado fizemos uma tabela para ver o conteudo mais assistido por cada um dos perfis.
Os dados continham temporada e episodio. Utilizando manipulação de strings retirei e mantive apenas o nome da série.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Country</th>
    </tr>
    <tr>
      <th>Profile Name</th>
      <th>title_clean</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Ana Cecília</th>
      <th>Brooklyn Nine-Nine</th>
      <td>1210</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">joão paulo</th>
      <th>How I Met Your Mother</th>
      <td>1020</td>
    </tr>
    <tr>
      <th>Friends</th>
      <td>927</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>Modern Family</th>
      <td>854</td>
    </tr>
    <tr>
      <th rowspan="5" valign="top">joão paulo</th>
      <th>BoJack Horseman</th>
      <td>767</td>
    </tr>
    <tr>
      <th>Dr. House</th>
      <td>752</td>
    </tr>
    <tr>
      <th>The Office (U.S.)</th>
      <td>586</td>
    </tr>
    <tr>
      <th>Rick and Morty</th>
      <td>560</td>
    </tr>
    <tr>
      <th>Brooklyn Nine-Nine</th>
      <td>553</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>Julie and the Phantoms</th>
      <td>543</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Apenas um Show</th>
      <td>383</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>Arrow</th>
      <td>372</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">Ana Cecília</th>
      <th>Barbie Life in the Dreamhouse</th>
      <td>367</td>
    </tr>
    <tr>
      <th>Suits</th>
      <td>362</td>
    </tr>
    <tr>
      <th>That '70s Show</th>
      <td>305</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Family Guy</th>
      <td>302</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>Brooklyn Nine-Nine</th>
      <td>282</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">joão paulo</th>
      <th>Seinfeld</th>
      <td>281</td>
    </tr>
    <tr>
      <th>Sons of Anarchy</th>
      <td>280</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">pedro henrique</th>
      <th>That '70s Show</th>
      <td>273</td>
    </tr>
    <tr>
      <th>The Walking Dead</th>
      <td>273</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Gravity Falls</th>
      <td>262</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>Brilhante Victória</th>
      <td>258</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>The Flash</th>
      <td>244</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>The Vampire Diaries</th>
      <td>241</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>That '70s Show</th>
      <td>235</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>Lucifer</th>
      <td>221</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>How I Met Your Mother</th>
      <td>220</td>
    </tr>
    <tr>
      <th>luciana</th>
      <th>Era uma vez</th>
      <td>217</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>The 100</th>
      <td>213</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>Pretty Little Liars</th>
      <td>191</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Neon Genesis Evangelion</th>
      <td>178</td>
    </tr>
    <tr>
      <th>luciana</th>
      <th>Elementary</th>
      <td>175</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>Vikings</th>
      <td>174</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>Scandal</th>
      <td>167</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Hora de Aventura</th>
      <td>165</td>
    </tr>
    <tr>
      <th>luciana</th>
      <th>Grimm</th>
      <td>165</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Naruto Shippuden</th>
      <td>152</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>Arrested Development</th>
      <td>151</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Um maluco no pedaço</th>
      <td>150</td>
    </tr>
    <tr>
      <th>luciana</th>
      <th>Ponto Cego</th>
      <td>148</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Hunter X Hunter (2011)</th>
      <td>144</td>
    </tr>
    <tr>
      <th>Ana Cecília</th>
      <th>Três é Demais</th>
      <td>143</td>
    </tr>
    <tr>
      <th>pedro henrique</th>
      <th>Star Wars: The Clone Wars</th>
      <td>141</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>Gotham</th>
      <td>137</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">Ana Cecília</th>
      <th>The Originals</th>
      <td>137</td>
    </tr>
    <tr>
      <th>Gossip Girl</th>
      <td>127</td>
    </tr>
    <tr>
      <th>luciana</th>
      <th>Outlander</th>
      <td>121</td>
    </tr>
    <tr>
      <th>joão paulo</th>
      <th>The Seven Deadly Sins</th>
      <td>120</td>
    </tr>
    <tr>
      <th>luciana</th>
      <th>Riverdale</th>
      <td>113</td>
    </tr>
  </tbody>
</table>

Conseguimos assim identificar as series preferidas de cada 1. Ana Cecília e "Brooklyn Nine-Nine", Luciana o registro mais alto é de "Era uma vez" (onde upon a time) mas não lembro dela assistindo num periodo recente, pode ter acabado as temporadas.  
Como eu por um tempo ia dormir e colocava How I met your mother pra passar ela esta em 1 posição mas a minha por muito tempo foi BoJack Horseman. Então podemos ter um estimador legal para series preferidas, pode esTar entre o top 3 das mais vistas.

---

### Heatmaps

Pelo heatmap da minha irmã vemos os principais horarios da semana que ela utiliza a netflix.

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/heatmap_ana.png)

Analisando meu heatmap vejo que existe um possivel ruído, quando vou dormir eu deixo a serie passando e pego no sono. O que faz com que continue por até 90 minutos. Então analisando o heatmap vemos um traço que leva até o começo da madrugada. PS: Tento me deitar antes das 00:00.

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/heatmap_joao.png)

O Heatmap de luciana vemos ele bem claro. Como ela assiste quase que somente na sala. Vemos perfeitamente seus horarios de uso. As vezes meio dia no almoço com minha irmã, outra coisa que pode gerar ruído pois quando estão assistindo juntas geram dados apenas para 1 perfil.

![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/heatmap_luciana.png)

## Conclusão da EDA

A partir dos mapas de calor da Hora X Dia-da-semana vemos que Luciana dorme cedo e utiliza quase exclusivamente na sala o serviço. Minha irmã pausa muito quando está assistindo, provavelmente para interagir com outra coisa.

## Próximo Artigo

Fazendo um modelo para os dados preparados.
