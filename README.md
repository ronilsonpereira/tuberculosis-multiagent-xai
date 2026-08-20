# Multi-Agent Explainable Decision Support System for Tuberculosis Outcome Prediction

Este repositório contém o código, a documentação e os procedimentos de execução do sistema baseado em **Sistemas Multiagentes (SMA)** e **Inteligência Artificial Explicável (XAI)** para a predição e explicação do desfecho do tratamento da tuberculose utilizando dados epidemiológicos.

---

## 📌 Arquitetura do Sistema

A solução organiza o fluxo de aprendizado de máquina em agentes especializados e independentes:

* **DataAgent**: Carga, limpeza, imputação, codificação e seleção de variáveis relevantes.
* **PredictiveAgent**: Treinamento e geração de inferências probabilísticas via XGBoost.
* **EvaluationAgent**: Otimização do limiar de decisão focado na maximização do **F1 Score macro**.
* **ExplainabilityAgent**: Atribuição de importância global e local às variáveis utilizando valores **SHAP**.
* **DecisionSupportAgent**: Consolidação e geração de relatórios interpretáveis para o apoio à decisão médica.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

* **Python 3.10+**
* **Scikit-Learn** & **XGBoost**
* **Imbalanced-Learn** (`SMOTETomek`)
* **SHAP** (Explicabilidade baseada em Teoria Games)
* **Seaborn** & **Matplotlib**

---

## 🚀 Como Executar

Escolha uma das opções abaixo para rodar o sistema de predição:

### 💻 Opção 1: Execução Local (Terminal)

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/ronilsonpereira/tuberculosis-multiagent-xai.git
   cd tuberculosis-multiagent-xai
   ```

2. **Crie e ative o ambiente virtual:**
   * **Linux/macOS:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```
   * **Windows:**
     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```

3. **Instale as dependências:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Prepare a base de dados:**
   * Crie uma pasta chamada `data` na raiz do projeto (se ela já não existir).
   * Cole o seu arquivo de dados `tuberculosis.csv` obrigatoriamente dentro dessa pasta `data/`.

5. **Execute o sistema:**
   ```bash
   python main.py
   ```

---

### ☁️ Opção 2: Execução no Google Colab (Notebook)

Crie um novo notebook no Google Colab e execute as células abaixo para rodar o pipeline:

1. **Clonar o projeto e instalar dependências:**
   ```python
   !git clone https://github.com/ronilsonpereira/tuberculosis-multiagent-xai.git
   %cd tuberculosis-multiagent-xai
   !pip install xgboost imbalanced-learn shap -q
   ```

2. **Fazer o upload da base de dados:**
   ```python
   import os
   from google.colab import files

   # Garante a criação da pasta de dados
   os.makedirs("data", exist_ok=True)
   uploaded = files.upload()

   # Move o arquivo carregado para a pasta correta
   for filename in uploaded.keys():
       os.rename(filename, os.path.join("data", filename))
   ```

3. **Executar o sistema e exibir resultados:**
   ```python
   !python main.py

   # Exibir o gráfico de explicabilidade global gerado pelo SHAP
   from IPython.display import Image, display
   display(Image(filename='global_xai.png'))
   ```
