# IA_PARA_DEVS_FASE1

# Diabetes Prediction using Machine Learning

## Visão Geral do Projeto

Este projeto tem como objetivo desenvolver um modelo de Machine Learning capaz de prever se um paciente possui diabetes com base em dados clínicos.

O sistema foi projetado para apoiar profissionais de saúde na detecção precoce da doença e na melhoria da eficiência do processo de triagem. É importante destacar que esta ferramenta não substitui o diagnóstico médico, atuando apenas como um sistema de apoio à decisão.

---

## Objetivo

O principal objetivo deste projeto é classificar pacientes em duas categorias:

* Com diabetes
* Sem diabetes

O modelo utiliza variáveis como nível de glicose, índice de massa corporal (BMI), idade e outros indicadores médicos para realizar as previsões.

Além disso, diferentes modelos de Machine Learning foram avaliados para identificar a abordagem mais eficaz, com foco na métrica **recall**, devido à sua importância na minimização de falsos negativos em aplicações na área da saúde.

---

## Dataset

O dataset utilizado neste projeto é o **Pima Indians Diabetes Dataset**, que contém as seguintes variáveis:

* Pregnancies
* Glucose
* BloodPressure
* SkinThickness
* Insulin
* BMI
* DiabetesPedigreeFunction
* Age
* Outcome (variável alvo)

Link para o dataset:
https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database

---

## Pré-processamento

As seguintes etapas de pré-processamento foram aplicadas:

* Substituição de valores inválidos (zero) por valores ausentes (NaN)
* Imputação de dados utilizando a mediana
* Padronização das variáveis com StandardScaler
* Utilização de pipeline para garantir consistência e evitar vazamento de dados

---

## Modelos Utilizados

Foram implementados os seguintes modelos de Machine Learning:

* Regressão Logística (modelo base interpretável)
* K-Nearest Neighbors (abordagem baseada em distância)
* Support Vector Machine (eficiente na definição de fronteiras de decisão)
* Random Forest (melhor desempenho geral e capaz de capturar relações não lineares)

---

## Métricas de Avaliação

Os modelos foram avaliados utilizando as seguintes métricas:

* Acurácia
* Recall (métrica principal)
* F1-score
* AUC (Área sob a curva ROC)

O recall foi priorizado, pois em um contexto médico é mais importante identificar corretamente pacientes com diabetes do que evitar falsos positivos.

---

## Resultados

O modelo Random Forest apresentou o melhor desempenho geral:

* Maior acurácia
* Maior AUC
* Recall equivalente ao KNN, porém com melhor equilíbrio geral

Isso indica que o Random Forest é o modelo mais adequado para o problema proposto.

---

## Interpretação do Modelo

### Importância das Variáveis

As variáveis mais relevantes identificadas foram:

* Glucose (mais importante)
* BMI
* Diabetes Pedigree Function
* Age

Esses resultados estão alinhados com o conhecimento médico sobre fatores de risco para diabetes.

### Análise com SHAP

A técnica SHAP (SHapley Additive Explanations) foi utilizada para compreender como cada variável influencia as previsões.

Principais observações:

* Altos níveis de glicose aumentam significativamente o risco de diabetes
* BMI e idade também contribuem positivamente
* Valores mais baixos reduzem a probabilidade da doença

---

## Limitações

* O dataset possui tamanho relativamente reduzido
* Nem todas as variáveis clínicas relevantes estão presentes
* O recall não é perfeito, o que significa que alguns casos podem não ser identificados

---

## Aplicação Prática

Este modelo pode ser utilizado como uma ferramenta de apoio à decisão na área da saúde, auxiliando na triagem inicial de pacientes com maior risco de diabetes.

No entanto:

O modelo não substitui o médico.
A decisão final deve sempre ser tomada por um profissional de saúde.

---

## Como Executar o Projeto

### Preparação do dataset

Faça o download do dataset e coloque o arquivo `diabetes.csv` no mesmo diretório do script Python.

---

### Instalação de dependências

```bash
pip install pandas numpy scikit-learn matplotlib seaborn shap
```

---

### Execução do projeto

```bash


---

## Docker (opcional)

```bash
docker build -t diabetes-ml .
docker run diabetes-ml
```

---

## Autor

Seu Nome Aqui

---

## Considerações Finais

Este projeto demonstra como técnicas de Machine Learning podem ser aplicadas na área da saúde para apoiar a tomada de decisão, mantendo sempre a importância da análise humana no diagnóstico médico.
