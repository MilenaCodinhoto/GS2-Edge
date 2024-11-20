# Monitoramento de Consumo com ESP32 e MQTT

Este projeto utiliza um ESP32 para monitorar o consumo elétrico a partir de um potenciômetro, publicando as informações em um broker MQTT. Ele também classifica o consumo em "Baixo", "Moderado" ou "Alto" com base em limites predefinidos. Os dados são enviados ao tópico MQTT configurado, permitindo sua integração em sistemas de IoT.

---

## Integrantes
- Milena Codinhoto
- Evellyn Valencia
- Carolina Ferraz

---
### Link do video <https://youtu.be/McqDoO7Afrc>

---

## Funcionalidades

- **Conexão Wi-Fi**: O ESP32 se conecta à rede Wi-Fi para comunicação com o broker MQTT.
- **Leitura do potenciômetro**: Mede a corrente elétrica simulada e calcula a potência instantânea.
- **Cálculo de consumo médio**: Calcula o consumo médio baseado em leituras acumuladas.
- **Classificação do consumo**:
  - **Baixo**: Abaixo de 50 W.
  - **Moderado**: Entre 50 W e 150 W.
  - **Alto**: Acima de 150 W.
- **Publicação MQTT**: Envia os dados (consumo médio e classificação) para o broker MQTT no formato JSON.

---

## Requisitos

- **Hardware**:
  - ESP32
  - Potenciômetro conectado ao pino analógico (Pino `34`).

- **Software**:
  - Arduino IDE com as bibliotecas:
    - [WiFi](https://www.arduino.cc/reference/en/libraries/wifi/)
    - [PubSubClient](https://pubsubclient.knolleary.net/)

---

## Configuração

### Wi-Fi
Edite as linhas abaixo para configurar sua rede Wi-Fi:
```cpp
const char* ssid = "SEU_SSID";
const char* password = "SUA_SENHA";
```

### MQTT
Defina o servidor e o tópico MQTT:
```cpp
const char* mqttServer = "test.mosquitto.org";
const int mqttPort = 1883;
const char* mqttTopic = "casa/consumo_potenciometro";
```

---

## Funcionamento do Código

1. **Setup**:
   - Conecta ao Wi-Fi e inicializa o cliente MQTT.
   
2. **Loop Principal**:
   - Verifica a conexão Wi-Fi e MQTT.
   - Lê a entrada analógica do potenciômetro.
   - Calcula a potência instantânea e o consumo médio.
   - Classifica o estado do consumo.
   - Publica os dados no broker MQTT.

3. **Reconexão Automática**:
   - Reconfigura o Wi-Fi e reconecta ao broker MQTT se a conexão for perdida.

---

## Formato dos Dados Enviados

Os dados são enviados ao tópico configurado em formato JSON:
```json
{
  "Consumo_Medio": 120.50,
  "Estado": "Moderado"
}
```

---

## Personalização

- **Limites de Classificação**: Ajuste os valores conforme necessário:
  ```cpp
  const float limiteBaixo = 50.0;   
  const float limiteModerado = 150.0; 
  const float limiteAlto = 300.0;
  ```
- **Frequência de Atualização**: Altere o tempo entre leituras ajustando `delay(1000)` no `loop()`.

---

## Licença

Este é um projeto acadêmico.
