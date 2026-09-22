# 🖥️ Projeto Arduino com Display OLED

## 📌 Sobre o projeto

Este projeto foi desenvolvido utilizando **Arduino** e um **display OLED de 128x64 pixels**, com comunicação através do protocolo **I2C**.

O objetivo do projeto é inicializar o display OLED e apresentar uma mensagem personalizada na tela:

> **Thais.P + Caio.M**

O código utiliza bibliotecas específicas para controlar o display e configurar a comunicação entre o Arduino e o OLED.

## 🛠️ Tecnologias e componentes

### Software

* Arduino IDE
* Linguagem C/C++ (Arduino)
* Bibliotecas:

  * `Wire.h`
  * `Adafruit GFX Library`
  * `Adafruit SSD1306`

### Hardware

* Arduino
* Display OLED 128x64
* Comunicação I2C

## 📚 Bibliotecas utilizadas

### Wire.h

Biblioteca utilizada para estabelecer a comunicação **I2C** entre o Arduino e o display OLED.

### Adafruit GFX

Biblioteca gráfica utilizada para trabalhar com textos, formas e outros elementos gráficos em displays.

### Adafruit SSD1306

Biblioteca responsável pelo controle do display OLED baseado no controlador **SSD1306**.

## ⚙️ Configuração do display

O display utilizado possui as seguintes configurações:

| Configuração   | Valor         |
| -------------- | ------------- |
| Largura        | 128 pixels    |
| Altura         | 64 pixels     |
| Comunicação    | I2C           |
| Endereço I2C   | `0x3C`        |
| Reset dedicado | Não utilizado |

## 🔌 Comunicação I2C

O display é inicializado utilizando a comunicação I2C através da biblioteca `Wire`.

O endereço utilizado no código é:

```cpp
0x3C
```

Esse endereço é utilizado para identificar o display na comunicação I2C.

## 🖥️ Funcionamento

Ao iniciar o Arduino, o programa executa as seguintes etapas:

1. Inicia a comunicação serial com velocidade de **9600 baud**.
2. Inicializa o display OLED.
3. Verifica se o display foi iniciado corretamente.
4. Define o tamanho do texto como **2**.
5. Define a cor do texto como **branco**.
6. Limpa o conteúdo anterior do display.
7. Posiciona o cursor na coordenada `(0, 10)`.
8. Exibe a mensagem **"Thais.P + Caio.M"**.
9. Atualiza o display para mostrar a mensagem.

Caso o OLED não seja inicializado corretamente, uma mensagem de erro será exibida no Monitor Serial:

```text
Erro ao iniciar o OLED
```

## 💻 Código principal

```cpp
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define LARGURA_OLED 128
#define ALTURA_OLED 64

Adafruit_SSD1306 telaOLED(
  LARGURA_OLED,
  ALTURA_OLED,
  &Wire,
  -1
);

void setup() {

  Serial.begin(9600);

  if (!telaOLED.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    Serial.println("Erro ao iniciar o OLED");
    for(;;);
  }

  telaOLED.setTextSize(2);
  telaOLED.setTextColor(WHITE);

  telaOLED.clearDisplay();

  telaOLED.setCursor(0, 10);

  telaOLED.println("Thais.P + Caio.M");

  telaOLED.display();
}

void loop() {

}
```

## ▶️ Como executar

### 1. Instalar a Arduino IDE

Instale a Arduino IDE no computador.

### 2. Instalar as bibliotecas

No gerenciador de bibliotecas da Arduino IDE, procure e instale:

* **Adafruit GFX Library**
* **Adafruit SSD1306**

A biblioteca `Wire` normalmente já acompanha a instalação da Arduino IDE.

### 3. Conectar o hardware

Conecte o display OLED ao Arduino utilizando os pinos correspondentes à comunicação I2C.

### 4. Abrir o código

Abra o arquivo do projeto na Arduino IDE.

### 5. Selecionar a placa

Na Arduino IDE, selecione a placa Arduino utilizada e a porta correspondente.

### 6. Fazer o upload

Compile o código e envie para o Arduino.

Após a inicialização, o display deverá apresentar:

```text
Thais.P + Caio.M
```

## 📸 Resultado esperado

Após o programa ser executado corretamente, o display OLED deverá mostrar a mensagem personalizada no tamanho de texto configurado.

## 👩‍💻 Autores

**Thais.P + Caio.M**

## 📄 Licença

Projeto desenvolvido para fins **educacionais e acadêmicos**.
