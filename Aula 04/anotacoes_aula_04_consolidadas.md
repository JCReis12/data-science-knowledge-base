# Aula 04 — Redes Neurais, AUC, Epoch, Random Forest e Amostragem

## 1. Redes neurais

### O que é uma rede neural?

Uma **rede neural artificial** é um modelo computacional inspirado, de forma simplificada, no funcionamento dos neurônios do cérebro humano.

A ideia é utilizar unidades matemáticas chamadas **neurônios artificiais** para receber informações, processá-las e produzir uma saída.

O primeiro modelo matemático de um neurônio artificial foi proposto em **1943**, por Warren McCulloch e Walter Pitts.

### Relação com o cérebro humano

No cérebro, os neurônios recebem sinais, processam essas informações e transmitem sinais para outros neurônios.

Em uma rede neural artificial, existe uma analogia:

| Cérebro humano | Rede neural artificial |
|---|---|
| Neurônio | Neurônio artificial |
| Sinais recebidos | Entradas |
| Conexões entre neurônios | Pesos |
| Processamento do sinal | Função matemática/ativação |
| Sinal de saída | Resultado do neurônio |

Essa comparação é uma **inspiração**, e não uma reprodução fiel do funcionamento biológico do cérebro.

---

## 2. Estrutura de uma rede neural

Uma estrutura básica pode ser representada como:

```text
ENTRADAS → CAMADAS OCULTAS → SAÍDA
```

### Camada de entrada

Recebe as características utilizadas pelo modelo.

Exemplo:

```text
Idade
Renda
Score
```

### Camadas ocultas

São responsáveis por realizar transformações e aprender padrões presentes nos dados.

Uma rede pode possuir:

- Uma camada oculta.
- Várias camadas ocultas.
- Diferentes quantidades de neurônios em cada camada.

### Camada de saída

Produz o resultado final desejado.

Em um problema de classificação binária, por exemplo:

```text
0 → Não inadimplente
1 → Inadimplente
```

A quantidade e o formato da saída dependem do tipo de problema.

---

## 3. Tipos de redes neurais

Existem diferentes arquiteturas de redes neurais, cada uma adequada a determinados tipos de problemas.

Alguns exemplos:

- **MLP (Multilayer Perceptron):** rede neural tradicional formada por camadas de neurônios.
- **CNN (Convolutional Neural Network):** muito utilizada em imagens e dados com estrutura espacial.
- **RNN (Recurrent Neural Network):** desenvolvida para lidar com sequências e dependências temporais.
- **LSTM:** arquitetura derivada das RNNs, utilizada para lidar melhor com dependências de longo prazo em sequências.
- **GRU:** outra arquitetura recorrente, geralmente mais simples que uma LSTM.
- **Transformers:** arquitetura baseada principalmente em mecanismos de atenção, muito utilizada atualmente em linguagem natural e outros tipos de dados sequenciais.

### Em aberto

A anotação apenas menciona que existem "tipos diferentes de rede neural", mas não define:

- Quais arquiteturas serão estudadas na disciplina.
- Qual é a diferença prática entre elas.
- Em quais situações cada arquitetura deve ser utilizada.
- Qual arquitetura será utilizada no projeto atual.

**Conclusão:** esse ponto precisa ser complementado conforme o conteúdo da disciplina e o projeto desenvolvido em aula.

---

# 4. AUC e curva ROC

A **AUC (Area Under the Curve)** é uma métrica utilizada principalmente para avaliar modelos de classificação.

Normalmente, quando falamos de AUC, estamos nos referindo à **área sob a curva ROC**, ou seja, **ROC-AUC**.

A curva ROC relaciona:

- **Taxa de Verdadeiros Positivos (TPR)**.
- **Taxa de Falsos Positivos (FPR)**.

A AUC representa a área sob essa curva.

### Interpretação simplificada

Quanto mais próxima de **1**, melhor tende a ser a capacidade do modelo de distinguir as classes.

Uma interpretação comum:

```text
AUC ≈ 0,5 → modelo pouco melhor que uma classificação aleatória
AUC > 0,5 → existe capacidade de discriminação
AUC → 1,0 → excelente capacidade de discriminação
```

Valores próximos de 0,5 indicam que o modelo tem pouca capacidade de separar as classes.

### Curva AUC/ROC

A anotação diz:

> "curva auc nunca é bonitinha, sempre com subidas e descidas"

A ideia está relacionada à curva ROC: ela é formada a partir de diferentes limiares de classificação e pode apresentar mudanças de direção.

Porém, é importante separar duas coisas:

- **A curva ROC** é o gráfico.
- **AUC** é um número que representa a área sob essa curva.

Portanto, não devemos dizer que a "AUC sobe ou desce" olhando diretamente para o gráfico. O que sobe e desce são os pontos da **curva ROC**; a AUC é calculada a partir dela.

### Em aberto

Ainda falta definir:

- Como calcular a ROC na prática.
- Como calcular a AUC.
- Como interpretar AUC em conjunto com outras métricas.
- Qual valor de AUC será considerado aceitável para o projeto.

---

# 5. Epoch

Uma **epoch** representa uma passagem completa pelo conjunto de dados de treinamento.

Exemplo:

Imagine um dataset com:

```text
300 registros
```

Se o treinamento utilizar os 300 registros uma vez:

```text
300 registros → treinamento → 1 epoch
```

Se forem executadas 10 epochs:

```text
Epoch 1 → dataset completo
Epoch 2 → dataset completo
Epoch 3 → dataset completo
...
Epoch 10 → dataset completo
```

Assim, o modelo terá passado pelos dados de treinamento **10 vezes**.

### Importante: epoch ≠ quantidade de atualizações

Se o treinamento utiliza **batch size**, uma epoch pode ser dividida em vários lotes.

Exemplo:

```text
Dataset = 300 registros
Batch size = 30

300 / 30 = 10 batches por epoch
```

Portanto:

```text
1 epoch = 10 batches
10 epochs = 100 batches
```

O modelo atualiza seus parâmetros a cada batch, e não somente no final da epoch.

### Em aberto

Ainda é necessário entender como a escolha de:

- `epoch`
- `batch size`
- `learning rate`

afeta o treinamento e pode causar **underfitting** ou **overfitting**.

---

# 6. Separação entre X e y

Considere um dataset utilizado para prever inadimplência:

| idade | renda | score | inadimplencia |
|---:|---:|---:|---:|
| 25 | 3000 | 650 | 0 |
| 42 | 5000 | 720 | 0 |
| 31 | 2200 | 500 | 1 |

O objetivo é prever:

```text
inadimplencia
```

Nesse caso, separamos os dados em:

### X — Variáveis de entrada

```text
X = idade + renda + score
```

### y — Variável alvo

```text
y = inadimplencia
```

Portanto:

```text
X → informações utilizadas para fazer a previsão
y → resposta que queremos prever
```

### Exemplo conceitual

```text
X
├── idade
├── renda
└── score

        ↓
    MODELO

        ↓

y
└── inadimplencia
```

Essa separação é fundamental em problemas de aprendizado supervisionado.

### Em aberto

É importante verificar se existem outras variáveis no dataset que possam causar **vazamento de dados (data leakage)**.

Também é necessário definir:

- Quais colunas realmente serão utilizadas em `X`.
- Qual coluna será o `y`.
- Se as variáveis precisam ser normalizadas/padronizadas.
- Como será feita a divisão entre treino, validação e teste.

---

# 7. Random Forest

O **Random Forest** é um algoritmo de aprendizado de máquina baseado em um conjunto de **árvores de decisão**.

Em vez de utilizar apenas uma árvore, o Random Forest cria várias árvores e combina seus resultados.

A ideia simplificada é:

```text
              Dataset
                 │
       ┌─────────┼─────────┐
       ↓         ↓         ↓
    Árvore 1  Árvore 2  Árvore 3
       │         │         │
       ↓         ↓         ↓
    Classe A   Classe B   Classe A
       └─────────┼─────────┘
                 ↓
             Votação
                 ↓
          Resultado final
```

Em classificação, as árvores podem votar em uma classe e o resultado final é determinado pela combinação dessas previsões.

### Por que "Random"?

A aleatoriedade está relacionada, entre outros aspectos, à seleção de amostras e subconjuntos de características utilizados pelas árvores.

Isso ajuda a produzir árvores diferentes e, consequentemente, um conjunto mais robusto.

### Random Forest x Rede Neural

São modelos diferentes.

**Random Forest:**

- Conjunto de árvores de decisão.
- Geralmente funciona muito bem com dados tabulares.
- É relativamente simples de utilizar.
- Pode fornecer informações sobre importância das características.

**Rede neural:**

- Utiliza neurônios artificiais organizados em camadas.
- Pode aprender relações bastante complexas.
- É muito utilizada em problemas como imagens, linguagem e outros dados complexos.
- Normalmente exige maior atenção a arquitetura e treinamento.

### Em aberto

A anotação apenas registra o algoritmo, então ainda falta definir:

- Como treinar um Random Forest.
- Como escolher o número de árvores.
- Quais hiperparâmetros serão utilizados.
- Como comparar Random Forest e Rede Neural no mesmo problema.
- Quais métricas serão utilizadas na comparação.

---

# 8. Amostragem

**Amostragem** é o processo de selecionar uma parte dos dados de uma população para realizar uma análise.

Existem diferentes métodos.

---

## 8.1 Amostragem aleatória simples

Cada elemento possui uma chance de ser selecionado.

Exemplo:

```text
População:
1, 2, 3, 4, 5, ..., 100

Amostra:
2, 53, 79, 14, 91
```

A seleção não segue uma ordem específica.

### Característica

É um método simples, mas pode não representar adequadamente a população quando existem grupos muito diferentes dentro dos dados.

---

## 8.2 Amostragem sistemática

Existe uma regra ou intervalo para selecionar os elementos.

Exemplo:

```text
1, 11, 21, 31, 41, 51...
```

Nesse exemplo, o intervalo é:

```text
10
```

A seleção segue uma lógica:

```text
primeiro elemento → 1
intervalo → 10
próximo → 11
próximo → 21
próximo → 31
```

### Característica

É simples de aplicar e organiza a seleção dos elementos.

---

## 8.3 Amostragem estratificada

Na **amostragem estratificada**, a população é dividida em grupos chamados **estratos**, geralmente com base em alguma característica relevante.

Depois, são selecionados elementos de cada estrato.

### Exemplo

Imagine uma população de clientes:

```text
Clientes
├── Baixa renda
├── Média renda
└── Alta renda
```

Em vez de selecionar clientes aleatoriamente sem considerar esses grupos, podemos selecionar uma quantidade de cada grupo.

Por exemplo:

```text
População:
60% baixa renda
30% média renda
10% alta renda

Amostra de 100 clientes:
60 baixa renda
30 média renda
10 alta renda
```

Dessa forma, a amostra mantém aproximadamente a proporção existente na população.

### Por que utilizar?

É especialmente útil quando a população possui grupos diferentes e queremos garantir que esses grupos estejam representados na amostra.

### Em aberto

Ainda é necessário estudar:

- Diferença entre amostragem estratificada proporcional e não proporcional.
- Quando escolher amostragem simples, sistemática ou estratificada.
- Como implementar esses métodos em Python.
- Como definir o tamanho adequado da amostra.

---

# 9. Divisão do dataset

A imagem mencionada nas anotações indica uma divisão do dataset.

O conceito normalmente utilizado em aprendizado de máquina é separar os dados em conjuntos diferentes.

Uma divisão comum é:

```text
                 DATASET
                    │
          ┌─────────┴─────────┐
          ↓                   ↓
       TREINO               TESTE
          │
     ┌────┴────┐
     ↓         ↓
  Treino    Validação
```

Uma abordagem possível seria:

```text
70% → treinamento
15% → validação
15% → teste
```

Os percentuais, porém, não são obrigatórios. Dependem do tamanho do dataset e da estratégia adotada.

### Treinamento

Utilizado para o modelo aprender os padrões dos dados.

### Validação

Utilizado para avaliar e ajustar escolhas durante o desenvolvimento do modelo, como hiperparâmetros.

### Teste

Utilizado para realizar uma avaliação final do modelo em dados que não foram utilizados no treinamento.

### Em aberto

O arquivo/imagem `divisao_do_dataset.png` foi mencionado nas anotações, mas não está disponível neste material.

Portanto, não é possível afirmar se a imagem apresentada em aula utilizava, por exemplo:

```text
70% / 30%
80% / 20%
70% / 15% / 15%
```

ou outra divisão.

**Recomendação:** adicionar a imagem original ao material e registrar exatamente a divisão ensinada pelo professor.

---

# 10. Fluxo geral do problema

Considerando o exemplo de inadimplência, podemos organizar o processo da seguinte maneira:

```text
                 DATASET
                    │
                    ↓
             Limpeza dos dados
                    │
                    ↓
             Separação X e y
              ┌─────┴─────┐
              ↓           ↓
              X           y
       características    alvo
              │           │
              └─────┬─────┘
                    ↓
             Divisão dos dados
                    │
          ┌─────────┼─────────┐
          ↓         ↓         ↓
       Treino    Validação   Teste
          │
          ↓
    Treinamento do modelo
          │
     ┌────┴───────────────┐
     ↓                    ↓
Rede Neural          Random Forest
     │                    │
     └─────────┬──────────┘
               ↓
        Avaliação dos modelos
               │
               ↓
       Métricas de desempenho
               │
        ┌──────┼──────────┐
        ↓      ↓          ↓
      AUC    Accuracy   Precision
               │
               ↓
         Escolha/validação
         do melhor modelo
```

---

# 11. Conceitos que precisam ser relacionados

Os assuntos da aula não devem ser estudados isoladamente.

A relação entre eles pode ser entendida assim:

### 1. Dataset

Temos os dados disponíveis.

### 2. Amostragem

Podemos selecionar dados de uma população utilizando diferentes estratégias.

### 3. X e y

Separamos as características (`X`) da variável que queremos prever (`y`).

### 4. Divisão do dataset

Separamos os dados em treino, validação e teste.

### 5. Modelo

Podemos utilizar, por exemplo:

- Rede Neural.
- Random Forest.

### 6. Treinamento

O modelo aprende utilizando os dados de treinamento.

No caso da rede neural, o treinamento ocorre durante várias **epochs**.

### 7. Avaliação

Utilizamos métricas como:

- AUC.
- Accuracy.
- Precision.
- Recall.
- F1-score.

### 8. Comparação

Podemos comparar modelos diferentes para descobrir qual apresenta melhor desempenho para o problema.

---

# 12. Pontos em aberto — resumo

| Tema | Situação | O que falta |
|---|---|---|
| Rede neural | Parcialmente estudado | Detalhar funcionamento do neurônio artificial e arquiteturas |
| Tipos de redes neurais | Em aberto | Identificar quais serão cobridos na disciplina e suas aplicações |
| AUC/ROC | Parcialmente estudado | Entender cálculo, interpretação e relação com outras métricas |
| Epoch | Estudado | Aprofundar relação com batch size e learning rate |
| X e y | Estudado | Verificar data leakage e preparação das variáveis |
| Random Forest | Introduzido | Aprofundar treinamento e hiperparâmetros |
| Amostragem aleatória simples | Estudado | Praticar implementação e entender limitações |
| Amostragem sistemática | Estudado | Praticar definição do intervalo |
| Amostragem estratificada | Em aberto | Aprofundar conceito, tipos e aplicação |
| Divisão do dataset | Em aberto | Confirmar o conteúdo da imagem e os percentuais ensinados |
| Treino/validação/teste | Parcialmente estudado | Entender quando e por que utilizar cada conjunto |
| Comparação de modelos | Em aberto | Definir métricas e estratégia de comparação |

---

# 13. Checklist para completar o conteúdo

- [ ] Revisar funcionamento de um neurônio artificial.
- [ ] Estudar pesos, bias e função de ativação.
- [ ] Identificar os principais tipos de redes neurais.
- [ ] Estudar a diferença entre classificação e regressão.
- [ ] Entender detalhadamente ROC e AUC.
- [ ] Praticar cálculo/interpretação de AUC.
- [ ] Entender epochs, batches e learning rate.
- [ ] Estudar overfitting e underfitting.
- [ ] Entender completamente a divisão `X` e `y`.
- [ ] Estudar data leakage.
- [ ] Estudar Random Forest e árvores de decisão.
- [ ] Comparar Random Forest e Redes Neurais.
- [ ] Revisar os três principais métodos de amostragem.
- [ ] Estudar amostragem estratificada.
- [ ] Confirmar a divisão apresentada na imagem `divisao_do_dataset.png`.
- [ ] Definir quais métricas serão utilizadas no projeto.
- [ ] Praticar a divisão entre treino, validação e teste em Python.

---

# 14. Resumo rápido

```text
REDE NEURAL
Entrada → Camadas ocultas → Saída

X
↓
Características usadas pelo modelo

y
↓
Variável que queremos prever

EPOCH
↓
Uma passagem completa pelo conjunto de treinamento

RANDOM FOREST
↓
Conjunto de várias árvores de decisão

ROC
↓
Curva que relaciona TPR e FPR

AUC
↓
Área sob a curva ROC

AMOSTRAGEM ALEATÓRIA
↓
Seleção sem uma regra de intervalo

AMOSTRAGEM SISTEMÁTICA
↓
Seleção seguindo um intervalo

AMOSTRAGEM ESTRATIFICADA
↓
Divisão da população em grupos e seleção dentro deles

DATASET
↓
Treino / Validação / Teste
```

---

## Observação final

Os principais pontos que permanecem **em aberto** são aqueles que dependem do conteúdo específico apresentado pelo professor ou de materiais que não foram incluídos nas anotações, principalmente a **imagem de divisão do dataset**, os **tipos de redes neurais que serão cobrados**, o aprofundamento de **AUC/ROC**, a **amostragem estratificada** e os detalhes práticos de **Random Forest e treinamento de redes neurais**.

Esses itens foram explicitamente separados para evitar transformar uma informação incompleta em uma afirmação incorreta.
