# 🏠 Spanish Housing Price Prediction

## 📖 Descrição

Este projeto tem como objetivo desenvolver um pipeline completo de Ciência de Dados para prever o preço de imóveis na Espanha utilizando técnicas de Machine Learning.

O projeto contempla todas as etapas de um fluxo de trabalho de Análise Preditiva, incluindo:

- Análise Exploratória dos Dados (EDA)
- Limpeza e Tratamento dos Dados
- Engenharia de Atributos (Feature Engineering)
- Preparação para Modelagem
- Treinamento e Avaliação de Modelos
- Versionamento do Modelo

O trabalho foi desenvolvido como parte da disciplina de **Análise Preditiva**.

---

# 🎯 Problema de Negócio

O mercado imobiliário possui diversos fatores que influenciam o valor de um imóvel, como localização, área construída, quantidade de quartos, banheiros, estado de conservação e infraestrutura.

O objetivo deste projeto é construir um modelo capaz de estimar o preço de imóveis com base nessas características, auxiliando processos de:

- Compra e venda de imóveis
- Avaliação imobiliária
- Investimentos
- Estudos de mercado

---

# 📂 Dataset

**Dataset utilizado:**

Spanish Housing Dataset

https://www.kaggle.com/datasets/thedevastator/spanish-housing-dataset-location-size-price-and

O conjunto de dados contém aproximadamente **100 mil imóveis** anunciados na Espanha, incluindo informações como:

- preço
- área construída
- área útil
- localização
- quartos
- banheiros
- elevador
- garagem
- piscina
- terraço
- estado do imóvel
- tipo do imóvel
- indicadores socioeconômicos da província

---

# 🛠 Tecnologias Utilizadas

- Python 3
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Statsmodels
- Joblib
- Jupyter Notebook

---

# 📊 Pipeline do Projeto

## Fase 1 — Análise Exploratória

Foram realizadas análises para compreender o comportamento dos dados:

- dimensão do dataset
- tipos das variáveis
- estatísticas descritivas
- identificação de valores ausentes
- distribuição da variável alvo
- correlação entre variáveis
- identificação de outliers

Gráficos utilizados:

- Histograma
- Boxplot
- Scatterplot
- Heatmap de Correlação

---

## Fase 2 — Limpeza dos Dados

As seguintes etapas foram realizadas:

- remoção de registros duplicados
- remoção de cabeçalhos repetidos
- tratamento de valores ausentes
- padronização de textos
- conversão de tipos
- tratamento de outliers
- remoção de colunas sem informação relevante

---

## Fase 3 — Feature Engineering

Foram criadas novas variáveis para enriquecer a análise:

- preço por metro quadrado
- banheiros por quarto
- índice de conforto

---

## Fase 4 — Preparação para Modelagem

Nesta etapa foram realizadas:

- seleção das variáveis
- One-Hot Encoding
- análise de multicolinearidade
- divisão Treino/Teste
- padronização utilizando StandardScaler

---

## Fase 5 — Modelagem

Foram treinados dois modelos:

- Regressão Linear
- Random Forest Regressor

Os modelos foram comparados utilizando:

- MAE
- MSE
- RMSE
- R²

Também foi realizada a análise de overfitting comparando os conjuntos de treino e teste.

---

## Fase 6 — Avaliação

O modelo final foi avaliado por meio de:

- MAE
- MSE
- RMSE
- R²

Também foram construídos gráficos de:

- Valores Reais × Valores Previstos
- Distribuição dos Resíduos
- Importância das Variáveis

---

# 📈 Modelo Escolhido

O modelo escolhido foi o:

**Random Forest Regressor**

A escolha foi baseada no menor RMSE e na melhor capacidade de generalização observada durante os testes.

---

# 📁 Estrutura do Projeto

```
spanish-housing-price-prediction/

│

├── data/
│   ├── raw/
│   ├── processed/
│   └── final/
│
├── models/
│   └── v1/
│       ├── modelo_random_forest_v1.pkl
│       └── metricas_v1.json
│
├── notebooks/
│   └── Projeto.ipynb
│
├── outputs/
│   └── figures/
│
├── src/ (opcional)
│
├── README.md
├── requirements.txt
├── LICENSE
└── .gitignore
```

---

# 📊 Métricas do Modelo

As métricas da versão **v1** encontram-se em:

```
models/v1/metricas_v1.json
```

São registradas automaticamente:

- MAE
- MSE
- RMSE
- R²
- Data de treinamento
- Lista das variáveis utilizadas

---

# 💾 Versionamento

Modelo atual:

```
v1
```

Arquivo:

```
models/v1/modelo_random_forest_v1.pkl
```

O projeto foi estruturado para permitir futuras versões:

```
models/
    v1/
    v2/
    v3/
```

preservando o histórico dos modelos treinados.

---

# 🚀 Como Executar

Clone o repositório:

```bash
git clone https://github.com/seuusuario/spanish-housing-price-prediction.git
```

Entre na pasta:

```bash
cd spanish-housing-price-prediction
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Abra o notebook:

```bash
jupyter notebook
```

Execute todas as células na ordem apresentada.

---

# 📌 Resultados

O projeto demonstrou que modelos baseados em árvores, especialmente o Random Forest Regressor, apresentam melhor desempenho para a previsão de preços de imóveis quando comparados à Regressão Linear.

Além disso, a análise exploratória evidenciou:

- forte assimetria da variável preço;
- presença de imóveis de alto padrão (outliers);
- influência significativa da área construída, quantidade de banheiros e localização sobre o preço dos imóveis.

---

# 🔮 Melhorias Futuras

As próximas versões poderão incluir:

- ajuste de hiperparâmetros com GridSearchCV;
- validação cruzada (Cross Validation);
- XGBoost Regressor;
- LightGBM;
- CatBoost;
- seleção automática de atributos;
- otimização do tratamento de outliers;
- implantação do modelo via API utilizando Flask ou FastAPI;
- criação de dashboard interativo com Streamlit.

---

# 👨‍💻 Autor

**Marcio Paiano de Souza**

Projeto desenvolvido para a disciplina de **Análise Preditiva** utilizando técnicas de Ciência de Dados e Machine Learning em Python.