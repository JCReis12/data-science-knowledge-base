# Resumo — CRISP-DM, Distribuições e Métricas de Classificação

## 1. CRISP-DM

O **CRISP-DM (Cross-Industry Standard Process for Data Mining)** é uma metodologia utilizada para estruturar projetos de **ciência de dados, mineração de dados e machine learning**.

Ele é dividido em **6 etapas principais**:

### 1. Entendimento do negócio

Definir e compreender o **problema de negócio** que será resolvido.

Nessa etapa devemos responder:

- Qual problema queremos resolver?
- Qual é o objetivo?
- O que será considerado sucesso?
- Quais são as restrições do projeto?

**Exemplo:** uma empresa quer identificar quais clientes possuem maior risco de inadimplência.

---

### 2. Entendimento dos dados

Coletar, explorar e compreender os dados disponíveis.

Atividades:

- Coleta dos dados;
- Identificação das fontes;
- Análise das variáveis;
- Verificação de valores ausentes;
- Identificação de inconsistências;
- Análise estatística;
- Visualização dos dados.

**Exemplo:** analisar idade, renda, histórico de pagamentos e número de empréstimos dos clientes.

---

### 3. Preparação dos dados

Transformar os dados para que possam ser utilizados na modelagem.

Pode envolver:

- Limpeza;
- Tratamento de valores nulos;
- Remoção de duplicidades;
- Tratamento de outliers;
- Transformação de variáveis;
- Normalização/padronização;
- Codificação de variáveis categóricas;
- Integração de diferentes fontes.

É uma das etapas que normalmente mais exige trabalho.

---

### 4. Modelagem

Aplicar técnicas de **Machine Learning/Data Mining** sobre os dados preparados.

Exemplos:

- Regressão;
- Árvores de decisão;
- Random Forest;
- KNN;
- Redes neurais;
- Clustering.

Também envolve:

- Escolha do algoritmo;
- Treinamento;
- Ajuste de hiperparâmetros;
- Comparação entre modelos.

---

### 5. Avaliação/Verificação

Verificar se o modelo realmente atende aos **objetivos definidos no entendimento do negócio**.

Não basta o modelo apresentar uma métrica alta. É necessário verificar se ele é adequado ao problema.

Podemos analisar:

- Accuracy;
- Precision;
- Recall;
- F1-score;
- Matriz de confusão;
- Curvas ROC/PR;
- Resultados de negócio.

---

### 6. Implantação

Colocar o resultado em utilização.

Pode significar:

- Colocar o modelo em produção;
- Criar uma API;
- Integrar o modelo a um sistema;
- Gerar relatórios;
- Criar dashboards;
- Entregar os resultados aos tomadores de decisão.

### 🔄 CRISP-DM é iterativo

As etapas **não precisam ser executadas apenas uma vez e em linha reta**.

Durante o projeto, novos problemas ou informações podem surgir.

Por exemplo:

```text
Modelagem → Avaliação → Preparação dos dados → Modelagem
```

Ou:

```text
Entendimento dos dados → Entendimento do negócio → Preparação dos dados
```

Portanto, o CRISP-DM é **flexível e iterativo**, podendo ser aplicado a diferentes tipos de problemas de análise e mineração de dados.

---

# 2. Classificação

Em problemas de classificação, o modelo tenta colocar cada registro em uma determinada **classe**.

### Exemplo

Uma instituição financeira quer classificar clientes como:

- **Bom pagador**
- **Mau pagador**

O modelo recebe os dados do cliente e tenta prever em qual dessas classes ele pertence.

---

# 3. Matriz de Confusão

Para entender as métricas de classificação, é importante conhecer:

| | Real Positivo | Real Negativo |
|---|---:|---:|
| **Previsto Positivo** | TP | FP |
| **Previsto Negativo** | FN | TN |

### TP — True Positive

O modelo previu positivo e **realmente era positivo**.

### TN — True Negative

O modelo previu negativo e **realmente era negativo**.

### FP — False Positive

O modelo previu positivo, mas **era negativo**.

Também chamado de **falso positivo**.

### FN — False Negative

O modelo previu negativo, mas **era positivo**.

Também chamado de **falso negativo**.

---

# 4. Accuracy — Acurácia

A **acurácia** mede a proporção de previsões que o modelo acertou em relação ao total de casos.

**Fórmula:**

```text
Accuracy = (TP + TN) / (TP + TN + FP + FN)
```

Em outras palavras:

> "De todos os casos que eu tinha, quantos eu classifiquei corretamente?"

### Exemplo

Temos **1.000 clientes**.

- 980 são bons pagadores;
- 20 são maus pagadores.

Imagine que o modelo simplesmente classifique **todos como bons pagadores**.

Ele acertará:

- 980 bons → acertos;
- 20 ruins → erros.

Logo:

```text
Accuracy = 980 / 1000
Accuracy = 98%
```

Aparentemente, o modelo possui uma excelente acurácia.

**Mas existe um problema.**

O modelo não conseguiu identificar **nenhum dos 20 maus pagadores**.

Isso demonstra por que a acurácia pode ser **enganosa em datasets desbalanceados**.

---

# 5. Precision — Precisão

A **precisão** responde:

> "Dos casos que o modelo classificou como positivos, quantos realmente eram positivos?"

**Fórmula:**

```text
Precision = TP / (TP + FP)
```

A precisão está relacionada à quantidade de **falsos positivos**.

Quanto maior a precisão, menor tende a ser a quantidade de falsos positivos.

### Exemplo

O modelo classificou 100 clientes como **maus pagadores**.

Porém, desses 100:

- 80 realmente eram maus pagadores;
- 20 eram bons pagadores.

Então:

```text
Precision = 80 / (80 + 20)
Precision = 80%
```

Ou seja:

> Quando o modelo diz que alguém é mau pagador, ele está correto em 80% das vezes.

---

# 6. Recall

O **Recall** responde:

> "Dos casos que realmente eram positivos, quantos o modelo conseguiu encontrar?"

**Fórmula:**

```text
Recall = TP / (TP + FN)
```

O recall está diretamente relacionado aos **falsos negativos**.

Quanto maior o recall, menos casos positivos reais são deixados de fora.

### Exemplo

Existem 100 maus pagadores.

O modelo conseguiu identificar 90 deles.

Então:

```text
Recall = 90 / 100
Recall = 90%
```

Ou seja:

> O modelo conseguiu encontrar 90% dos maus pagadores reais.

---

# 7. F1-Score

O **F1-score** combina **Precision e Recall** utilizando a **média harmônica**, e não uma média aritmética simples.

**Fórmula:**

```text
F1 = 2 × (Precision × Recall) / (Precision + Recall)
```

Ele é útil quando queremos um equilíbrio entre:

- **Precision**
- **Recall**

### Importante

> **F1-score não é a média entre acurácia e precisão.**

O correto é:

> **F1-score é a média harmônica entre Precision e Recall.**

---

# 8. Comparação das métricas

| Métrica | Pergunta principal | Prioriza |
|---|---|---|
| **Accuracy** | Quantos casos foram classificados corretamente? | Acertos gerais |
| **Precision** | Dos positivos previstos, quantos eram realmente positivos? | Evitar falsos positivos |
| **Recall** | Dos positivos reais, quantos foram encontrados? | Evitar falsos negativos |
| **F1-score** | Qual é o equilíbrio entre Precision e Recall? | Equilíbrio |

### Resumindo

**Accuracy:**

> "Quanto eu acertei no geral?"

**Precision:**

> "Quando digo que é positivo, posso confiar?"

**Recall:**

> "Consegui encontrar todos os positivos?"

**F1-score:**

> "Tenho um bom equilíbrio entre Precision e Recall?"

---

# 9. Qual métrica utilizar?

Depende do problema.

### Precision é mais importante quando:

Um **falso positivo é muito prejudicial**.

Exemplos:

- Sistema que classifica transações como fraude;
- Sistema que identifica candidatos para determinada ação;
- Situações em que falsos alarmes possuem alto custo.

### Recall é mais importante quando:

Um **falso negativo é muito prejudicial**.

Exemplos:

- Identificação de doenças;
- Detecção de fraudes;
- Identificação de maus pagadores, dependendo do objetivo.

### Accuracy pode ser suficiente quando:

As classes estão relativamente **balanceadas** e os erros possuem custos semelhantes.

### F1-score:

Útil quando queremos um **equilíbrio entre Precision e Recall**, principalmente em problemas com classes desbalanceadas.

---

# 10. Distribuição Gaussiana / Normal

A **distribuição normal**, também conhecida como **distribuição Gaussiana**, é uma distribuição estatística muito utilizada.

Ela possui o formato característico de uma **curva em sino**.

Suas principais características são:

- Simétrica;
- Média, mediana e moda coincidem;
- A maior concentração dos dados fica próxima da média.

---

## Regra 68–95–99,7

Na distribuição normal:

### ±1 desvio padrão

Aproximadamente **68%** dos dados estão dentro de:

```text
média ± 1 desvio padrão
```

### ±2 desvios padrão

Aproximadamente **95%** dos dados estão dentro de:

```text
média ± 2 desvios padrão
```

### ±3 desvios padrão

Aproximadamente **99,7%** dos dados estão dentro de:

```text
média ± 3 desvios padrão
```

Por isso é conhecida como **regra 68–95–99,7**.

---

# 11. Média e desvio padrão

## Média

Representa o valor central dos dados.

Exemplo:

```text
10, 20, 30, 40, 50

Média = 30
```

## Desvio padrão

Indica o quanto os dados estão **dispersos em relação à média**.

- Desvio padrão baixo → dados mais próximos da média;
- Desvio padrão alto → dados mais espalhados.

---

# 12. `loc`, `scale` e `lam`

Esses parâmetros aparecem bastante em bibliotecas estatísticas do Python.

## `loc`

Normalmente representa a **localização**, frequentemente a média em distribuições como a normal.

Exemplo:

```python
loc = 50
```

Significa que a distribuição está centrada em torno de 50, para a distribuição normal.

---

## `scale`

Normalmente representa a **escala**, que na distribuição normal corresponde ao **desvio padrão**.

Exemplo:

```python
scale = 10
```

Indica um desvio padrão de 10.

---

## `lam`

O parâmetro `lambda` (`lam`) aparece em algumas distribuições, como a **Poisson**.

Ele representa a **taxa ou número médio esperado de ocorrências**.

Exemplo:

```python
lam = 5
```

Pode representar uma média esperada de **5 ocorrências** em determinado intervalo.

> Portanto, `lam` não deve ser confundido com a média/desvio padrão da distribuição normal. Ele depende da distribuição utilizada.

---

# 13. Gráficos

Os gráficos são utilizados para **visualizar e compreender os dados**.

## Gráfico de barras

Utilizado para comparar categorias.

Exemplos:

- Quantidade de clientes por cidade;
- Quantidade de produtos por categoria.

## Gráfico de linhas

Utilizado para observar evolução ao longo do tempo.

Exemplos:

- Vendas por mês;
- Temperatura ao longo do dia.

## Gráfico de dispersão — Scatter Plot

Utilizado para observar a relação entre duas variáveis.

Exemplo:

```text
Renda × Valor do empréstimo
```

## Histograma

Utilizado para visualizar a **distribuição dos dados**.

Exemplo:

```text
Distribuição das idades dos clientes
```

## Boxplot

Utilizado para visualizar:

- Mediana;
- Quartis;
- Dispersão;
- Possíveis outliers.

---

# 14. Filtragem de dados

A filtragem consiste em selecionar apenas os registros que atendem a determinadas condições.

Exemplo conceitual:

```text
Selecionar clientes com idade > 18
```

Ou:

```text
Selecionar clientes com renda > R$ 3.000
```

Também podemos combinar condições:

```text
idade > 18 AND renda > 3000
```

Ou:

```text
cidade = "São Paulo" OR cidade = "Sorocaba"
```

Em Python/Pandas, por exemplo:

```python
df[df["idade"] > 18]
```

E com múltiplas condições:

```python
df[(df["idade"] > 18) & (df["renda"] > 3000)]
```

---

# 15. Conceito de "indeterminada"

Esse termo depende do contexto em que foi utilizado na aula.

Em problemas de **classificação**, geralmente trabalhamos com classes determinadas pelo modelo, mas pode existir uma situação em que o modelo não consegue determinar uma classe com confiança suficiente.

Nesse caso, é importante verificar o contexto específico em que o professor utilizou **"indeterminada"**, pois ela não é uma métrica padrão como Accuracy, Precision, Recall ou F1-score.

---

# 16. Resumo para prova

```text
CRISP-DM
1. Entendimento do negócio
2. Entendimento dos dados
3. Preparação dos dados
4. Modelagem
5. Avaliação
6. Implantação

↓

CLASSIFICAÇÃO

Accuracy
→ Acertos gerais

Precision
→ Dos positivos previstos, quantos realmente eram positivos?
→ Reduz falsos positivos

Recall
→ Dos positivos reais, quantos foram encontrados?
→ Reduz falsos negativos

F1-score
→ Equilíbrio entre Precision e Recall

↓

DISTRIBUIÇÃO NORMAL

68% → ±1 desvio padrão
95% → ±2 desvios padrão
99,7% → ±3 desvios padrão

loc
→ localização / média (na normal)

scale
→ desvio padrão (na normal)

lam
→ taxa/média esperada em distribuições como Poisson

↓

GRÁFICOS

Barras → comparação de categorias
Linhas → evolução temporal
Scatter → relação entre variáveis
Histograma → distribuição
Boxplot → dispersão e outliers

↓

FILTRAGEM

Selecionar registros
que atendem a condições específicas.
```
