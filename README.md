# Modelos Previsão do Etanol no Brasil

> **Resumo:** Aplicação de modelos Lineares e não-lineares para a previsão de série de preços do Etanol no estado de São Paulo/Brasil.

---

## O Desafio
O estado de São Paulo é um grande produtor de etanol, devido a alta volatilidade dos preços, a sazonalidade forte (safra e entressafra), influências do preço de petróleo, taxa de câmbio, preço do açúcar e políticas governamentais causam grande impecilhos na previsibilidade.  

O objetivo deste projeto foi responder a uma pergunta central: **"É possível comparar modelos lineares e não lineares, e são capazes de capturar tanto padrões simples quanto dinâmicas complexas da série temporal, garantindo boa capacidade preditiva e generalização?."**

## Modelos utilizados
1. Modelos de Machine Learning:
- Ridge
- Lasso
- Linear Regression
- Random Forest
- LightGBM
- KNN
- MLP
2. Modelo LSTM - Deep Learning
3. Modelo SARIMA

## A Matéria-Prima (Coleta de Dados)
1. Para construir este modelo, criei um excel com os preços de etanol: base_de_dados_etanol.csv
* ** Fonte: CEPEA
* Período: 2015 a 2025
* Frequência: mensal
* Variável principal: preço do etanol (R$ e US$)
2. * ** No código Machine_learning_models, gerei um excel: analise_desempenho.csv

## Desenvolvimento
Início → tratou a série temporal → aplicou diferentes modelos (lineares, ML e deep learning) → avaliou → comparou os resultados. Os resultados, foram:
.


## Métricas de Desempenho
Utilizei várias métricas:
MAE
RMSE
MAPE
sMAPE

## Feature Engineering Agronômico
O maior salto de precisão do modelo ocorreu quando deixei de tratar os dados como meros números e apliquei **conhecimento de negócio**. Traduzi o ciclo fenológico da soja para a IA, criando variáveis específicas:

1. **Chuva de Plantio (Set-Nov):** Onde a semente precisa germinar.
2. **Período de Seca (Jun-Ago):** Onde o déficit hídrico já é o padrão esperado.
3. **Enchimento de Grãos (Dez-Mar):** Fases reprodutivas (R5 e R6), cruciais para o peso final da vagem.

Dessa forma ao invés de um dataset com várias colunas separadas por meses, cheguei a um dataset definitivo que traduzia os intervalos de meses em que estavam ocorrendo o ciclo fenológico da soja.

## Resultados e Validação no Mundo Real (Safra 2024)
O modelo final alcançou resultados expressivos nos dados de teste, considerando que o que queria aqui era tentar prever algo que depende de diversas váriaveis,
mas a verdadeira prova de fogo foi tentar prever a **Safra de 2024** (um ano marcado por forte anomalia climática). Como o IBGE (SIDRA) disponibiliza até 2024, foi uma ótima oportunidade para ver como o modelo estava se saindo
em comparação a dados reais.

> Os resultados:

* **Erro Absoluto Médio (MAE):** ~283 kg/ha no histórico.
* **Previsão Cega (2024):** O modelo errou por apenas **141,61 kg/ha** (cerca de 2,3 sacas por hectare).

Os resultados foram em muito satisfatórios considerando as features usada (a feature no caso), um modelo que erra aproximadamente em 283 kg de soja por hectare, ou seja ~4,5 sacas de soja,
uma margem de 8% deerro considerando que a produtividade média recente em Mato Grosso passa dos 3.500 kg/ha (66 sacas).

Abaixo, o gráfico demonstra como a linha da IA acompanha a realidade do IBGE ao longo das décadas, detectando as quebras de safra:

![Gráfico comparativo entre IA e Realidade](grafico_previsao_soja_mt.png)

## Tecnologias Utilizadas
* **Python:** Linguagem principal
* **Pandas & NumPy:** Limpeza, formatação e Feature Engineering
* **Scikit-Learn:** Separação de dados e treinamento do Random Forest
* **Matplotlib & Seaborn:** Data Storytelling e visualização
* **Requests:** Consumo de APIs REST (NASA e IBGE)

---
*Projeto desenvolvido para estudo e aplicação de Data Science no Agronegócio.*
