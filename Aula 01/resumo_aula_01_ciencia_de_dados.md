# Resumo — Ciência de Dados | Aula 01

## 1. Estatística como base da Ciência de Dados

A estatística fornece fundamentos para **entender, resumir e analisar dados**. Na Ciência de Dados, esses conceitos são importantes principalmente nas etapas de entendimento e preparação dos dados.

---

## 2. Amostragem

Quando não é viável analisar toda uma população, podemos trabalhar com uma **amostra representativa**.

### Principais tipos

- **Amostragem Aleatória Simples:** todos os elementos possuem a mesma probabilidade de serem selecionados.
- **Amostragem Sistemática:** seleção de elementos seguindo intervalos fixos.
- **Amostragem Estratificada:** a população é dividida em grupos (estratos) e são selecionados elementos de cada grupo, ajudando a manter a representatividade.

---

## 3. Escalas de Medição

A natureza da variável influencia as operações estatísticas que podem ser realizadas.

| Escala | Característica | Exemplo |
|---|---|---|
| **Nominal** | Categorias sem ordem | Estado civil, cor dos olhos |
| **Ordinal** | Categorias com ordem | Satisfação: baixa, média, alta |
| **Intervalar** | Intervalos constantes, sem zero absoluto | Temperatura em °C |
| **Razão** | Possui zero absoluto e permite proporções | Idade, peso, renda |

---

## 4. Medidas Estatísticas

### Tendência central

- **Média:** soma dos valores dividida pela quantidade de elementos. É sensível a outliers.
- **Mediana:** valor central dos dados ordenados. É mais resistente a outliers.
- **Moda:** valor ou categoria que aparece com maior frequência.

### Quartis e percentis

- **Q1 / P25:** 25% dos dados estão abaixo desse valor.
- **Q2 / P50:** corresponde à mediana.
- **Q3 / P75:** 75% dos dados estão abaixo desse valor.

### Dispersão

- **Amplitude:** máximo − mínimo.
- **Variância:** mede a variabilidade dos dados em relação à média.
- **Desvio padrão:** raiz quadrada da variância e expressa a dispersão na mesma unidade dos dados.

---

# 5. CRISP-DM

O **CRISP-DM (Cross-Industry Standard Process for Data Mining)** é uma metodologia para estruturar projetos de **Ciência de Dados, Data Mining e Machine Learning**.

Diferentemente de um desenvolvimento de software tradicional, projetos de Ciência de Dados possuem caráter mais **experimental, não linear e baseado na validação de hipóteses**.

## As 6 fases

### 1. Business Understanding — Entendimento do Negócio

Define-se:

- objetivo do negócio;
- situação atual;
- metas de Ciência de Dados;
- plano do projeto.

É importante traduzir o problema de negócio em objetivos técnicos.

**Exemplo:** reduzir a inadimplência e criar um modelo capaz de identificar clientes de maior risco.

### 2. Data Understanding — Entendimento dos Dados

Envolve:

- coleta dos dados;
- descrição das variáveis;
- exploração dos dados (EDA);
- análise de distribuições e correlações;
- identificação de valores faltantes, outliers e desbalanceamento.

### 3. Data Preparation — Preparação dos Dados

Transforma os dados brutos em dados adequados para os modelos.

Pode envolver:

- seleção de dados;
- limpeza;
- tratamento de valores nulos;
- remoção de ruídos;
- engenharia de atributos (*Feature Engineering*);
- codificação de variáveis categóricas.

> Essa etapa pode consumir a maior parte do tempo de um projeto de Ciência de Dados.

### 4. Modeling — Modelagem

É a etapa de seleção e treinamento dos algoritmos.

Exemplos:

- Random Forest;
- XGBoost;
- Regressão Logística.

Também envolve validação e ajuste de hiperparâmetros.

### 5. Evaluation — Avaliação

Verifica-se se o modelo atende aos objetivos técnicos e de negócio.

Podem ser analisados:

- Matriz de Confusão;
- Precision;
- Recall;
- F1-Score;
- ROC-AUC;
- impacto financeiro / ROI.

### 6. Deployment — Implantação

É a operacionalização da solução, podendo envolver:

- APIs REST;
- Docker;
- nuvem;
- monitoramento;
- manutenção do modelo.

Também é importante acompanhar problemas como **Data Drift** e **Concept Drift**.

---

## 6. Custos Assimétricos e Classificação

Em problemas como análise de crédito, diferentes tipos de erro podem ter custos muito diferentes.

- **Falso Negativo (FN):** um cliente inadimplente é classificado como bom pagador.
- **Falso Positivo (FP):** um bom pagador é classificado como inadimplente.

Por isso, **Accuracy (Acurácia) sozinha pode ser inadequada**, principalmente em problemas com classes desbalanceadas. Dependendo do objetivo do negócio, o **Recall** pode ser uma métrica mais importante.

---

## 7. Fluxo geral

```text
Problema de Negócio
        ↓
Business Understanding
        ↓
Data Understanding
        ↓
Data Preparation
        ↓
Modeling
        ↓
Evaluation
        ↓
Deployment
        ↓
Monitoramento
```

O CRISP-DM é **cíclico**: os resultados de uma etapa podem indicar que é necessário voltar para uma etapa anterior.

---

# 8. Resumo rápido para estudar

| Conceito | Ideia principal |
|---|---|
| **Amostra** | Parte da população utilizada na análise |
| **Nominal** | Categoria sem ordem |
| **Ordinal** | Categoria com ordem |
| **Intervalar** | Intervalos constantes, sem zero absoluto |
| **Razão** | Possui zero absoluto |
| **Média** | Valor médio |
| **Mediana** | Valor central |
| **Moda** | Valor mais frequente |
| **Variância** | Mede a variabilidade |
| **Desvio padrão** | Mede a dispersão na unidade original |
| **CRISP-DM** | Metodologia para projetos de Data Mining/Ciência de Dados |
| **EDA** | Exploração dos dados |
| **Feature Engineering** | Criação/transformação de atributos |
| **Recall** | Importante quando é necessário identificar a maior parte dos positivos |
| **FN** | Positivo real classificado como negativo |
| **FP** | Negativo real classificado como positivo |
| **Data Drift** | Mudança na distribuição dos dados ao longo do tempo |
| **Concept Drift** | Mudança na relação entre entradas e resultado |

---

## 9. Ideia central da aula

A Ciência de Dados não consiste apenas em escolher um algoritmo. É necessário **entender o problema, compreender os dados, preparar os dados corretamente, modelar, avaliar os resultados e colocar a solução em operação**.

O **CRISP-DM** organiza esse processo, enquanto os fundamentos de estatística ajudam a interpretar e preparar os dados de maneira adequada.
