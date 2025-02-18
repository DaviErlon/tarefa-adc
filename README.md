# Descrição
  Este é um repositório dedicado a um trabalho do projeto EmbarcaTech que envolve o periférico ADC do rp2040, utilizando da placa de desenolvimento BitDogLab. A arquivo principal é o
`tarefa-adc.c`, os arquivos auxiliares para manipulação do display se encontram na pasta `inc` e a compilação deve seguir o arquivo `CMakeLists.txt`.
## Hardware 
  Como este projeto utiliza a placa de desenvolvimento BitDogLab, os periféricos utilizados se encontram nas seguintes GPIOs:
    * GPIO 5: Push Button A.
    * GPIO 22: Push Button Joystick.
    * GPIO 26: Potenciômetro correspondendo ao eixo Y \(ADC canal 0\).
    * GPIO 27: Potenciômetro correspondendo ao eixo X \(ADC canal 1\).
    * GPIO 11: Pino verde de um Led RGB.
    * GPIO 12: Pino azul de um Led RGB.
    * GPIO 13: Pino vermelho de um Led RGB.
    * GPIO 14: Pino I2C SDA do display.
    * GPIO 15: Pino I2C SCL do display.

## Software
  O firmware desse projeto é desenvolvido com o principal intuito de manipular a posição de um quadrado no display e a s cores do led RGB com o joystick. As demais funções são desenvolvidas
com interrupções simples que alteram flags para desenhar bordas no display ou ativar ou desativar o PWM já estudado nas aulas anteriores. Delimitei o espaço válido para leitura do joystick,
ou seja, pûs um limite na leitura do ADC dos eixos dos potenciômetros, fiz isso para criar um retangulo de mesmas proporções do display para ser de fácil conversão para uma coordenada do quadrado,
quando o ADC lê um valor maior que os limites impostos ele entra em desvio condicional que muda o valor do limite, seja o limite da direita ou esquerda ou cima e baixo. Além disso também delimitei
as coordenadas do quadrado para que sempre deixe 3 pixels nas bordas para desenhar bordas personalizadas. Os cálculos necessários não serão muito aprofundados mas satisfaz o conceito da leitura do
ADC seja proporcional as coordenadas do display.

Nota: há um tratamento especial para a coordenada Y visto que para o potenciometro ele cresce de baixo para cima, já as coordenadas do display no eixo Y cresce de cima para baixo.

***

## Vídeo
  Link para o [vídeo]().
