# 🕵️ Fraud Detection (Kaggle) 

Projeto individual do processo seletivo da Liga Acadêmica de IA do Cin, objetivo de realizar **detecção de fraude**, com **pipeline reprodutível** e **explicabilidade (SHAP)**. O dataset usado está disponível no link da competição no kaggle, e passou por uma transformação por PCA, onde tem features V1-V28 anonimizadas  
Inclui notebooks de **EDA**, **treinamento** e **inferência** (geração do `submission.csv`).

---

## 📌 Objetivo

Construir um modelo para prever a probabilidade de fraude e gerar um arquivo de submissão no formato do Kaggle.

**Métrica (Kaggle):** ROC-AUC (AUROC)

---

## 🗂️ Estrutura do projeto
```
fraud-detection-kaggle/
├── notebooks/
│ ├── eda.ipynb #Análise exploratória dos dados
│ ├── train.ipynb #Pre processamento dos dados e Treinamento do modelo
│ └── inference.ipynb #Geração da submissão no conjunto de testes com o modelo final
├── models/ # artefatos do modelo treinado (.joblib, .json)
├── outputs/ # submission.csv
├── data/ # (NÃO versionado) train.csv e test.csv
├── requirements.txt #Requirements para rodar no windows/mac
├── requirements-colab.txt #Requirements para rodar no colab
└── README.md #Instruções
```


**Link do dataset/competição:** `https://www.kaggle.com/competitions/ligia-machine-learning/overview`

---

## ✅ Como rodar (Windows / macOS / Linux)

### 1) Pré-requisitos
- **Python 3.13.9** 

### 2) Instalação
```bash
git clone https://github.com/alicebarbosam/fraud-detection-kaggle.git
cd fraud-detection-kaggle

# 2. Criar ambiente virtual
python -m venv .venv

# 3. Ativar ambiente virtual
# Windows
.venv\Scripts\activate
# Linux/Mac
source .venv/bin/activate

# 4. Instalar dependências
pip install -r requirements.txt

# 5. Criar a pasta data
Na raiz, criar uma pasta chamada data e baixar os dados em https://www.kaggle.com/competitions/ligia-machine-learning/data e mover o `train.csv` e `test.csv` para a pasta data
```
### 3) Executar o pipeline completo
```bash


# 1. Executar EDA (opcional)
jupyter notebook eda.ipynb

# 2. Executar Trainamento 
jupyter notebook training.ipynb

# 3. Executar Inferência
jupyter notebook inference.ipynb
```
### 4) Uso rápido
```bash

# 1. Executar notebook de Inferência(ja tem o melhor modelo carregado no repositório)
jupyter notebook inference.ipynb
```

## ✅ Como rodar no colab 
### 1) Instruções
```bash
# 1. Abrir o notebook
No google colab, vá em arquivo -> abrir notebook -> Github e cole o link https://github.com/alicebarbosam/fraud-detection-kaggle/ e escolha a branch main, após isso, abra o notebook desejado

# 2. Rodar a primeira celula(de clone e install requirements-colab.txt)
Rode a primeira celula do notebook que você abrir, ela possue uma marcação "only on colab"

# 3. Upload dos dados
Criar a pasta data na raiz do projeto no explorador do colab após o clone do repositório e baixar os dados em https://www.kaggle.com/competitions/ligia-machine-learning/data e mover o `train.csv` e `test.csv` para a pasta data

# 4. Correção do path
Tive problemas de path ao tentar reproduzir os notebooks no colab, isso é resolvido ajustando manualmente os paths no colab e removendo "../" do início deles
Exemplo:
df = pd.read_csv("../data/train.csv") -> df = pd.read_csv("data/train.csv")
Esse passo deve ser feito em todas as celulas que usem path do notebook
