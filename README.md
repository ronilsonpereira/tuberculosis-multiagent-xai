# Multi-Agent Explainable Decision Support System for Tuberculosis Outcome Prediction

Este repositório contém o código-fonte da arquitetura baseada em **Sistemas Multiagentes (SMA)** integrada a **Inteligência Artificial Explicável (XAI)** para a predição e explicação do desfecho do tratamento da tuberculose utilizando dados epidemiológicos.

## 📌 Arquitetura do Sistema

A solução organiza o fluxo de aprendizado de máquina em agentes especializados:

* **DataAgent**: Responsável pela carga, pré-processamento (imputação e codificação) e seleção das 10 principais variáveis explicativas via ganho de informação (Embedded Feature Selection).
* **PredictiveAgent**: Executa a predição probabilística do desfecho utilizando o algoritmo XGBoost.
* **EvaluationAgent**: Realiza a varredura do limiar de decisão (*threshold tuning*) focado na maximização do **F1 Score macro**.
* **ExplainabilityAgent**: Gera atribuições globais e locais de importância para cada preditor empregando os valores **SHAP (SHapley Additive exPlanations)**.
* **DecisionSupportAgent**: Modula e consolida a decisão com seu respectivo relatório interpretável para apoio ao profissional de saúde.

## 🛠️ Tecnologias e Bibliotecas Utilizadas

* **Python 3.10+**
* **Scikit-Learn** & **XGBoost**
* **Imbalanced-Learn** (`SMOTETomek`)
* **SHAP** (Explicabilidade baseada em Teoria dos Jogos)
* **Seaborn** & **Matplotlib**

## 🚀 Como Executar

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/ronilsonpereira/tuberculosis-multiagent-xai.git
   cd tuberculosis-multiagent-xai