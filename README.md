Sistema de Monitoramento de Consumo Elétrico com ESP32 e MQTT
Este projeto utiliza o ESP32 com um potenciômetro para simular o consumo de energia em uma residência ou empresa. Os dados de consumo são enviados para um broker MQTT (ex: test.mosquitto.org) e podem ser monitorados em tempo real.

Funcionalidades
Leitura de Potenciômetro: O potenciômetro conectado ao pino analógico do ESP32 simula o consumo de energia.
Cálculo de Potência: O código calcula a potência instantânea e a média do consumo em watts (W) com base na leitura do potenciômetro.
Classificação de Consumo: O sistema classifica o consumo em três categorias: Baixo, Moderado e Alto.
Envio para MQTT: O consumo médio e seu estado (Baixo, Moderado, Alto) são enviados para um broker MQTT para monitoramento remoto.
Materiais Necessários
ESP32 (Placa de Desenvolvimento)
Potenciômetro
Broker MQTT (ex: test.mosquitto.org)
Bibliotecas Requeridas
WiFi.h: Para conectar o ESP32 à rede Wi-Fi.
PubSubClient.h: Para a comunicação com o broker MQTT.
Configurações
Wi-Fi
Altere as credenciais Wi-Fi para se conectar à sua rede local:
