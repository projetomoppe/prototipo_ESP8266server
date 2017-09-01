# O uso de redes de sensores para monitoramento da bacia hidrográfica do rio Jacaraípe para prediçao de enchentes

O projeto tem como intuito construir um dispositivo para monitoramento de nível d'água que será utilizado no rio Jacaraípe para alertar a população local sobre possíveis enchentes e alagamentos. 

## Introdução

Para que o desenvolvimento e implementação do protótipo acontecesse, foi realizada uma pesquisa de componentes e sistemas embarcados para saber qual seria mais viável para o projeto, e o Arduino foi o que mais atendeu às nossas necessidades.

### Pré-requisitos

Para o protótipo ser construído, foi necessário alguns componentes para o Arduino chamados Shields. os Shields, são componentes ligados diretamente à ele, com diversas finalidades, tais como: medir a distância a partir de ondas sonoras que é feita pelo sensor ultrassônico, etc.

```
Os sensores ou Shields, fazem a leitura dos dados, que são enviados ao Arduino que por meio de códigos
em linguagem C de programação, podem ser exibidos no Serial Monitor ou enviados para outro lugar.
```

## Pinagem dos dispositivos

Sensores ICOS:                                                                                                            
sensor1 - pino de dados 4 e 5v.                                                                                           
sensor2 - pino de dados 3 e 5v.

Sensor ultrassônico:                                                                                                        
pino 12 - ligação do pino ECHO.                                                                                           
pino 13 - ligação do pino TRIGGER.                                                                                         
pino GND.
pino 5v.

Módulo GPS:                                                                                                               
portas serial RX3 e TX3 para comunicação.                                                                                   
porta GND.                                                                                                                  
alimentação com divisor de tensão para 3v(pino vcc com 2 resistores, 4.7k e 10k).

Módulo Wifi:                                                                                                                


## Construído com

https://github.com/itead/ITEADLIB_Arduino_WeeESP8266 - weeESP8266 utilizada no módulo wifi.
https://bitbucket.org/teckel12/arduino-new-ping/downloads/ - NewPing utilizada no módulo ultrassônico.
https://github.com/mikalhart/TinyGPSPlus/releases/tag/v0.95 - TinyGPS utilizada no módulo GPS.


### Biblioteca weeESP8266

funções utilizadas:

bool 	setOprToStation (void) : Define o modo de operação para a estação.

bool 	joinAP (String ssid, String pwd) : Entra em um ponto de acesso wifi.

String 	getLocalIP (void) : obtém o endereço IP para o módulo ESP8266.

bool 	enableMUX (void) : Habilita multiplas conexões com o módulo.

bool 	startTCPServer (uint32_t port=333) : inicia o servidor TCP(somente em modo múltipo).

bool 	setTCPServerTimeout (uint32_t timeout=180) : Define o tempo limite do servidor TCP.

bool 	send (uint8_t mux_id, const uint8_t *buffer, uint32_t len) : Envia dados com base em um dos TCP ou UDP construídos já em modo múltiplo.

bool lenght :

bool 	releaseTCP (uint8_t mux_id) : Libere a conexão TCP no modo múltiplo.

String 	getIPStatus (void) : Obtenha o status atual da conexão (UDP e TCP).

#define SSID  "moppe_wireless" : Define o nome do ponto de acesso(wifi) que será utilizado.

#define PASSWORD  "Moppe123JAC12" : Senha do ponto de acesso(wifi).

### Biblioteca NewPing

Funções utilizadas:

NewPing us(TRIG, ECHO);

### Biblioteca TinyGPS

Funções utilizadas:

static const uint32_t GPSB = 9600; // definindo a velocidade de comunicação do módulo GPS.

### Funções dos dispositivos

Sensores ICOS: medir nível de acordo com seu estado que varia entre 0 e 1. À medida que o nível sobe, passa pelo sensor, mudando seu estado. O sensor pode estar normalmente aberto(0) ou normalmente fechado(1).

Sensor ultrassônico: medir nível com ondas sonoras que rebatem na água e mostra exatamente a altura do nível. Também é possível medir a velocidade em que o nível sobe para assim realizar uma estitamita de tempo em que o nível subirá até um nível crítico.

Módulo GPS: exibir a localização do protótipo e mostrar dados como data e hora.

Módulo Wifi: enviar os dados lidos pelos dispositivos para um servidor, onde serão exibidos num website para que qualquer pessoa tenha acesso aos dados lidos em tempo real.
