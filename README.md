# TEMP-SENSOR
//sensor de temperatura com variaçaõ de parâmetros//
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Configuração do display LCD I2C (Endereço padrão 0x27, 16 colunas, 2 linhas)
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Definição do pino do sensor
const int pinoLM35 = A0; 

void setup() {
  // Inicializa a comunicação serial para monitoramento no PC
  Serial.begin(9600);
  
  // Inicializa o LCD
  lcd.init();      
  lcd.backlight(); 

  // Mensagem de inicialização
  lcd.setCursor(0, 0);
  lcd.print("TempSensor Init.");
  delay(2000);
  lcd.clear();
}

void loop() {
  // 1. Faz a leitura do valor analógico no pino A0 (retorna de 0 a 1023)
  int leituraADC = analogRead(pinoLM35);

  // 2. Converte a leitura do ADC para Tensão em Volts (considerando Arduino a 5V)
  float tensao = leituraADC * (5.0 / 1023.0);

  // 3. Converte a tensão para Temperatura (O LM35 varia 10mV ou 0.01V por grau Celsius)
  float temperaturaC = tensao / 0.01;

  // Exibe o resultado no Monitor Serial
  Serial.print("Temperatura: ");
  Serial.print(temperaturaC);
  Serial.println(" °C");

  // Exibe o resultado no Display LCD
  lcd.setCursor(0, 0);
  lcd.print("Temp: ");
  lcd.print(temperaturaC, 1); // Exibe com 1 casa decimal
  lcd.print(" C    ");        // Espaços extras para limpar caracteres residuais

  // Aguarda 1 segundo antes da próxima leitura
  delay(1000); 
}
