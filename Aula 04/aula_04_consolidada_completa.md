# Aula 04 — Redes Neurais, Random Forest, AUC, Epoch e Amostragem

## 1. Redes Neurais Artificiais

### O que é uma rede neural?

Uma **rede neural artificial (RNA)** é um modelo computacional inspirado, de forma simplificada, no funcionamento dos neurônios do cérebro humano.

Ela é utilizada em **Machine Learning** para aprender padrões a partir de dados e, depois do treinamento, realizar previsões ou classificações.

A ideia básica é:

```text
Dados de entrada
       ↓
Processamento
       ↓
Aprendizado de padrões
       ↓
Resultado / previsão
```

As redes neurais são formadas por unidades chamadas **neurônios artificiais**, organizadas em camadas.

---

## 2. Relação entre o neurônio humano e o neurônio artificial

No cérebro humano, os neurônios recebem sinais de outros neurônios, processam essas informações e transmitem novos sinais.

O neurônio artificial foi inspirado nessa ideia.

Em 1943, **Warren McCulloch e Walter Pitts** apresentaram um modelo matemático de neurônio artificial.

A comparação é simplificada:

| Neurônio biológico | Neurônio artificial |
|---|---|
| Recebe sinais | Recebe entradas |
| Conexões entre neurônios | Pesos |
| Processa os sinais | Operação matemática |
| Produz um sinal | Produz uma saída |

O neurônio artificial não reproduz o funcionamento real do cérebro. Ele utiliza uma abstração matemática inspirada nessa ideia.

---

## 3. Como funciona um neurônio artificial?

Um neurônio recebe várias entradas.

Por exemplo:

```text
x₁ = idade
x₂ = renda
x₃ = score
```

Cada entrada possui um **peso**, que representa a importância daquela entrada para o cálculo.

```text
x₁ ── w₁ ──┐
x₂ ── w₂ ──┼──> Neurônio ──> Saída
x₃ ── w₃ ──┘
```

O neurônio realiza uma soma ponderada:

```text
z = x₁w₁ + x₂w₂ + x₃w₃ + b
```

Onde:

- `x` = entrada;
- `w` = peso;
- `b` = bias;
- `z` = resultado da combinação das entradas.

Depois, esse resultado passa por uma **função de ativação**:

```text
saída = função_de_ativação(z)
```

O modelo aprende modificando os pesos e o bias durante o treinamento.

---

# 4. Estrutura de uma rede neural

Uma rede neural pode ser representada como:

```text
ENTRADA → CAMADAS OCULTAS → SAÍDA
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

São responsáveis pelo processamento das informações e pela identificação de padrões.

Uma rede pode ter:

- uma camada oculta;
- várias camadas ocultas;
- diferentes quantidades de neurônios em cada camada.

Quanto mais complexa a rede, maior pode ser sua capacidade de aprender relações complexas, mas também aumenta a necessidade de dados, processamento e ajuste adequado.

### Camada de saída

Produz o resultado final.

Em uma classificação binária:

```text
0 → Não inadimplente
1 → Inadimplente
```

---

# 5. Tipos de redes neurais

Existem diversas arquiteturas de redes neurais.

## 5.1 MLP — Multilayer Perceptron

É uma rede neural formada por camadas de neurônios conectadas.

Estrutura:

```text
Entrada → Camada oculta → Camada oculta → Saída
```

É bastante utilizada para problemas com dados tabulares e classificação/regressão.

---

## 5.2 CNN — Convolutional Neural Network

As **CNNs** são redes neurais convolucionais.

São muito utilizadas em:

- imagens;
- reconhecimento facial;
- classificação de imagens;
- visão computacional;
- detecção de objetos.

Elas conseguem identificar padrões espaciais, como bordas, formas e objetos.

---

## 5.3 RNN — Recurrent Neural Network

As **RNNs** são redes recorrentes, desenvolvidas para trabalhar com dados sequenciais.

Exemplos:

- séries temporais;
- textos;
- sequências de eventos;
- dados de sensores.

Elas consideram informações relacionadas à sequência dos dados.

---

## 5.4 LSTM

A **LSTM (Long Short-Term Memory)** é uma arquitetura baseada em RNN criada para lidar melhor com dependências de longo prazo.

É utilizada, por exemplo, em:

- séries temporais;
- processamento de linguagem;
- previsão de sequências.

---

## 5.5 GRU

A **GRU (Gated Recurrent Unit)** também é uma arquitetura recorrente.

Possui uma estrutura mais simples que a LSTM e pode apresentar bom desempenho em problemas sequenciais.

---

## 5.6 Transformers

Transformers utilizam principalmente mecanismos de **atenção** para processar relações entre elementos de uma sequência.

São muito utilizados atualmente em:

- processamento de linguagem natural;
- tradução;
- geração de texto;
- modelos de linguagem;
- visão computacional.

---

# 6. Aprendizado da rede neural

Durante o treinamento, a rede recebe os dados e produz uma previsão.

Essa previsão é comparada com o resultado correto.

```text
Entrada
   ↓
Rede neural
   ↓
Previsão
   ↓
Comparação com o valor real
   ↓
Erro
   ↓
Ajuste dos pesos
   ↓
Novo treinamento
```

Esse processo acontece repetidamente.

O objetivo é encontrar valores de pesos que permitam à rede produzir previsões cada vez melhores.

Um dos mecanismos utilizados para ajustar os pesos é o **backpropagation**, normalmente combinado com um algoritmo de otimização, como o **Gradient Descent** ou variantes como Adam.

---

# 7. Epoch

Uma **epoch** representa uma passagem completa pelo conjunto de dados de treinamento.

Imagine um dataset com:

```text
300 registros
```

Se os 300 registros forem utilizados uma vez para treinar a rede:

```text
300 registros → treinamento → 1 epoch
```

Se forem utilizadas 10 epochs:

```text
Epoch 1 → dataset completo
Epoch 2 → dataset completo
Epoch 3 → dataset completo
...
Epoch 10 → dataset completo
```

Portanto, os dados de treinamento foram apresentados ao modelo 10 vezes.

---

## 7.1 Epoch, batch e iteração

Uma epoch pode ser dividida em **batches**.

Imagine:

```text
Dataset = 300 registros
Batch size = 30
```

Então:

```text
300 / 30 = 10 batches
```

Logo:

```text
1 epoch = 10 batches
```

Se forem utilizadas 20 epochs:

```text
20 × 10 = 200 atualizações
```

Assim:

- **Epoch:** passagem completa pelo dataset de treinamento.
- **Batch:** pequeno conjunto de dados processado de uma vez.
- **Iteração/step:** processamento de um batch e, normalmente, uma atualização dos parâmetros.

---

# 8. Learning Rate

O **learning rate** define o tamanho do passo utilizado para atualizar os parâmetros do modelo durante o treinamento.

Simplificando:

```text
Learning rate muito baixo
→ aprendizado muito lento

Learning rate muito alto
→ pode passar do ponto ideal
→ treinamento pode ficar instável

Learning rate adequado
→ aprendizado mais eficiente
```

O learning rate é um **hiperparâmetro**, ou seja, normalmente é definido antes ou durante o processo de treinamento e não é aprendido diretamente pela rede como os pesos.

---

# 9. Overfitting e Underfitting

## Overfitting

Acontece quando o modelo aprende muito bem os dados de treinamento, inclusive características específicas ou ruídos, mas apresenta desempenho ruim em dados novos.

Exemplo:

```text
Treinamento → 98%
Teste       → 70%
```

Pode ser um sinal de overfitting.

## Underfitting

Acontece quando o modelo é simples demais ou não foi treinado adequadamente e não consegue aprender suficientemente os padrões dos dados.

Exemplo:

```text
Treinamento → 65%
Teste       → 63%
```

Nesse caso, o modelo pode estar tendo dificuldade até mesmo para representar os dados de treinamento.

---

# 10. Dataset de entrada e saída: X e y

Considere um dataset utilizado para prever inadimplência:

| idade | renda | score | inadimplencia |
|---:|---:|---:|---:|
| 25 | 3000 | 650 | 0 |
| 42 | 5000 | 720 | 0 |
| 31 | 2200 | 500 | 1 |
| 55 | 2800 | 450 | 1 |

O objetivo é prever a coluna:

```text
inadimplencia
```

Então separamos os dados.

## X — Variáveis de entrada

```text
X = idade + renda + score
```

## y — Variável alvo

```text
y = inadimplencia
```

Em código Python, utilizando pandas:

```python
X = df[["idade", "renda", "score"]]
y = df["inadimplencia"]
```

Assim:

```text
X → informações utilizadas pelo modelo
y → resposta que o modelo deve aprender a prever
```

---

# 11. Classificação binária

O exemplo de inadimplência é um problema de **classificação binária**, porque existem duas possibilidades:

```text
0 → Não inadimplente
1 → Inadimplente
```

O modelo recebe as características do cliente:

```text
idade
renda
score
```

e tenta prever:

```text
inadimplencia
```

Por exemplo:

```text
Entrada:
idade = 35
renda = 3000
score = 580

       ↓

Modelo

       ↓

Probabilidade de inadimplência = 0,78

       ↓

Classificação:
Inadimplente
```

O limiar utilizado para transformar uma probabilidade em classe pode ser alterado dependendo do problema.

---

# 12. Divisão do dataset

Não devemos utilizar todos os dados disponíveis diretamente para treinar e avaliar o mesmo modelo.

Se o modelo for treinado e avaliado exatamente nos mesmos dados, a avaliação pode ficar artificialmente otimista.

Por isso, normalmente dividimos o dataset.

Uma divisão possível é:

```text
Dataset
│
├── Treinamento
├── Validação
└── Teste
```

Um exemplo:

```text
70% → Treinamento
15% → Validação
15% → Teste
```

Outra possibilidade:

```text
80% → Treinamento
20% → Teste
```

A proporção não é fixa. Deve ser escolhida de acordo com o problema, tamanho do dataset e estratégia de validação.

---

## 12.1 Conjunto de treinamento

Utilizado para o modelo aprender.

```text
Dados de treinamento
       ↓
Aprendizado dos padrões
       ↓
Ajuste dos parâmetros
```

---

## 12.2 Conjunto de validação

Utilizado durante o desenvolvimento do modelo para:

- comparar configurações;
- escolher hiperparâmetros;
- avaliar versões do modelo;
- acompanhar possíveis problemas de overfitting.

---

## 12.3 Conjunto de teste

É reservado para uma avaliação final.

O objetivo é verificar como o modelo se comporta diante de dados que não participaram do treinamento.

Uma regra importante é:

> O conjunto de teste deve permanecer separado durante o desenvolvimento do modelo.

---

# 13. Amostragem

**Amostragem** é o processo de selecionar uma parte de uma população para realizar uma análise.

Exemplo:

```text
População = 100.000 clientes

Amostra = 5.000 clientes
```

Em vez de analisar necessariamente todos os 100.000 clientes, podemos selecionar uma amostra representativa.

Existem diferentes técnicas.

---

# 14. Amostragem aleatória simples

Na **amostragem aleatória simples**, os elementos são selecionados aleatoriamente.

Exemplo:

```text
2, 53, 79, 14, 91...
```

Não existe uma sequência ou intervalo específico para escolher os elementos.

A ideia é que cada elemento tenha uma chance conhecida de ser selecionado.

### Exemplo

População:

```text
1, 2, 3, 4, 5, ..., 100
```

Amostra:

```text
7, 23, 45, 67, 89
```

---

# 15. Amostragem sistemática

Na **amostragem sistemática**, os elementos são selecionados seguindo um intervalo.

Exemplo:

```text
1, 11, 21, 31, 41, 51...
```

Nesse caso:

```text
Intervalo = 10
```

Começando no elemento 1 e avançando de 10 em 10:

```text
1
↓ +10
11
↓ +10
21
↓ +10
31
```

### Exemplo prático

Imagine uma lista com 10.000 clientes e queremos selecionar 1.000.

Podemos calcular:

```text
10.000 / 1.000 = 10
```

Então o intervalo é aproximadamente 10.

A partir de um ponto inicial aleatório, podemos selecionar:

```text
8, 18, 28, 38, 48...
```

---

# 16. Amostragem estratificada

Na **amostragem estratificada**, a população é dividida em grupos chamados **estratos**.

Depois, realizamos uma amostragem dentro de cada grupo.

O objetivo é garantir que grupos importantes da população estejam representados na amostra.

### Exemplo

Imagine uma população de clientes:

```text
100.000 clientes
│
├── 60.000 baixa renda
├── 30.000 média renda
└── 10.000 alta renda
```

Se quisermos uma amostra de 1.000 clientes mantendo a mesma proporção:

```text
600 → baixa renda
300 → média renda
100 → alta renda
```

Isso é uma **amostragem estratificada proporcional**.

---

## 16.1 Por que utilizar amostragem estratificada?

Imagine que exista um grupo que representa apenas 5% da população.

Em uma amostragem aleatória simples, esse grupo pode acabar ficando sub-representado por acaso.

A amostragem estratificada permite garantir que esse grupo seja considerado.

Ela é especialmente útil quando os grupos possuem características diferentes e relevantes para a análise.

---

## 16.2 Amostragem estratificada não proporcional

Nem sempre precisamos manter exatamente a proporção da população.

Podemos selecionar mais elementos de determinado grupo.

Exemplo:

```text
População:

90% → Grupo A
10% → Grupo B
```

Podemos criar uma amostra:

```text
50% → Grupo A
50% → Grupo B
```

Isso pode ser útil quando queremos estudar com mais profundidade um grupo pequeno.

Depois, dependendo do objetivo da análise, pode ser necessário considerar os pesos/proporções originais.

---

# 17. Comparação dos métodos de amostragem

| Método | Como funciona | Exemplo |
|---|---|---|
| Aleatória simples | Seleção aleatória | 2, 53, 79, 14... |
| Sistemática | Seleção seguindo intervalo | 1, 11, 21, 31... |
| Estratificada | Divide em grupos e seleciona dentro deles | 60% A, 30% B, 10% C |

---

# 18. Random Forest

O **Random Forest** é um algoritmo de Machine Learning baseado em várias **árvores de decisão**.

Em vez de depender de uma única árvore, ele cria várias árvores e combina seus resultados.

```text
                 Dataset
                    │
          ┌─────────┼─────────┐
          ↓         ↓         ↓
       Árvore 1  Árvore 2  Árvore 3
          │         │         │
          ↓         ↓         ↓
          A         B         A
          └─────────┼─────────┘
                    ↓
                  Votação
                    ↓
             Resultado final
```

Em um problema de classificação, cada árvore pode votar em uma classe.

A classe mais votada pode ser escolhida como resultado final.

---

# 19. Por que Random Forest utiliza aleatoriedade?

O nome **Random Forest** está relacionado à utilização de aleatoriedade na construção das árvores.

De forma simplificada:

- diferentes amostras dos dados podem ser utilizadas pelas árvores;
- diferentes subconjuntos de características podem ser considerados nas divisões;
- as árvores acabam aprendendo padrões diferentes.

A combinação das árvores tende a produzir um modelo mais robusto do que depender de uma única árvore.

---

# 20. Random Forest no problema de inadimplência

Podemos utilizar o mesmo conjunto:

```text
X:
- idade
- renda
- score

y:
- inadimplencia
```

O Random Forest recebe:

```text
X → características
y → resultado conhecido
```

e aprende padrões relacionados à inadimplência.

Depois, podemos fornecer um novo cliente:

```text
idade = 35
renda = 3000
score = 580
```

e o modelo pode retornar:

```text
Não inadimplente
```

ou:

```text
Inadimplente
```

Dependendo da implementação, também podemos obter uma probabilidade para cada classe.

---

# 21. Hiperparâmetros do Random Forest

Alguns hiperparâmetros importantes são:

### `n_estimators`

Quantidade de árvores.

Exemplo:

```python
RandomForestClassifier(n_estimators=100)
```

Significa que o modelo utilizará 100 árvores.

### `max_depth`

Define a profundidade máxima das árvores.

### `min_samples_split`

Define a quantidade mínima de amostras necessária para dividir um nó.

### `min_samples_leaf`

Define a quantidade mínima de amostras que deve existir em uma folha.

### `max_features`

Define quantas características podem ser consideradas em determinadas divisões.

Esses parâmetros podem ser ajustados para tentar obter melhor desempenho e controlar overfitting.

---

# 22. Rede Neural x Random Forest

Os dois podem ser utilizados para classificação, mas possuem estruturas diferentes.

| Característica | Rede Neural | Random Forest |
|---|---|---|
| Estrutura | Neurônios em camadas | Várias árvores |
| Aprendizado | Ajuste de pesos | Construção de árvores |
| Dados tabulares | Pode funcionar bem | Frequentemente muito forte |
| Imagens | Muito utilizada | Não é a escolha tradicional |
| Complexidade | Pode ser alta | Geralmente mais simples |
| Hiperparâmetros | Muitos | Vários |
| Interpretabilidade | Geralmente menor | Pode ser mais fácil de analisar |

Não existe um modelo que seja sempre melhor. O desempenho depende do problema e dos dados.

---

# 23. ROC — Receiver Operating Characteristic

A **curva ROC** é utilizada para avaliar modelos de classificação binária em diferentes limiares de decisão.

Ela relaciona:

```text
Eixo Y → Taxa de Verdadeiros Positivos (TPR)
Eixo X → Taxa de Falsos Positivos (FPR)
```

As fórmulas são:

```text
TPR = TP / (TP + FN)

FPR = FP / (FP + TN)
```

Onde:

- `TP` = verdadeiro positivo;
- `TN` = verdadeiro negativo;
- `FP` = falso positivo;
- `FN` = falso negativo.

---

# 24. Como funciona a curva ROC?

Imagine que o modelo produza probabilidades:

```text
Cliente A → 0,90
Cliente B → 0,75
Cliente C → 0,60
Cliente D → 0,30
Cliente E → 0,10
```

Podemos definir diferentes limiares.

Por exemplo:

```text
Limiar = 0,50
```

Tudo acima de 0,50 pode ser classificado como positivo.

Se mudarmos para:

```text
Limiar = 0,70
```

a classificação muda.

A curva ROC mostra como o desempenho muda conforme alteramos o limiar.

Por isso, a curva não precisa ser uma linha "bonita" ou perfeitamente suave. Ela é formada a partir dos resultados obtidos em diferentes pontos de corte.

---

# 25. AUC

**AUC** significa **Area Under the Curve**, ou área sob a curva.

Quando estamos falando de ROC:

```text
ROC-AUC = área sob a curva ROC
```

A AUC resume, em um único valor, a capacidade do modelo de separar as classes.

Uma interpretação simplificada:

```text
AUC = 0,50
→ desempenho semelhante ao aleatório

AUC > 0,50
→ existe capacidade de discriminação

AUC próxima de 1,00
→ excelente separação das classes
```

Por exemplo:

```text
Modelo A → AUC = 0,91
Modelo B → AUC = 0,76
```

Nesse aspecto específico, o Modelo A apresenta melhor capacidade de discriminação.

---

# 26. Uma correção importante sobre AUC

A anotação original dizia:

> "curva auc nunca é bonitinha, sempre com subidas e descidas (melhorou: sobe, piorou: desce)"

O conceito precisa ser ajustado.

**AUC não é a curva.**

Temos:

```text
Curva ROC → gráfico
AUC       → área calculada sob o gráfico
```

A curva ROC pode apresentar pontos de subida e mudanças na trajetória porque é construída a partir de diferentes limiares.

Já a AUC é um **valor numérico**.

Portanto:

```text
ROC → curva
AUC → número que resume a área da curva
```

---

# 27. Outras métricas de classificação

A AUC não deve ser analisada isoladamente.

Algumas métricas importantes são:

### Accuracy

Proporção geral de previsões corretas.

```text
Accuracy = (TP + TN) / (TP + TN + FP + FN)
```

### Precision

Entre os casos classificados como positivos, quantos realmente são positivos?

```text
Precision = TP / (TP + FP)
```

### Recall

Entre os positivos reais, quantos o modelo conseguiu encontrar?

```text
Recall = TP / (TP + FN)
```

### F1-score

Combina Precision e Recall em uma única métrica.

```text
F1 = 2 × (Precision × Recall) / (Precision + Recall)
```

A métrica mais importante depende do problema.

No caso de inadimplência, por exemplo, pode ser importante analisar cuidadosamente falsos positivos e falsos negativos antes de decidir qual métrica priorizar.

---

# 28. Exemplo completo: previsão de inadimplência

Imagine o seguinte dataset:

| idade | renda | score | inadimplencia |
|---:|---:|---:|---:|
| 25 | 3000 | 650 | 0 |
| 42 | 5000 | 720 | 0 |
| 31 | 2200 | 500 | 1 |
| 55 | 2800 | 450 | 1 |
| 38 | 4000 | 680 | 0 |

Primeiro:

```text
X = idade, renda, score
y = inadimplencia
```

Depois dividimos os dados:

```text
Dataset
   │
   ├── Treinamento
   ├── Validação
   └── Teste
```

Podemos então treinar dois modelos:

```text
                 X + y
                   │
          ┌────────┴────────┐
          ↓                 ↓
     Rede Neural       Random Forest
          │                 │
          ↓                 ↓
      Previsões          Previsões
          │                 │
          └────────┬────────┘
                   ↓
              Avaliação
                   │
        ┌──────────┼──────────┐
        ↓          ↓          ↓
       AUC      Precision    Recall
```

Depois comparamos os resultados.

---

# 29. Fluxo completo do aprendizado de máquina

O conteúdo da aula pode ser organizado neste fluxo:

```text
                  DATASET
                     │
                     ↓
              Entendimento
               dos dados
                     │
                     ↓
               Preparação
                dos dados
                     │
                     ↓
              ┌──────┴──────┐
              ↓             ↓
              X             y
        características     alvo
              │             │
              └──────┬──────┘
                     ↓
             Divisão dos dados
                     │
          ┌──────────┼──────────┐
          ↓          ↓          ↓
       Treino     Validação    Teste
          │
          ↓
       Treinamento
          │
     ┌────┴──────────┐
     ↓               ↓
Rede Neural      Random Forest
     │               │
     └──────┬────────┘
            ↓
        Previsões
            │
            ↓
         Métricas
            │
    ┌───────┼────────┐
    ↓       ↓        ↓
   AUC    Recall   Precision
            │
            ↓
       Comparação
            │
            ↓
       Modelo final
```

---

# 30. O que é mais importante memorizar

## Rede neural

```text
Entrada → Camadas ocultas → Saída
```

A rede aprende ajustando seus pesos durante o treinamento.

## X e y

```text
X = características usadas para prever
y = variável que queremos prever
```

## Epoch

```text
1 epoch = uma passagem completa pelo dataset de treinamento
```

## Batch

```text
Batch = parte do dataset processada de uma vez
```

## Random Forest

```text
Random Forest = conjunto de várias árvores de decisão
```

## Amostragem

```text
Aleatória simples → seleção aleatória
Sistemática        → seleção por intervalo
Estratificada      → seleção considerando grupos
```

## ROC e AUC

```text
ROC = curva de desempenho em diferentes limiares
AUC = área sob a curva ROC
```

## Treino, validação e teste

```text
Treino     → aprender
Validação  → ajustar/escolher
Teste      → avaliação final
```

---

# 31. Observação sobre a imagem da aula

As anotações originais fazem referência ao arquivo:

```text
divisao_do_dataset.png
```

A imagem não foi disponibilizada junto com as anotações. Por isso, não é possível reproduzir exatamente o desenho ou os percentuais apresentados pelo professor.

O conceito foi completado neste documento utilizando a divisão padrão em:

```text
Treinamento
Validação
Teste
```

com exemplos de proporções como `70% / 15% / 15%`.

A proporção exata deve ser entendida como uma **escolha de projeto**, e não como uma regra universal.

---

# 32. Conclusão

Os conceitos da aula estão relacionados principalmente ao processo de construção e avaliação de modelos de Machine Learning.

O fluxo fundamental é:

```text
Dados
 ↓
Separação entre X e y
 ↓
Divisão em treino/validação/teste
 ↓
Treinamento
 ↓
Modelo
 ↓
Previsões
 ↓
Métricas
 ↓
Avaliação
```

Dentro desse processo, a **rede neural** aprende por meio do ajuste de pesos, enquanto o **Random Forest** combina diversas árvores de decisão.

A quantidade de vezes que os dados são apresentados durante o treinamento é controlada pelas **epochs**, enquanto a avaliação de classificadores pode utilizar métricas como **Accuracy, Precision, Recall, F1-score e ROC-AUC**.

Já as técnicas de **amostragem** determinam como uma parcela de uma população pode ser selecionada, sendo as principais estudadas nesta aula a amostragem aleatória simples, sistemática e estratificada.
