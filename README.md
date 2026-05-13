# TempSensor 🌡️

Sistema de monitoramento de temperatura em tempo real desenvolvido em C++ para placa de prototipagem (Arduino). O projeto realiza a leitura de um sensor analógico (LM35) e exibe os dados processados fisicamente em um display LCD via protocolo I2C, além de enviar os logs via comunicação Serial.

## 🛠️ Tecnologias e Hardwares Utilizados
* **Linguagem:** C/C++
* **Plataforma:** Arduino IDE
* **Hardware:** Arduino Uno (ou compatível), Sensor de Temperatura LM35, Display LCD 16x2 com Módulo I2C.
* **Bibliotecas:** `Wire.h` (Nativa) e `LiquidCrystal_I2C.h`

## 🔌 Esquema de Ligação (Wiring)

**Sensor LM35:**
* Pino 1 (VCC) ➔ 5V do Arduino
* Pino 2 (OUT) ➔ Pino Analógico A0
* Pino 3 (GND) ➔ GND

**Display LCD I2C:**
* VCC ➔ 5V
* GND ➔ GND
* SDA ➔ Pino A4 (SDA)
* SCL ➔ Pino A5 (SCL)

## 🚀 Como executar
1. Clone este repositório.
2. Certifique-se de ter a biblioteca `LiquidCrystal_I2C` instalada na sua Arduino IDE (Gerenciador de Bibliotecas).
3. Abra o arquivo `TempSensor/TempSensor.ino`.
4. Conecte a placa via USB, selecione a porta COM correta e faça o upload.
5. Acompanhe a temperatura pelo display ou abra o Monitor Serial (baud rate: 9600).
