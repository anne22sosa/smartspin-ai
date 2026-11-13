# SmartSpin AI: Telemetria e Previsão de Fadiga no Indoor Cycling

**Projeto Final - Especialização em Inteligência Artificial Aplicada (Unisinos)**

O **SmartSpin AI** é uma plataforma preditiva IoT desenvolvida para sessões de *indoor cycling* (spinning). O sistema coleta métricas de desempenho em tempo real, aplica algoritmos de clusterização e redes neurais para prever limites de fadiga e utiliza um agente virtual para sugerir ajustes dinâmicos de carga, prevenindo o *overtraining* e maximizando a queima calórica.

## Arquitetura e Tecnologias

O ecossistema deste projeto baseia-se na integração de três pilares - Internet das Coisas (IoT), processamento escalável em nuvem e modelagem preditiva com Inteligência Artificial:

*   **IoT & Borda (Simulador):** Script Python atuando como sensor virtual, gerando dados de Cadência (RPM), Potência (Watts) e Frequência Cardíaca (BPM).
*   **Mensageria:** Protocolo MQTT (via `paho-mqtt`) para garantir a entrega contínua dos dados de telemetria sem perda de pacotes.
*   **Unsupervised Machine Learning:** Algoritmo K-Means (`scikit-learn`) para clusterizar os dados iniciais do treino e perfilar o condicionamento do usuário sem necessidade de rótulos prévios.
*   **Deep Neural Networks (DNN):** Arquitetura LSTM (`TensorFlow/Keras`) focada em séries temporais para prever a curva de exaustão nos 5 minutos subsequentes.
*   **Reinforce Learning:** Agente treinado (`OpenAI Gym`) que aprende a política ótima de recomendação, sugerindo o aumento ou a redução da resistência (carga) da bicicleta para manter o ciclista na zona alvo.

## Estrutura do Repositório

├── /iot_simulator
│   └── sensor_bike.py        # Simulador gerador de telemetria (RPM, Watts, BPM) e publisher MQTT
├── /ai_models
│   ├── unsupervised.ipynb    # Clusterização do perfil do atleta
│   ├── lstm_fatigue.ipynb    # Treinamento da Rede Neural Profunda para previsão de fadiga
│   └── rl_agent.ipynb        # Agente de Aprendizado por Reforço para ajuste de carga
├── /backend
│   ├── app.py                # Subscriber MQTT e inferência dos modelos em tempo real
│   └── requirements.txt      # Dependências do projeto
└── README.md                 # Documentação principal

## Instalação e Execução

**1. Clone o repositório:**
```bash
git clone [https://github.com/sua-equipe/smartspin-ai.git](https://github.com/sua-equipe/smartspin-ai.git)
cd smartspin-ai