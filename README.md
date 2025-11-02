# Análise de Segurança em Redes IoT com Machine Learning

Este projeto realiza uma análise detalhada de tráfego de rede em um ambiente de Internet das Coisas (IoT) utilizando o protocolo MQTT. O objetivo principal é construir e avaliar diferentes modelos de Machine Learning para a detecção de anomalias e ataques de segurança, como DDoS e DoS.

## Descrição

A análise explora um pipeline completo de ciência de dados, desde a engenharia de features robusta, focada em séries temporais, até a comparação de desempenho entre modelos clássicos, AutoML e redes neurais profundas. O trabalho visa não apenas alcançar alta precisão na detecção, mas também entender o comportamento dos modelos e a importância das variáveis para a classificação do tráfego como benigno ou malicioso.

Este repositório serve como base para um artigo de segurança da informação, demonstrando uma metodologia rigorosa para a criação de um Sistema de Detecção de Intrusão (IDS) eficaz.

## Features da Análise

- **Engenharia de Features Avançada:**
  - **Janelas Deslizantes (Rolling Windows):** Cálculo de média, desvio padrão e máximo para capturar a dinâmica do tráfego.
  - **Features de Atraso (Lag Features):** Utilização de valores passados para fornecer contexto temporal aos modelos.
  - **Features de Tendência (Slope):** Cálculo da inclinação para identificar tendências de aumento ou diminuição nas métricas de tráfego.
  - **Features Cíclicas:** Transformação de dados temporais (hora do dia) em representações contínuas usando seno e cosseno.

- **Modelagem e Comparação:**
  - **Random Forest:** Usado como um modelo de baseline robusto e para seleção de features.
  - **AutoML (FLAML):** Busca automatizada pelo melhor modelo e hiperparâmetros para um benchmark de desempenho.
  - **LSTM (Long Short-Term Memory):** Abordagem com Deep Learning, ideal para dados de série temporal.

- **Validação e Interpretabilidade:**
  - **Validação Cruzada Estratificada:** Garante a robustez e a generalização dos resultados do modelo.
  - **Análise de Curvas (ROC e Precision-Recall):** Avaliação detalhada do desempenho do classificador.
  - **Análise de Erros:** Investigação aprofundada das classificações incorretas.
  - **SHAP (SHapley Additive exPlanations):** Técnicas de XAI (Explainable AI) para interpretar as previsões do modelo.

## Dataset

O conjunto de dados é composto por múltiplos arquivos `.csv`, cada um representando um tipo específico de tráfego de rede MQTT:

- `Benign Traffic.csv` (Tráfego Benigno)
- `MQTT DDoS Publish Flood.csv` (Ataque de Negação de Serviço Distribuído)
- `MQTT DoS Connect Flood.csv` (Ataque de Negação de Serviço)
- `MQTT DoS Publish Flood.csv`
- `MQTT Malformed.csv` (Tráfego com Pacotes Malformados)

## Instalação e Setup

Para executar este projeto, é recomendado criar um ambiente virtual e instalar as dependências listadas.

1. **Clone o repositório:**
   ```sh
   git clone <url-do-repositorio>
   cd UFABC_SI
   ```

2. **Crie e ative um ambiente virtual:**
   ```sh
   python -m venv .venv
   # Windows
   .venv\Scripts\activate
   # macOS/Linux
   source .venv/bin/activate
   ```

3. **Instale as dependências:**
   ```sh
   pip install -r requirements.txt
   ```

## Como Executar

1. Com o ambiente virtual ativado, inicie o Jupyter Lab:
   ```sh
   jupyter lab
   ```

2. No seu navegador, navegue até a pasta `Main/` e abra o notebook `analise_sec_info_new.ipynb`.

3. Execute as células em sequência para reproduzir toda a análise.

## Resultados

A análise comparativa demonstrou que o modelo **Random Forest** alcançou uma performance excepcional, com acurácia e F1-Score próximos de 100%, superando abordagens mais complexas como a LSTM para este conjunto de dados. A seleção de features também se mostrou eficaz, permitindo a criação de um modelo mais simples e computacionalmente mais eficiente sem perda significativa de performance.

Esses resultados sugerem que, para a detecção de ataques em redes MQTT com as features desenvolvidas, um modelo clássico e bem ajustado pode ser a solução mais pragmática e eficaz para um sistema de segurança em tempo real.