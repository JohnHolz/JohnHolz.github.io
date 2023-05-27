---
layout: post
title: "Projeto 2"
categories: Fonte
author:
- João Holz
meta: "Ufes - IC 1 - Departamento de Estatística"
---

# Projeto 2 - Dados pessoais Netflix

Hoje com o mundo cada vez mais virtual, saimos da tv para o computador. Não sei se na tv conseguiriamos analisar tanto o usuário e seus interesses, mas certamente tentaremos procurar essas informações com apoio da Netflix. Veremos alguns padrões simples mas que nós trarão conclusões preciosas.


## Aquisição do dataset
Foi pedido o dataset pelo link de requisição. Estando logado você precisa apenas dar o aceite pelo email. Dentro do .Zip enviado temos:

Titulo|Descrição|
---|---
ACCOUNT|Dados de login
CONTENT_INTERACTION|Dados de marketing e jornada de usuário
SURVEYS|Pesquisas respondidas
PROFILES|Fotos de perfil e nomes
MESSAGES|Mensagens encaminhadas por email e notificação
PAYTMANT|Historico de Pagamento (Sem dados de cartão)
GAMES|dados relativos a serie jogo da netflix
DEVICES|Equipamentos utilizados e acessos
IP_ADDRESSES|Historico de IP de acessos
Folha de capa.pdf | Descrição detalhada em portugues dos dados exportados 
Dados adicionais.pdf | Dados gerais faltantes do documento Folha de capa e informações adiquiridas de terceiros

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



## Conclusão da EDA.
A partir dos mapas de calor da horaXdia-da-semana.



## Próximo Artigo
Fazendo um modelo para os dados preparados.



