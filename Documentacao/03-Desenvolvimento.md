
# Materiais
- Arduino UNO ou ESP32 – Responsável pelo controle central do sistema (movimentação, sensores e irrigação).
- Sensor de Umidade do Solo – Detecta o nível de umidade do solo para decidir quando irrigar.
- Sensor Ultrassônico ou Infravermelho – Detecta obstáculos para navegação segura do carrinho.
- Sensor GPS (caso utilizado) – Permite rastreamento e localização geográfica do carrinho.
- Motores DC ou Motores com Redutor – Utilizados para movimentar o carrinho.
- Servo Motores – Para direcionamento ou controle de válvulas.
- Bomba de Água – Responsável por impulsionar a água até os sistemas de irrigação.
- Mangueiras de gotejamento ou bicos pulverizadores – Para irrigação direta nas plantas.
- Válvulas e Atuadores (elétricos ou mecânicos) – Controlam o fluxo de água.
- Módulo Bluetooth (HC-05/HC-06) – Comunicação entre o carrinho e o aplicativo.
- Módulo Wi-Fi (caso ESP32 ou ESP8266) – Alternativa para controle remoto via rede.
- Chassi de Carrinho Robótico – Base para montagem dos componentes.
- Rodas e Eixos – Para movimentação do sistema.
- Protoboard e Fios Jumper – Montagem dos circuitos de teste.
- Caixa ou Suporte para Componentes – Proteção e organização dos elementos eletrônicos.


# Desenvolvimento

Durante o desenvolvimento do projeto do carrinho autônomo para irrigação, enfrentamos diversos desafios, principalmente relacionados ao sistema de irrigação em si e à movimentação autônoma do carrinho.

O primeiro passo foi a definição do escopo e da abordagem de construção. Tivemos várias ideias iniciais sobre como montar o carrinho, incluindo a possibilidade de montar todo o chassi do zero. No entanto, para otimizar o tempo e facilitar a montagem da parte elétrica e de irrigação, optamos por adquirir um chassi de carrinho já pronto. Este chassi veio com estrutura básica, suporte para motores e encaixes adequados, o que nos permitiu focar diretamente na parte eletrônica e funcional do projeto.

Assim que o chassi chegou, realizamos a montagem mecânica com a fixação das rodas e componentes estruturais utilizando parafusos. Em seguida, iniciamos o desenvolvimento da parte elétrica, necessária para movimentar o carrinho de forma autônoma. Originalmente, a movimentação seria feita com o auxílio de uma ponte H (como o módulo L298N), responsável por controlar o sentido de rotação dos motores DC. No entanto, como não havíamos adquirido o módulo a tempo, tivemos o apoio do monitor de LIEC, Fernando, que nos orientou em uma alternativa funcional.

A solução encontrada foi utilizar quatro módulos de relé comuns, cada um destinado a controlar uma direção do carrinho: frente, ré, direita e esquerda. Cada relé foi conectado de forma a controlar o funcionamento individual dos motores, permitindo que o carrinho se movesse conforme os comandos recebidos. Os relés foram ligados aos pinos de controle do microcontrolador e configurados por meio de lógica digital para acionar os motores conforme a direção desejada.

Antes da montagem completa do sistema de movimentação, montamos também a base fixa que ficaria próxima à planta. Essa base é responsável por monitorar a umidade do solo e transmitir a informação para o carrinho. Para isso, utilizamos um Arduino Uno e uma protoboard, onde conectamos um sensor de umidade de solo capacitivo. O sensor detecta quando o solo está seco e, por meio de um sistema de comunicação (como módulos RF 433 MHz ou Bluetooth, dependendo da versão final), envia um sinal ao carrinho.

A lógica do projeto prevê que, ao receber esse sinal, o carrinho se locomove até o local da planta e ativa o sistema de irrigação, que é composto por uma bomba d'água acionada por um módulo relé separado. Esse processo envolve tanto a leitura dos sensores quanto o controle dos atuadores, exigindo sincronia entre os módulos de detecção e os módulos de ação.

Ao longo do processo, realizamos diversos testes de movimentação, acionamento dos relés e detecção da umidade, corrigindo problemas de ligação, alimentação elétrica e programação. O suporte da equipe, especialmente do monitor Fernando, foi essencial para que conseguíssemos uma alternativa viável para a movimentação do carrinho mesmo sem a ponte H tradicional.

## Desenvolvimento do Aplicativo

A criação do aplicativo foi um processo relativamente rápido, no qual dedicamos atenção especial à parte estética e à organização da interface. Optamos por estruturar o app com três telas principais:

Apesar da interface ter sido construída de forma simples e intuitiva, a parte de programação do aplicativo apresentou alguns desafios. Foi necessário pensar em toda a lógica de funcionamento final do carrinho para que o app conseguisse interpretar corretamente os comandos enviados. Isso incluiu a configuração da conexão Bluetooth, o envio dos sinais de controle, e a definição dos comandos que o carrinho deveria executar a partir da comunicação recebida.

Pensar nessa integração entre o app e o hardware foi essencial para garantir que o sistema funcionasse corretamente, especialmente nos momentos em que o carrinho deveria se mover ou iniciar a irrigação automaticamente.

### Interface

Tela de Login: Essa foi a primeira tela desenvolvida. Ela serve apenas para fins de apresentação, simulando um sistema de autenticação, onde os dados de login são fornecidos de forma manual e pré-configurada.
Tela Principal: Essa é a tela funcional do aplicativo. Seu principal objetivo é realizar a conexão via Bluetooth com o carrinho. Nela, o usuário pode ativar ou desativar o sistema de irrigação, além de verificar o status do solo, recebido por meio da comunicação com o Arduino.
Tela de Controle: Esta tela foi pensada para o controle da movimentação do carrinho. Através de botões direcionais, o usuário pode enviar comandos para que o carrinho se mova para frente, para trás, para a esquerda ou para a direita, conforme a necessidade.

### Código

O desenvolvimento do código do aplicativo foi feito utilizando a plataforma MIT App Inventor, que oferece uma interface gráfica baseada em blocos, facilitando a criação de aplicativos Android mesmo sem conhecimento aprofundado em linguagens de programação.

A lógica principal do app foi dividida em três partes:

Conexão Bluetooth: Programamos a funcionalidade de busca e conexão com dispositivos Bluetooth disponíveis. Uma vez conectado ao módulo Bluetooth do carrinho, o app passa a enviar comandos e receber dados.
Envio de Comandos: Criamos blocos para enviar comandos específicos por meio da conexão Bluetooth. Esses comandos foram definidos previamente no código do Arduino/ESP, como letras ou números que representam ações (por exemplo, “A” para ativar a irrigação, “F” para frente, “D” para direita, etc.).
Interface Responsiva: Também programamos os botões e elementos visuais para responder às ações do usuário, garantindo uma experiência intuitiva e funcional.

## Desenvolvimento do Hardware

### Montagem

A montagem do projeto começou com a preparação da base do carrinho, utilizando um chassi comprado pronto, que já vinha com espaço para os motores e suporte para baterias. Isso facilitou a fixação das rodas e a estruturação do sistema de movimentação.

Após a montagem física do carrinho, passamos para a instalação da parte elétrica. Como não utilizamos uma ponte H tradicional (como o L298N), montamos o sistema de controle dos motores com quatro módulos de relé, cada um responsável por uma direção: frente, ré, esquerda e direita. Esses relés foram conectados aos motores DC do carrinho e controlados por pinos digitais do microcontrolador.

Paralelamente, montamos também o sistema fixo da planta, com um sensor de umidade capacitivo conectado a um Arduino (ou ESP32). Esse sensor é responsável por detectar a umidade do solo e enviar um sinal ao carrinho, indicando quando a irrigação deve ser acionada.

### Desenvolvimento do Código

O código embarcado foi desenvolvido para controlar os motores, a bomba d’água e receber os comandos via comunicação Bluetooth ou módulo RF, dependendo da versão utilizada.

No programa, definimos os pinos de controle dos relés responsáveis pelo movimento e também o pino do relé que aciona a bomba de irrigação. O código foi estruturado para ler os comandos recebidos (como letras ou números) e, a partir disso, acionar os relés correspondentes.

Além disso, no sistema fixo da planta, o sensor de umidade foi configurado para ler os níveis de umidade em tempo real e enviar um sinal lógico ao carrinho sempre que o solo estivesse seco, garantindo o acionamento da irrigação.

O código foi escrito na IDE do Arduino, testado em etapas e ajustado conforme a necessidade de integração com o aplicativo e com os módulos de comunicação.

## Comunicação entre App e Hardware

A comunicação entre o aplicativo e o carrinho foi feita por meio de módulos Bluetooth (como o HC-05 ou similar). No aplicativo, configuramos o componente BluetoothClient para procurar dispositivos disponíveis, conectar-se ao módulo do carrinho e enviar os comandos via texto.

Esses comandos são interpretados no código do Arduino/ESP como sinais de controle. Por exemplo:

O comando “1” pode significar "ligar irrigação";
O comando “F” indica movimento para frente;
O comando “P” representa parada.
Quando o solo está seco, o sensor envia essa informação ao microcontrolador, que pode repassá-la ao app (dependendo da lógica usada), ou agir diretamente iniciando a irrigação.

Essa comunicação bidirecional garantiu a integração eficiente entre o controle do usuário (via app) e a execução das ações pelo hardware, tornando o sistema completo e funcional.
