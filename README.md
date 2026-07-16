# 🏠 Spanish Housing Price Prediction

# Predição de Preços de Imóveis com Machine Learning


## Pipeline do projeto

| Fase | Descrição | Resultado |
|---|---|---|
| Extração | Download do dataset público de imóveis da Espanha. Devido ao tamanho do arquivo, a base original não é incluída no repositório e deve ser posicionada manualmente na pasta indicada. | `data/raw/spanish_houses.csv` |
| 1 — EDA | Análise da distribuição de preços, valores ausentes, outliers, variáveis categóricas, dispersões em relação ao alvo e matriz de correlação. | `outputs/figures/` |
| 2 — Limpeza | Padronização de textos, remoção dos anúncios de aluguel, exclusão de duplicatas, tratamento de preços inconsistentes e avaliação da qualidade das variáveis numéricas. | Base limpa |
| 3 — Feature engineering | Criação de `andar`, `exterior`, `floor_na`, `garage_included`, `rooms_per_m2`, `perc_area_util` e `price_log`. A variável `price_m2` foi utilizada apenas para análise, por ser derivada do alvo. | `data/processed/spanish_houses_processed.csv` |
| 4 — Preparação para modelagem | Seleção das variáveis finais, One-Hot Encoding, análise de VIF, remoção de variáveis redundantes, split 80/20, imputação pela mediana e StandardScaler aplicado com ajuste somente no treino. | `data/final/spanish_houses_final.csv` |
| 5 — Modelagem | Treinamento e comparação de Regressão Linear, KNN, Árvore de Decisão e Random Forest, com diagnóstico de overfitting pela comparação entre treino e teste. | Modelos treinados e tabela comparativa |
| 6 — Avaliação e versionamento | Cálculo de MAE, MSE, RMSE e R²; análise gráfica; interpretação em euros; escolha da Random Forest; retreino final com 100% dos dados e versionamento como v1. | `models/v1/` e `outputs/figures/` |

## Projeto 3 – Ciência de Dados
**Curso:** Ciência de Dados – SENAI  
**Autor:** Márcio Paiano de Souza

---
## Base de Dados

EsteEste  projeto utiliza a base de dados **Spanish Houses Dataset**, disponível publicamente.

Devido ao tamanho do arquivo (aproximadamente 94 MB), o dataset original não foi incluído neste repositório, seguindo as recomendações do GitHub para arquivos grandes.

### Estrutura esperada

Após realizar o download, coloque o arquivo na seguinte pasta:

```
data/raw/spanish_houses.csv
```

### Fonte dos dados

O dataset pode ser obtido em:

- Kaggle: https://www.kaggle.com/datasets/thedevastator/spanish-housing-dataset-location-size-price-and
- (ou o link exato de onde você baixou)

Após o download, execute o notebook principal para realizar todo o processo de limpeza, engenharia de atributos e treinamento dos modelos.


# Objetivo

Este projeto tem como objetivo desenvolver um modelo de Machine Learning capaz de prever o preço de imóveis a partir de suas características estruturais, localização e atributos do imóvel.

Durante o desenvolvimento foram aplicadas todas as etapas de um projeto de Ciência de Dados, incluindo:

- exploração dos dados;
- limpeza e tratamento da base;
- engenharia de atributos;
- análise de multicolinearidade;
- treinamento de diferentes modelos de regressão;
- comparação entre algoritmos;
- avaliação do desempenho;
- versionamento do modelo final.

---

# Base de dados

Foi utilizada a base de imóveis do **Idealista Espanha**, contendo informações sobre milhares de imóveis anunciados para venda.

As principais informações disponíveis incluem:

- preço do imóvel;
- área total;
- área útil;
- número de quartos;
- número de banheiros;
- tipo do imóvel;
- andar;
- garagem;
- elevador;
- piscina;
- jardim;
- varanda;
- localização (província, município, distrito e rua);
- certificado energético;
- diversas outras características do imóvel.

---

# Estrutura do projeto

```
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
│   └── projetofinal.ipynb
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

# Tecnologias utilizadas

O projeto foi desenvolvido em Python utilizando as bibliotecas:

- Pandas
- NumPy
- Matplotlib
- Scikit-Learn
- Joblib
- Jupyter Notebook

---

# Etapas do projeto

## 1. Análise exploratória

Inicialmente foi realizada uma análise exploratória dos dados para compreender:

- distribuição das variáveis;
- valores ausentes;
- tipos de dados;
- outliers;
- inconsistências;
- correlações.

Também foram produzidos gráficos descritivos para auxiliar na compreensão da base.

---

## 2. Limpeza dos dados

Foram realizados diversos tratamentos, incluindo:

- remoção de imóveis para aluguel;
- remoção de registros inconsistentes;
- tratamento de valores ausentes;
- remoção de duplicidades;
- padronização de textos;
- simplificação de variáveis categóricas.

Exemplos:

- variável **garage** transformada em variável binária (`garage_included`);
- variável **floor** decomposta em:
  - andar;
  - exterior;
  - floor_na;
- simplificação das categorias de condição do imóvel.

---

## 3. Engenharia de atributos

Foram criadas novas variáveis para melhorar a capacidade preditiva do modelo:

- percentual de área útil (`perc_area_util`);
- quartos por metro quadrado (`rooms_per_m2`);
- banheiros por quarto (`bath_per_room`);
- garagem incluída;
- andar;
- exterior;
- indicador de ausência de informação do andar.

Também foi realizada codificação One-Hot das variáveis categóricas.

---

## 4. Tratamento de valores ausentes

Os valores ausentes das variáveis numéricas foram preenchidos utilizando a **mediana**, estratégia escolhida por ser robusta à presença de outliers.

---

## 5. Seleção de variáveis

Foi realizada análise de multicolinearidade utilizando:

- matriz de correlação;
- VIF (Variance Inflation Factor).

Variáveis altamente correlacionadas foram removidas ou simplificadas para reduzir redundâncias.

---

## 6. Preparação para modelagem

Foi realizada:

- separação entre variáveis explicativas (X) e variável alvo (y);
- transformação logarítmica da variável alvo:

```python
price_log = np.log1p(price)
```

- divisão treino/teste (80/20);
- escalonamento das variáveis quando necessário.

---

# Modelos avaliados

Foram treinados quatro algoritmos de regressão:

- Regressão Linear
- KNN Regressor
- Árvore de Decisão
- Random Forest

---

# Métricas utilizadas

Os modelos foram comparados utilizando:

- MAE
- MSE
- RMSE
- R²

Além disso, foi realizada comparação entre treino e teste para verificar overfitting.

---

# Resultados

## Regressão Linear

|Conjunto|MAE|RMSE|R²|
|--------|------:|------:|------:|
|Treino|0.4411|0.5938|0.7833|
|Teste|0.4406|0.5845|0.7832|

Excelente capacidade de generalização.

---

## KNN

|Conjunto|MAE|RMSE|R²|
|--------|------:|------:|------:|
|Treino|0.4166|0.6182|0.7651|
|Teste|0.4568|0.6771|0.7091|

Apresentou desempenho inferior aos demais modelos.

---

## Árvore de Decisão

|Conjunto|MAE|RMSE|R²|
|--------|------:|------:|------:|
|Treino|0.3132|0.4809|0.8579|
|Teste|0.3771|0.5855|0.7824|

Apresentou leve overfitting.

---

## Random Forest

|Conjunto|MAE|RMSE|R²|
|--------|------:|------:|------:|
|Treino|0.1187|0.1869|0.9785|
|Teste|0.3181|0.5033|0.8392|

Foi o modelo de melhor desempenho.

Na escala original dos preços:

- **MAE:** € 139.308,43
- **RMSE:** € 382.600,19
- **R²:** 0,6264

---

# Modelo escolhido

O modelo campeão foi a **Random Forest**, pois apresentou:

- menor MAE;
- menor RMSE;
- maior R²;
- melhor desempenho geral no conjunto de teste.

---

# Principais variáveis importantes

A análise de importância das variáveis mostrou que os atributos com maior influência na previsão dos preços foram:

- número de banheiros;
- população da província;
- área do imóvel;
- tipo do imóvel;
- número de quartos;
- elevador;
- andar;
- garagem;
- características estruturais do imóvel.

---

# Avaliação gráfica

Foram construídos os seguintes gráficos:

- Valores Reais × Valores Previstos;
- Distribuição dos resíduos;
- Resíduos × Valores previstos;
- Importância das variáveis.

Os gráficos demonstraram boa capacidade de generalização do modelo e ausência de viés sistemático relevante.

---

# Versionamento

O modelo final foi salvo em:

```
models/v1/modelo_regressao_rf_final_v1.pkl
```

Também foi criado:

```
models/v1/metricas_v1.json
```

contendo:

- métricas de desempenho;
- data do treinamento;
- hiperparâmetros;
- lista das variáveis utilizadas.

---

# Como executar

Clone o projeto:

```bash
git clone https://github.com/MarcioPaiano/SENAI-Projeto3.git
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Abra o notebook:

```bash
jupyter notebook
```

ou

```bash
jupyter lab
```

Execute o notebook:

```
projetofinal.ipynb
```

---

# Possíveis melhorias

Como trabalhos futuros podem ser desenvolvidos:

- otimização de hiperparâmetros (Grid Search);
- validação cruzada;
- inclusão de novas variáveis geográficas;
- utilização de latitude e longitude;
- utilização de XGBoost;
- utilização de LightGBM;
- utilização de CatBoost;
- deploy do modelo utilizando Streamlit ou Flask.

---

# Conclusão

O projeto permitiu aplicar todas as etapas do processo de Ciência de Dados, desde a exploração e tratamento da base até a construção, avaliação e versionamento de modelos preditivos.

Entre os algoritmos avaliados, a **Random Forest** apresentou o melhor desempenho, demonstrando elevada capacidade preditiva e boa generalização para novos dados. Apesar da margem média de erro observada, o modelo mostrou-se adequado como ferramenta de apoio para estimativas preliminares de preços e análises do mercado imobiliário.

Além do desenvolvimento dos modelos, o projeto evidenciou a importância da qualidade dos dados, da engenharia de atributos e da comparação entre diferentes algoritmos para obtenção de resultados mais robustos e confiáveis.

# 👨‍💻 Autor

**Marcio Paiano de Souza**

Projeto desenvolvido para a disciplina de **Análise Preditiva** utilizando técnicas de Ciência de Dados e Machine Learning em Python.