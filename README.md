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
sensor1 = 4;
sensor2 = 3;

Sensor ultrassônico:
pino ECHO = 12;
pino TRIG = 13;

Módulo GPS:



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

#define SSID     "moppe_wireless" : Define o nome do ponto de acesso(wifi) que será utilizado.

#define PASSWORD "Moppe123JAC12" : Senha do ponto de acesso(wifi).

### Biblioteca NewPing

Funções utilizadas:

NewPing us(TRIG, ECHO);

### Biblioteca TinyGPS

Funções utilizadas:

static const uint32_t GPSB = 9600; // definindo a velocidade de comunicação do módulo GPS.

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone who's code was used
* Inspiration
* etc
