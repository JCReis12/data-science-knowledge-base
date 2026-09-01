# Anotações de Ciência de Dados — Aula 05

## Inferência Estatística, Distribuições e Testes de Hipóteses

> **Objetivo da aula:** aprender a utilizar uma amostra de dados para tirar conclusões sobre uma população, avaliar hipóteses estatísticas, verificar a normalidade de variáveis e analisar associações entre variáveis categóricas.

---

## 1. Inferência Estatística

### O que é?

**Inferência Estatística** é o conjunto de métodos que permite tirar conclusões sobre uma **população** a partir de uma **amostra**, levando em consideração a incerteza existente nos dados.

Na prática, normalmente não conseguimos analisar toda a população. Por isso, coletamos uma amostra que deve representar, da melhor maneira possível, o comportamento da população.

### 🍲 Metáfora da sopa

Imagine que você preparou uma panela de sopa e quer descobrir se ela está com a quantidade correta de sal.

Não é necessário beber a panela inteira para descobrir isso. Você pode:

1. Mexer a sopa para que os ingredientes fiquem distribuídos;
2. Retirar uma pequena porção;
3. Provar essa porção;
4. Usar o resultado para inferir se a panela inteira está adequadamente temperada.

Nesse exemplo:

- **Panela inteira** → população;
- **Pequena porção retirada** → amostra;
- **Sabor da porção** → informação obtida da amostra;
- **Conclusão sobre a panela** → inferência estatística.

### Exemplo em Ciência de Dados

Em uma análise de crédito, podemos ter milhões de clientes na população, mas analisar apenas uma amostra de clientes.

A partir dessa amostra, podemos investigar se determinados fatores estão associados à inadimplência ou se uma variável apresenta determinado comportamento estatístico.

### Fluxo geral

```text
POPULAÇÃO
    ↓
Amostragem
    ↓
AMOSTRA
    ↓
Estatística descritiva + Testes estatísticos
    ↓
Inferência sobre a população
    ↓
Tomada de decisão
```

> **Atenção:** uma amostra precisa ser adequada e representativa. Uma amostra ruim pode levar a conclusões ruins sobre a população.

---

# 2. Testes de Hipóteses

Um **Teste de Hipóteses** é utilizado para avaliar, com base nos dados, se existe evidência suficiente para questionar uma determinada afirmação sobre a população.

Trabalhamos principalmente com duas hipóteses:

## 2.1 Hipótese Nula — H₀

A **Hipótese Nula (H₀)** normalmente representa:

- ausência de efeito;
- ausência de diferença;
- ausência de associação;
- ou o comportamento considerado como referência.

Ela é a hipótese que tentamos encontrar evidências suficientes para rejeitar.

### Exemplos

**Teste de normalidade:**

> H₀: a variável segue uma distribuição Normal.

**Teste Qui-Quadrado de Independência:**

> H₀: as variáveis são independentes, ou seja, não existe associação estatisticamente significativa entre elas.

---

## 2.2 Hipótese Alternativa — H₁

A **Hipótese Alternativa (H₁ ou Hₐ)** representa o resultado contrário à hipótese nula.

### Exemplos

**Teste de normalidade:**

> H₁: a variável não segue uma distribuição Normal.

**Teste Qui-Quadrado de Independência:**

> H₁: as variáveis não são independentes; existe associação estatisticamente significativa entre elas.

---

# 3. Nível de Significância — α

Antes de realizar um teste, definimos um **nível de significância (α)**.

Um valor comum é:

```text
α = 0,05
```

Isso corresponde a um nível de confiança de:

```text
1 - α = 0,95 = 95%
```

O α funciona como um **limiar para a decisão estatística**.

---

# 4. p-valor

O **p-valor** indica quão compatível o resultado observado é com a hipótese nula.

De forma mais precisa:

> O p-valor é a probabilidade de obter um resultado tão ou mais extremo quanto o observado, **assumindo que H₀ seja verdadeira**.

### Regra de decisão

| p-valor | Decisão |
|---|---|
| **p ≤ 0,05** | Rejeita-se H₀ |
| **p > 0,05** | Não se rejeita H₀ |

### Como interpretar?

#### p ≤ 0,05

Existe evidência estatística suficiente, considerando α = 0,05, para **rejeitar H₀**.

#### p > 0,05

Não existe evidência estatística suficiente para rejeitar H₀.

> ⚠️ É melhor dizer **"não rejeitamos H₀"** do que simplesmente dizer **"H₀ é verdadeira"**. Um p-valor alto não prova que H₀ seja verdadeira; apenas indica que os dados não forneceram evidência suficiente contra ela.

### ❌ Cuidado com uma interpretação comum

O p-valor **não** significa:

> "A chance de a hipótese nula ser verdadeira é de 1%."

Ele representa a probabilidade de observarmos um resultado tão extremo quanto o encontrado **sob a suposição de que H₀ é verdadeira**.

---

# 5. Fluxo de um Teste de Hipóteses

```text
1. Formular H₀ e H₁
          ↓
2. Definir α
          ↓
3. Coletar/analisar os dados
          ↓
4. Calcular a estatística do teste
          ↓
5. Obter o p-valor
          ↓
6. Comparar p com α
          ↓
   ┌───────────────┐
   │ p ≤ α         │ → Rejeita H₀
   │ p > α         │ → Não rejeita H₀
   └───────────────┘
          ↓
7. Interpretar o resultado no contexto do problema
```

---

# 6. Matriz de Decisão e Erros Estatísticos

Ao tomar uma decisão estatística, podemos cometer erros.

| Realidade | Não rejeitar H₀ | Rejeitar H₀ |
|---|---|---|
| **H₀ verdadeira** | ✅ Decisão correta | ❌ **Erro Tipo I (α)** |
| **H₀ falsa** | ❌ **Erro Tipo II (β)** | ✅ Decisão correta |

## 6.1 Erro Tipo I — α

Ocorre quando:

> **Rejeitamos H₀ mesmo quando H₀ é verdadeira.**

É conhecido como **falso positivo**.

Com α = 0,05, o teste aceita uma taxa de 5% de risco de cometer esse tipo de erro, sob as condições do teste.

### Exemplo

Imagine que um teste indique que existe associação entre duas variáveis, quando na realidade não existe.

---

## 6.2 Erro Tipo II — β

Ocorre quando:

> **Não rejeitamos H₀ mesmo quando H₀ é falsa.**

É conhecido como **falso negativo**.

### Exemplo

Existe uma associação real entre duas variáveis, mas o teste não consegue detectá-la.

---

## 6.3 Poder do teste

O **poder estatístico** é:

```text
Poder = 1 - β
```

Representa a capacidade do teste de detectar um efeito ou diferença quando ele realmente existe.

---

# 7. Testes de Normalidade

A aula apresenta testes utilizados para verificar se uma variável numérica apresenta comportamento compatível com uma **Distribuição Normal (Gaussiana)**.

Essa avaliação é importante porque alguns métodos estatísticos, especialmente testes paramétricos e determinados modelos, trabalham com pressupostos relacionados à distribuição dos dados.

Na aula, são utilizados três testes:

1. **Shapiro-Wilk**
2. **Kolmogorov-Smirnov**
3. **Anderson-Darling**

Além dos testes estatísticos, a aula utiliza gráficos para complementar o diagnóstico.

---

# 8. Hipóteses dos Testes de Normalidade

Para os testes apresentados:

### H₀

> A variável segue uma Distribuição Normal.

### H₁

> A variável não segue uma Distribuição Normal.

Com α = 0,05:

```text
p > 0,05
→ Não rejeitamos H₀
→ Não há evidência suficiente contra a normalidade

p ≤ 0,05
→ Rejeitamos H₀
→ Há evidência de que a variável não é Normal
```

> **Importante:** "não rejeitar H₀" não significa provar que os dados são perfeitamente normais. O resultado deve ser analisado junto com gráficos e com o contexto da aplicação.

---

# 9. Principais Testes de Normalidade

## 9.1 Shapiro-Wilk

O **Shapiro-Wilk** testa se os dados são compatíveis com uma distribuição Normal.

Na aula, ele é aplicado sobre uma subamostra de até **2.000 observações**, utilizando `scipy.stats.shapiro`.

```python
stats.shapiro(amostra)
```

Retorna, entre outros valores:

- estatística **W**;
- **p-valor**.

### Interpretação

```text
p ≤ 0,05 → rejeita H₀ → evidência de não normalidade
p > 0,05 → não rejeita H₀ → dados compatíveis com normalidade
```

---

## 9.2 Kolmogorov-Smirnov — KS

O teste **Kolmogorov-Smirnov** compara a distribuição empírica dos dados com uma distribuição teórica.

Na implementação da aula, os dados são padronizados e comparados com a distribuição Normal:

```python
z_scores = (amostra - amostra.mean()) / amostra.std()
stats.kstest(z_scores, 'norm')
```

A estatística do teste é representada por **D**, relacionada à maior distância entre as distribuições acumuladas.

---

## 9.3 Anderson-Darling

O **Anderson-Darling** também verifica a aderência dos dados a uma distribuição teórica.

Na aula:

```python
stats.anderson(amostra, dist='norm')
```

Um ponto importante é que o teste dá maior atenção às **caudas da distribuição**, tornando-se útil para avaliar desvios que podem ocorrer nos valores extremos.

Diferentemente do Shapiro-Wilk e do KS, a implementação utilizada na aula trabalha com **valores críticos**, e não diretamente com um p-valor.

Para α = 0,05:

```text
Estatística AD > Valor crítico de 5%
→ Rejeita H₀

Estatística AD ≤ Valor crítico de 5%
→ Não rejeita H₀
```

---

# 10. Comparação dos Testes de Normalidade

| Teste | O que avalia | Resultado principal |
|---|---|---|
| **Shapiro-Wilk** | Compatibilidade com Normal | W + p-valor |
| **Kolmogorov-Smirnov** | Distância entre distribuição empírica e teórica | D + p-valor |
| **Anderson-Darling** | Aderência à distribuição, com maior atenção às caudas | Estatística + valor crítico |

---

# 11. Diagnóstico Visual da Normalidade

Não devemos depender exclusivamente de um teste estatístico. A aula combina os testes com três visualizações.

## 11.1 Histograma + KDE + Curva Normal

Permite observar:

- formato da distribuição;
- assimetria;
- concentração dos dados;
- possíveis caudas;
- comparação com a curva Normal teórica.

---

## 11.2 Gráfico Q-Q

O **Q-Q Plot (Quantile-Quantile Plot)** compara os quantis observados com os quantis esperados de uma distribuição Normal.

### Interpretação intuitiva

Se os pontos estiverem aproximadamente sobre a linha de referência:

```text
Dados observados
      ↗
    ↗
  ↗
↗____________
  Quantis teóricos
```

há maior compatibilidade visual com a normalidade.

Desvios sistemáticos da linha podem indicar:

- assimetria;
- caudas diferentes;
- outliers;
- ou outras diferenças em relação à distribuição Normal.

---

## 11.3 ECDF vs. CDF Teórica

### ECDF

**ECDF (Empirical Cumulative Distribution Function)** é a função de distribuição acumulada empírica dos dados.

Ela mostra, para cada valor, a proporção de observações menores ou iguais àquele valor.

### Comparação

A aula compara:

```text
ECDF dos dados
       VS.
CDF da Normal teórica
```

Quanto mais próximas as curvas, maior a compatibilidade visual com a distribuição teórica.

---

# 12. Exemplo da aula: Dados de Crédito

A aula utiliza uma base de risco de crédito e avalia, entre outras variáveis:

- `score_serasa`
- `renda_mensal`

O diagnóstico foi estruturado para avaliar:

### Score Serasa

A variável é tratada no exercício como exemplo de variável com comportamento **Normal**.

### Renda Mensal

É utilizada como exemplo de variável com **assimetria / não normalidade**.

> A conclusão deve ser baseada nos resultados efetivamente obtidos pelos testes e gráficos, e não apenas no nome da variável.

---

# 13. Teste Qui-Quadrado (χ²)

O **Teste Qui-Quadrado** é utilizado na aula para analisar **variáveis categóricas**.

Uma aplicação importante é verificar se existe associação entre duas variáveis categóricas.

### Exemplo

Queremos saber:

> Existe associação entre o **tipo de vínculo empregatício** e a **inadimplência**?

As variáveis poderiam ser:

```text
tipo_vinculo → categórica
inadimplente → categórica/binária
```

---

# 14. Teste Qui-Quadrado de Independência

O **Teste Qui-Quadrado de Independência** verifica se duas variáveis categóricas são independentes ou se existe uma associação estatisticamente significativa entre elas.

Na implementação Python:

```python
stats.chi2_contingency(tabela)
```

---

## 14.1 Hipóteses

### H₀

> As variáveis são **independentes**. Não existe associação estatisticamente significativa.

### H₁

> As variáveis são **dependentes**, ou seja, existe associação estatisticamente significativa.

### Regra de decisão

```text
p > 0,05
→ Não rejeita H₀
→ Não há evidência estatística de associação

p ≤ 0,05
→ Rejeita H₀
→ Há evidência estatística de associação
```

---

# 15. Tabela de Contingência

Para aplicar o teste, construímos uma **tabela de contingência**.

Ela organiza as frequências observadas para as combinações entre duas variáveis categóricas.

Exemplo:

| Tipo de vínculo | Adimplente | Inadimplente |
|---|---:|---:|
| CLT | Observado | Observado |
| Autônomo | Observado | Observado |
| Empresário | Observado | Observado |

Essas frequências são chamadas de **frequências observadas (O)**.

---

# 16. Frequências Esperadas

O teste compara:

- **frequências observadas (O)**;
- **frequências esperadas (E)**.

As frequências esperadas representam o que seria observado caso as variáveis fossem independentes.

A fórmula utilizada é:

```text
Eᵢⱼ = (Total da linha i × Total da coluna j)
       / Total geral
```

---

# 17. Estatística Qui-Quadrado

A estatística do teste é calculada por:

```text
        (Oᵢⱼ - Eᵢⱼ)²
χ² = Σ ───────────────
             Eᵢⱼ
```

Onde:

- **Oᵢⱼ** = frequência observada;
- **Eᵢⱼ** = frequência esperada.

### Intuição

Se os valores observados forem muito diferentes dos valores esperados sob independência, a estatística χ² tende a ser maior.

Consequentemente, podemos obter um p-valor pequeno e rejeitar H₀.

---

# 18. Graus de Liberdade

No teste Qui-Quadrado de Independência, os **graus de liberdade (DoF)** são calculados por:

```text
DoF = (número de linhas - 1)
    × (número de colunas - 1)
```

Eles fazem parte do cálculo da distribuição de referência utilizada pelo teste.

---

# 19. Interpretação do Qui-Quadrado

### Caso 1 — p > 0,05

```text
Não rejeita H₀
       ↓
Não há evidência estatística suficiente
de associação entre as variáveis.
```

### Caso 2 — p ≤ 0,05

```text
Rejeita H₀
       ↓
Existe evidência estatística de associação
entre as variáveis.
```

> ⚠️ **Associação não significa causalidade.** Se o teste mostrar associação entre duas variáveis, isso não prova que uma variável cause a outra.

---

# 20. Exemplo da aula: Vínculo vs. Inadimplência

A aula utiliza:

```text
tipo_vinculo
        ×
inadimplente
```

O processo é:

1. Padronizar a variável de vínculo;
2. Criar a tabela de contingência;
3. Calcular o teste Qui-Quadrado;
4. Obter:
   - χ²;
   - graus de liberdade;
   - p-valor;
5. Comparar o p-valor com α = 0,05;
6. Interpretar o resultado no contexto do risco de crédito.

Além disso, a aula calcula a **taxa de inadimplência por tipo de vínculo** para complementar a interpretação.

---

# 21. Teste Qui-Quadrado de Aderência

Outro teste apresentado é o **Qui-Quadrado de Aderência (Goodness-of-Fit)**.

Enquanto o teste de independência analisa a relação entre **duas variáveis categóricas**, o teste de aderência avalia se a distribuição observada de **uma variável categórica** é compatível com uma distribuição teórica esperada.

Na implementação:

```python
stats.chisquare(
    f_obs=freq_observada.values,
    f_exp=freq_esperada_uniforme
)
```

### Exemplo da aula

Avaliar se os proponentes estão distribuídos **uniformemente entre os estados civis**.

---

# 22. Diferença entre os testes Qui-Quadrado

| Teste | Pergunta |
|---|---|
| **Qui-Quadrado de Independência** | Duas variáveis categóricas possuem associação? |
| **Qui-Quadrado de Aderência** | Uma variável categórica segue uma distribuição/proporção esperada? |

### Exemplos

**Independência:**

```text
Tipo de contrato × Cancelamento
```

**Aderência:**

```text
Estado civil × Distribuição uniforme esperada
```

---

# 23. Aplicação em Telecom — Churn

A aula propõe aplicar os conceitos em uma base de **Telecom Churn**, com **7.500 clientes**.

O objetivo é transformar os conceitos estatísticos em problemas reais de negócio.

---

## Exercício 1 — Diagnóstico de Normalidade

Variáveis analisadas:

- `mensalidade_reais` → valor cobrado mensalmente;
- `uso_dados_gb` → volume de internet utilizado.

Para cada variável:

1. Aplicar os testes de normalidade;
2. Observar Shapiro-Wilk;
3. Analisar o Q-Q Plot;
4. Analisar ECDF vs. CDF teórica;
5. Concluir se há evidência de normalidade.

### Pergunta central

> A distribuição observada é compatível com uma distribuição Normal?

---

# 24. Exercício 2 — Tipo de Contrato vs. Churn

Variáveis:

```text
tipo_contrato
        ×
cancelou_plano
```

Categorias de contrato:

- Mensal;
- Anual;
- Bienal.

### Procedimento

1. Criar a tabela de contingência;
2. Aplicar `chi2_contingency()`;
3. Obter:
   - χ²;
   - graus de liberdade;
   - p-valor;
4. Comparar p com 0,05;
5. Interpretar a associação no contexto do negócio.

### Pergunta de negócio

> Existe evidência estatística de que o tipo de contrato esteja associado ao cancelamento?

---

# 25. Exercício 3 — Erros Tipo I e Tipo II no Churn

Imagine que a empresa ofereça **2 meses grátis** para clientes identificados como estando em risco de cancelamento.

### Erro Tipo I

O sistema identifica um cliente como risco de churn, mas ele **não cancelaria**.

A empresa oferece o benefício desnecessariamente.

### Possível consequência

- custo do benefício;
- redução de receita;
- concessão de desconto para um cliente que permaneceria mesmo sem incentivo.

---

### Erro Tipo II

O sistema não identifica um cliente como risco, mas ele **realmente cancela**.

A empresa deixa de oferecer a retenção.

### Possível consequência

- perda do cliente;
- perda de receita futura;
- necessidade de adquirir outro cliente;
- possível impacto relacionado ao CAC.

---

# 26. Exercício 4 — Forma de Pagamento vs. Churn

Variáveis:

```text
forma_pagamento
        ×
cancelou_plano
```

Formas de pagamento:

- Cartão de Crédito;
- Boleto;
- Pix;
- Débito Automático.

### O exercício pede:

1. Aplicar o teste Qui-Quadrado de Independência;
2. Calcular a taxa de cancelamento por forma de pagamento;
3. Criar um gráfico de barras;
4. Identificar a categoria com maior taxa de churn;
5. Verificar se a associação possui significância estatística com α = 0,05.

### Atenção

Uma categoria apresentar a **maior taxa de churn** não significa, sozinha, que a diferença seja estatisticamente significativa.

É necessário analisar o resultado do teste.

---

# 27. Significância Estatística vs. Importância Prática

Esse é um ponto importante para Ciência de Dados.

### Significância estatística

Pergunta:

> Existe evidência suficiente de que o padrão observado não seja explicado apenas pela variação amostral?

É avaliada, no contexto da aula, principalmente pelo **p-valor**.

### Importância prática

Pergunta:

> Mesmo que exista associação estatística, ela é grande o suficiente para fazer diferença no negócio?

Uma associação pode ser estatisticamente significativa e ainda ter impacto prático pequeno.

Por isso, a análise estatística deve ser combinada com métricas de negócio.

---

# 28. Checklist para Resolver um Teste Estatístico

Antes de executar um teste, pergunte:

### 1. Qual é o tipo dos dados?

```text
Numérico contínuo?
       ↓
Pode haver teste de normalidade.

Categórico?
       ↓
Pode haver teste Qui-Quadrado.
```

### 2. Qual pergunta quero responder?

Exemplo:

> "A variável é Normal?"

ou:

> "Existe associação entre as duas variáveis?"

### 3. Quais são H₀ e H₁?

Sempre escreva claramente antes do teste.

### 4. Qual é o α?

Na aula:

```text
α = 0,05
```

### 5. Qual é o resultado?

Observe:

- estatística do teste;
- p-valor;
- graus de liberdade, quando aplicável;
- valores críticos, no Anderson-Darling.

### 6. Qual é a decisão?

```text
p ≤ α → rejeitar H₀
p > α → não rejeitar H₀
```

### 7. O que isso significa no negócio?

Nunca termine apenas com:

> "p = 0,03."

Explique o que esse resultado representa no problema analisado.

---

# 29. Resumo dos principais conceitos

| Conceito | Ideia principal |
|---|---|
| **População** | Conjunto total que queremos estudar |
| **Amostra** | Parte da população utilizada na análise |
| **Inferência Estatística** | Usar a amostra para tirar conclusões sobre a população |
| **H₀** | Hipótese de referência/nula |
| **H₁** | Hipótese alternativa |
| **α** | Nível de significância definido antes do teste |
| **p-valor** | Evidência contra H₀ sob a suposição de que H₀ é verdadeira |
| **Erro Tipo I** | Rejeitar H₀ quando H₀ é verdadeira |
| **Erro Tipo II** | Não rejeitar H₀ quando H₀ é falsa |
| **Poder** | Capacidade de detectar um efeito real |
| **Normalidade** | Compatibilidade dos dados com uma distribuição Normal |
| **Shapiro-Wilk** | Teste de normalidade |
| **Kolmogorov-Smirnov** | Compara distribuição empírica e teórica |
| **Anderson-Darling** | Teste de aderência com atenção às caudas |
| **Qui-Quadrado de Independência** | Testa associação entre duas variáveis categóricas |
| **Qui-Quadrado de Aderência** | Testa aderência de uma distribuição observada a uma esperada |
| **Tabela de contingência** | Organiza frequências de duas variáveis categóricas |
| **Frequência observada** | Quantidade realmente encontrada |
| **Frequência esperada** | Quantidade esperada sob H₀ |
| **Associação** | Relação estatística entre variáveis; não implica causalidade |

---

# 30. 🧠 Resumo para prova

### Inferência Estatística

> **Amostra → análise → conclusão sobre a população.**

### Hipóteses

```text
H₀ = hipótese nula
H₁ = hipótese alternativa
```

### Regra principal

```text
p ≤ 0,05 → rejeita H₀
p > 0,05 → não rejeita H₀
```

### Teste de Normalidade

```text
H₀: dados são compatíveis com Normal
H₁: dados não são compatíveis com Normal
```

### Qui-Quadrado de Independência

```text
H₀: variáveis são independentes
H₁: existe associação entre as variáveis
```

### Qui-Quadrado de Aderência

```text
Compara a distribuição observada
com uma distribuição esperada.
```

### Erros

```text
Tipo I  → falso positivo → rejeitar H₀ sendo H₀ verdadeira
Tipo II → falso negativo → não rejeitar H₀ sendo H₀ falsa
```

### Poder

```text
Poder = 1 - β
```

### Regra de ouro

> **Resultado estatístico ≠ conclusão de negócio automática.**

O teste indica evidência estatística. A interpretação final deve considerar também o contexto, o tamanho do efeito, os dados utilizados e o impacto prático da decisão.
