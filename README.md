# Estação Metereológica
## Introdução
Estação meteorológica desenvolvida pelo GPADS

As estações meteorológicas de baixo custo representam uma alternativa acessível e eficiente para o monitoramento das condições climáticas. Por meio de sensores eletrônicos, esses equipamentos permitem coletar informações importantes, como temperatura, umidade do ar, pressão atmosférica e outras variáveis meteorológicas. Esses dados contribuem para compreender melhor as características climáticas no Agreste e Sertão, mas também acompanhar possíveis mudanças nas condições do tempo. Nesse contexto, está sendo realizada a instalação e desenvolvimento de estações meteorológicas de baixo custo em cidades do interior de Pernambuco, como Jataúba, Serra Talhada e Caruaru. A iniciativa busca ampliar o acesso a informações meteorológicas locais, permitindo a coleta de dados diretamente nessas localidades. Além de contribuir para o desenvolvimento de pesquisas e estudos climáticos, o projeto pode auxiliar a população, os agricultores e outros setores que dependem das condições do tempo em suas atividades.

## Resumo de funcionamento

A estação meteorológica é composta por um microcontrolador ESP32, responsável por processar os dados coletados pelos sensores e enviá-los para um dashboard, onde as informações podem ser visualizadas e acompanhadas. O sistema monitora oito variáveis: umidade, temperatura, concentração de CO₂, luminosidade, índice UV, pressão atmosférica, velocidade do vento (anemômetro) e volume de chuva (pluviômetro). Sua alimentação energética é realizada por um conjunto de três baterias de 2.200 mAh, recarregadas por meio de uma placa solar. Dessa forma, a estação utiliza energia solar para manter seu funcionamento e realizar o monitoramento contínuo das condições ambientais.


## Descrição das pinagens e conexões

A estação meteorológica utiliza um ESP32 como unidade central de processamento, responsável pela comunicação com os sensores e módulos periféricos. As conexões estão organizadas principalmente em dois grupos: o barramento I²C, compartilhado por vários sensores, e as conexões individuais utilizadas pelos módulos de medição.

### Conexões dos sensores e módulos
- BME680: sensor conectado ao barramento I²C, utilizando os pinos D23 (SCL) e D22 (SDA). Sua alimentação é realizada pelo pino 3V3, com GND comum.
- INA219: módulo de monitoramento elétrico conectado ao barramento I²C, também utilizando D23 (SCL) e D22 (SDA). Possui conexões de alimentação VCC e GND, além dos terminais VIN+ e VIN− para medição elétrica.
- SCD40: sensor conectado ao barramento I²C, utilizando D23 (SCL) e D22 (SDA), com alimentação de 3,3 V e GND.
- DS1307: módulo de relógio de tempo real (RTC), conectado ao barramento I²C pelos pinos D23 (SCL) e D22 (SDA).
- BH1750: sensor de luminosidade conectado ao barramento I²C, utilizando os mesmos pinos de comunicação. A planilha indica o pino ADDR conectado ao GND.
- Módulo MicroSD: utiliza comunicação SPI, com as seguintes conexões:
  - D7: MOSI;
  - D2: MISO;
  - D6: SCK;
  - D3: CS.
- LED Neopixel: conectado individualmente ao pino D8 do ESP32, por meio do sinal SIG.
- Sensor UV (UVM-30A): conectado ao pino D1 por meio da saída OUT, com alimentação de 3,3 V e GND.
- Pluviômetro: conectado ao pino D11 por meio do sinal SIG. A planilha indica alimentação e aterramento, mas não detalha o circuito interno do sensor.
- Anemômetro HWFS-1: utiliza uma conexão individual com o ESP32. O esquema apresenta os fios positivo e negativo, além de um circuito com resistores de 1 kΩ e 4,7 kΩ para formar um nó de medição.

### Alimentação elétrica
O sistema possui uma alimentação baseada em energia solar, utilizando um banco de três baterias de 2.200 mAh. A energia é fornecida por uma placa solar e gerenciada pelo circuito de alimentação.

De acordo com o esquema, o sistema apresenta:
- 3V3: alimentação dos sensores e módulos compatíveis com essa tensão.
- 5V: linha de alimentação indicada para o ESP32 e para o circuito de gerenciamento.
- GND: referência elétrica comum entre o microcontrolador e os periféricos.
- INA219: responsável pela medição de parâmetros elétricos por meio dos terminais VIN+ e VIN−.
Observação técnica: a planilha apresenta duas possibilidades de ligação, uma com o gerenciador fotovoltaico e outra sem ele. Antes da montagem definitiva, é importante confirmar o caminho da alimentação, especialmente as conexões VIN+ e VIN− do INA219, e verificar a tensão exigida por cada módulo. Também é necessário conferir a identificação exata da placa ESP32 e seus pinos, pois a planilha menciona ESP32-C6-DEV-MODULE e uma pinagem de 30 vias.
