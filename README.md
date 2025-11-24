# Projeto de Previsão de Séries Temporais - Grupo 2
## Previsão de Visualizações de Páginas da Wikipedia

---

## 📋 Visão Geral

Este projeto implementa uma solução completa de previsão de séries temporais para prever o número de visualizações futuras de páginas da Wikipedia. O projeto está dividido em 5 notebooks modulares que cobrem todas as etapas do processo de Data Science.

### Desafio
Prever o número de visualizações futuras considerando tendências e eventos especiais, utilizando dados históricos de tráfego web.

### Dataset
- **Fonte**: Web Traffic Time Series Forecasting (Kaggle) - Sample de 9 linhas
- **Período**: Julho 2015 - Dezembro 2016
- **Frequência**: Diária
- **Formato**: Séries temporais de visualizações por página

---

## 📚 Estrutura do Projeto

O projeto está organizado em 5 notebooks independentes e modulares:

### 1️⃣ **01_exploracao_dados.ipynb** (Etapa 1 - 20%)
**Coleta e Exploração de Dados**

Conteúdo:
- Carregamento e documentação do dataset
- Análise exploratória completa (EDA)
- Estatísticas descritivas
- Identificação de valores ausentes e outliers
- Análise de tendências e sazonalidade
- Decomposição de séries temporais
- Análise de autocorrelação (ACF/PACF)
- Visualizações interativas

Outputs:
- `dados_explorados.csv`: Dataset transformado para formato long

---

### 2️⃣ **02_preparacao_dados.ipynb** (Etapa 2 - 20%)
**Preparação e Tratamento dos Dados**

Conteúdo:
- **Limpeza de Dados**:
  - Imputação de valores ausentes (interpolação, forward fill, mediana)
  - Tratamento de outliers (Winsorização)
  - Remoção de inconsistências

- **Engenharia de Features**:
  - Features temporais (dia da semana, mês, trimestre)
  - Features cíclicas (seno/cosseno)
  - Features de lag (1, 7, 14, 30 dias)
  - Rolling window statistics (média, std, min, max)
  - Features de diferenciação

- **Normalização**:
  - StandardScaler (Z-score)
  - MinMaxScaler (0-1)

- **Divisão dos Dados**:
  - Train: 60%
  - Validation: 20%
  - Test: 20%
  - Respeitando ordem temporal

Outputs:
- `dados_limpos.csv`: Dataset com features
- `dados_padronizados.csv`: Dados com StandardScaler
- `dados_normalizados.csv`: Dados com MinMaxScaler
- `train_data.csv`, `val_data.csv`, `test_data.csv`: Conjuntos separados
- `metadata.json`: Metadados da preparação

---

### 3️⃣ **03_modelos_baseline_estatisticos.ipynb** (Etapa 3 Parte 1 - 15%)
**Modelos Baseline e Estatísticos**

Conteúdo:
- **Modelos Baseline**:
  - Naive (Persistência)
  - Média Móvel Simples (janelas de 7, 14, 30 dias)
  - Suavização Exponencial Simples (SES)

- **Modelos Estatísticos**:
  - ARIMA (com auto_arima para otimização)
  - SARIMA (sazonalidade semanal)
  - Holt-Winters (Triple Exponential Smoothing)

- **Métricas de Avaliação**:
  - MAE (Mean Absolute Error)
  - RMSE (Root Mean Squared Error)
  - MAPE (Mean Absolute Percentage Error)
  - R² (Coeficiente de Determinação)

Outputs:
- `baseline_statistical_comparison.csv`: Comparação dos modelos
- `baseline_statistical_results.pkl`: Resultados detalhados

---

### 4️⃣ **04_modelos_machine_learning.ipynb** (Etapa 3 Parte 2 - 15%)
**Modelos de Machine Learning**

Conteúdo:
- **Prophet (Facebook)**:
  - Detecção automática de tendências
  - Múltiplas sazonalidades
  - Robusto a outliers e dados ausentes

- **Regressão com Features Temporais**:
  - Ridge Regression
  - Random Forest
  - Gradient Boosting
  - XGBoost
  - Feature importance analysis

- **Deep Learning**:
  - LSTM (Long Short-Term Memory)
  - Arquitetura com dropout
  - Early stopping
  - Previsões iterativas

Outputs:
- `all_models_comparison.csv`: Comparação de todos os modelos
- `all_results.pkl`: Resultados completos
- `best_model.json`: Informações do melhor modelo

---

### 5️⃣ **05_avaliacao_final.ipynb** (Etapa 4 - 20%)
**Avaliação e Comparação de Modelos**

Conteúdo:
- **Análise Comparativa**:
  - Tabela comparativa completa
  - Rankings por métrica
  - Heatmaps de performance

- **Análise de Resíduos**:
  - Teste de normalidade (Shapiro-Wilk)
  - Teste de autocorrelação (Ljung-Box)
  - Q-Q plots
  - ACF dos resíduos

- **Validação Cruzada Temporal**:
  - Expanding Window
  - Avaliação de estabilidade

- **Seleção do Modelo Final**:
  - Justificativa detalhada
  - Pontos fortes e limitações
  - Recomendações para produção

- **Dashboard Executivo**:
  - Visualizações consolidadas
  - Sumário de resultados

Outputs:
- `relatorio_final.txt`: Relatório completo do projeto

---

## 🚀 Como Executar

### Pré-requisitos
```bash
# Python 3.9+
# Jupyter Notebook ou JupyterLab
```

### Instalação de Dependências

As dependências são instaladas automaticamente em cada notebook, mas você pode instalá-las manualmente:

```bash
pip install pandas numpy matplotlib seaborn plotly
pip install statsmodels pmdarima prophet
pip install scikit-learn xgboost
pip install tensorflow keras
```

### Ordem de Execução

Execute os notebooks na ordem numérica:

1. **01_exploracao_dados.ipynb**
   - Carregue o arquivo `train_1_sample.csv`
   - Execute todas as células

2. **02_preparacao_dados.ipynb**
   - Usa output do notebook anterior
   - Execute todas as células

3. **03_modelos_baseline_estatisticos.ipynb**
   - Usa outputs do notebook 2
   - Execute todas as células

4. **04_modelos_machine_learning.ipynb**
   - Usa outputs dos notebooks anteriores
   - Execute todas as células
   - ⚠️ LSTM pode demorar alguns minutos

5. **05_avaliacao_final.ipynb**
   - Consolida todos os resultados
   - Execute todas as células
   - Gera relatório final

---

## 📊 Modelos Implementados

### Baseline (3 modelos)
- ✅ Naive (Persistência)
- ✅ Média Móvel Simples
- ✅ Suavização Exponencial Simples

### Estatísticos (3 modelos)
- ✅ ARIMA
- ✅ SARIMA
- ✅ Holt-Winters

### Machine Learning (6 modelos)
- ✅ Prophet
- ✅ Ridge Regression
- ✅ Random Forest
- ✅ Gradient Boosting
- ✅ XGBoost
- ✅ LSTM (Deep Learning)

**Total: 12 modelos**

---

## 📈 Métricas de Avaliação

Todos os modelos são avaliados usando 4 métricas principais:

1. **MAE** (Mean Absolute Error)
   - Erro médio absoluto
   - Mesma unidade que a variável alvo
   - Interpretação direta

2. **RMSE** (Root Mean Squared Error)
   - Penaliza erros grandes
   - Sensível a outliers

3. **MAPE** (Mean Absolute Percentage Error)
   - Erro percentual médio
   - Independente de escala
   - Fácil interpretação

4. **R²** (Coeficiente de Determinação)
   - Proporção de variância explicada
   - Varia de 0 a 1 (maior = melhor)

---

## 🎯 Resultados Esperados

Após executar todos os notebooks, você terá:

### Arquivos Gerados
```
/
├── dados_explorados.csv
├── dados_limpos.csv
├── dados_padronizados.csv
├── dados_normalizados.csv
├── train_data.csv
├── val_data.csv
├── test_data.csv
├── metadata.json
├── baseline_statistical_comparison.csv
├── baseline_statistical_results.pkl
├── all_models_comparison.csv
├── all_results.pkl
├── best_model.json
└── relatorio_final.txt
```

### Insights
- Identificação do melhor modelo
- Comparação detalhada de performance
- Análise de resíduos
- Recomendações para produção

---

## 🔍 Principais Insights do Projeto

### 1. Sazonalidade
- Padrão semanal identificado nas visualizações
- Variação entre dias úteis e fins de semana

### 2. Tendências
- Tendências de longo prazo capturadas
- Mudanças de comportamento ao longo do tempo

### 3. Features Importantes
- Lags de 7, 14 e 30 dias
- Médias móveis
- Features cíclicas (dia da semana, mês)

### 4. Performance dos Modelos
- Modelos de ML geralmente superam baseline
- LSTM e XGBoost tendem a ter boa performance
- Prophet é robusto e fácil de usar

---

## 📋 Checklist de Qualidade

### Análise Exploratória ✅
- [x] Estatísticas descritivas completas
- [x] Visualizações de tendências
- [x] Identificação de sazonalidade
- [x] Análise de autocorrelação
- [x] Detecção de outliers

### Preparação de Dados ✅
- [x] Tratamento de valores ausentes
- [x] Tratamento de outliers
- [x] Engenharia de features
- [x] Normalização/Padronização
- [x] Divisão temporal correta

### Modelagem ✅
- [x] Modelos baseline implementados
- [x] Modelos estatísticos (ARIMA, SARIMA, HW)
- [x] Modelos de ML (Prophet, XGBoost, RF, etc)
- [x] Deep Learning (LSTM)
- [x] Otimização de hiperparâmetros

### Avaliação ✅
- [x] Múltiplas métricas calculadas
- [x] Comparação visual de modelos
- [x] Análise de resíduos
- [x] Validação cruzada temporal
- [x] Seleção e justificativa do melhor modelo

---

## 📚 Referências

### Documentação
- [Statsmodels](https://www.statsmodels.org/)
- [Prophet](https://facebook.github.io/prophet/)
- [XGBoost](https://xgboost.readthedocs.io/)
- [TensorFlow/Keras](https://www.tensorflow.org/)

### Datasets
- [Kaggle: Web Traffic Time Series Forecasting](https://www.kaggle.com/c/web-traffic-time-series-forecasting)

### Papers

- Box, G. E., & Jenkins, G. M. (1976). Time series analysis: forecasting and control
- Taylor, S. J., & Letham, B. (2018). Forecasting at scale (Prophet paper)
- Hochreiter, S., & Schmidhuber, J. (1997). Long short-term memory (LSTM paper)
