# Tech Challenge – Fase 1
## Classificação de Exames com Machine Learning

---

## Objetivo Geral
Classificação de exames com Machine Learning: você deve escolher uma base de dados em forma de tabela e realizar o diagnóstico para saber se a pessoa tem ou não uma doença via algoritmos de aprendizado de máquina.

---

## Tema Escolhido
### Pré-triagem de pacientes do sexo feminino: classificação entre diabéticas e não diabéticas

---

##  Identificação do problema
Em ambientes hospitalares e clínicos, o grande volume de pacientes e exames torna o processo de triagem inicial mais demorado e suscetível a falhas humanas. Diante desse cenário, este projeto propõe o uso de técnicas de Machine Learning para auxiliar na análise inicial de dados clínicos estruturados, identificando padrões que indiquem a presença de diabetes. O principal desafio consiste em desenvolver um modelo eficiente que minimize falsos negativos, ou seja, casos em que pacientes diabéticas não são corretamente identificadas.

---

## Objetivo do Projeto
- Desenvolver um modelo de Machine Learning capaz de classificar pacientes em diabéticas ou não diabéticas, disponibilizando uma solução que atue como ferramenta de apoio à decisão médica, auxiliando na triagem inicial e na identificação precoce da doença.

---

## Dataset Utilizado
- **Link:** https://www.kaggle.com/datasets/mathchi/diabetes-data-set/data  

Dataset composto por dados clínicos de pacientes do sexo feminino, utilizado em problemas de classificação de diabetes.

---

## 🛠️ Etapas do Projeto

### 1️. Exploração e Análise dos Dados (EDA)
Nesta etapa, é realizada a compreensão inicial do dataset por meio de:
- Visualização das primeiras linhas (`.head()`)
- Inspeção da estrutura e tipos de dados (`.info()`)
- Análise estatística descritiva com `df.describe(include="all").T`, contendo:
  - Contagem
  - Média
  - Desvio padrão
  - Quartis
  - Valores mínimos e máximos

#### Análise da Distribuição das Variáveis
Na análise da distribuição das variáveis, foram gerados histogramas acompanhados de curvas de densidade (KDE) para todas as variáveis numéricas do dataset. Essa abordagem permite avaliar a forma das distribuições, identificando se os dados apresentam comportamento simétrico ou assimétrico, além de facilitar a detecção de outliers e de possíveis valores inconsistentes. A visualização também contribui para uma melhor compreensão do comportamento das variáveis clínicas, evidenciando padrões, concentrações e dispersões dos dados. Essa etapa é essencial para orientar decisões de pré-processamento e assegurar maior qualidade na etapa de modelagem.

Estas análises orientam decisões de **pré-processamento**, como normalização, transformação de variáveis e tratamento de valores ausentes.

### Proporção de Diabéticos e Não Diabéticos
Foi criado um gráfico de barras para analisar o balanceamento da variável alvo (*Outcome*), exibindo:
- Quantidade absoluta de pacientes diabéticas e não diabéticas
- Percentual correspondente a cada classe

Essa visualização permite identificar desbalanceamentos que podem impactar o desempenho dos modelos e justificar técnicas adicionais durante a modelagem.

---

### 2. Pré-processamento dos Dados
A análise exploratória identificou valores zerados sem significado clínico nas seguintes variáveis:
- Glicose
- Pressão arterial
- Espessura da pele
- Insulina
- IMC

Esses valores foram tratados substituindo zeros por **NaN**, possibilitando posterior imputação adequada.

#### Mapa de Calor de Correlação
Foi gerado um mapa de calor de correlação (heatmap) baseado no coeficiente de Pearson com o objetivo de analisar a relação linear entre todas as variáveis numéricas do dataset. Essa visualização permite identificar o grau de associação entre os atributos, avaliar possíveis casos de multicolinearidade e compreender como cada variável se relaciona com o desfecho do problema (Outcome). A análise de correlação contribui para a seleção e interpretação das variáveis mais relevantes, apoiando decisões importantes na etapa de modelagem.

As cores indicam:
- Correlação positiva (vermelho)
- Correlação negativa (azul)
- Correlação fraca ou inexistente (valores próximos de zero)

---

### 3. Treinamento e Avaliação dos Modelos
Os dados foram divididos em:
- **80% para treino**
- **20% para teste**
utilizando **amostragem estratificada**, mantendo a proporção das classes.

####  Modelos Avaliados
- Random Forest
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)
- Regressão Logística

Cada modelo foi treinado usando um **pipeline** contendo:
- Imputação de valores ausentes (mediana)
- Padronização dos dados (`StandardScaler`)
- Treinamento do modelo

#### Métricas de Avaliação
Os modelos foram comparados utilizando:
- **Accuracy**
- **Recall** (métrica prioritária)
- **F1-score**
- **AUC-ROC**

Os resultados foram organizados em uma tabela comparativa e ordenados pelo **Recall**, por ser a métrica mais relevante no contexto clínico abordado. O Recall mede a capacidade do modelo em identificar corretamente as pacientes diabéticas, reduzindo a ocorrência de falsos negativos, que representam um risco significativo em cenários de pré-triagem médica.
Em situações de **empate nos valores de Recall**, foi utilizada a métrica **AUC-ROC** como critério secundário de desempate. 
O AUC-ROC avalia a capacidade do modelo em diferenciar entre as classes ao longo de diferentes limiares de decisão, fornecendo uma medida mais abrangente da capacidade discriminativa do classificador.

#### Matrizes de Confusão
Para cada modelo, foi gerada uma matriz de confusão, permitindo a análise de:
- Verdadeiros positivos
- Verdadeiros negativos
- Falsos positivos
- Falsos negativos

---

##  Modelo Selecionado
Após a comparação dos modelos avaliados, o **Random Forest** foi selecionado como o modelo final do projeto. Essa escolha se deu por apresentar o **melhor desempenho em Recall**, métrica prioritária neste contexto de pré-triagem médica, e também um desempenho superior em **AUC-ROC** nos casos em que houve empate nos valores de Recall.







