# Testes do Projeto

Os testes iniciais do carrinho autônomo de irrigação concentraram-se na verificação das funcionalidades básicas. Primeiramente, avaliamos a capacidade de locomoção do carrinho. Foram realizados testes para confirmar se o 
chassi 2WD, em conjunto com os motores DC e o módulo motor, permitia que o carrinho se movesse para frente, para trás e executasse manobras laterais conforme o esperado. Esta etapa foi fundamental para assegurar a 
funcionalidade da plataforma mecânica.
Posteriormente, a atenção foi direcionada aos sensores de umidade. Tanto o sensor de umidade do solo capacitivo quanto o sensor de umidade da estação fixa foram submetidos a testes rigorosos. O objetivo era verificar a 
precisão das leituras de umidade e, crucialmente, a eficácia da transmissão desses dados por meio dos módulos RF 433MHz (TX e RX) para o sistema de monitoramento. Esta fase demandou múltiplas tentativas e ajustes para a 
calibração dos sensores e a otimização da comunicação sem fio, garantindo a transmissão e recepção confiável dos sinais.
Com a locomoção e a comunicação dos sensores estabelecidas, procedemos aos testes da bomba de água. Verificou-se se o relé acionava a bomba de forma adequada e se a bomba era capaz de bombear água eficientemente através do 
tubo transparente. Os testes asseguraram que a bomba ligava e desligava conforme os comandos e que o fluxo de água era apropriado para a irrigação.
Finalmente, foram conduzidos testes do sistema integrado, nos quais todos os componentes do carrinho autônomo de irrigação foram combinados e avaliados em um cenário operacional simulado. Isso incluiu a verificação da 
detecção de baixa umidade do solo pelo carrinho, seu deslocamento para a área designada, o acionamento da bomba para irrigação e a desativação da bomba ao atingir o nível de umidade desejado. A comunicação entre a estação 
fixa e o carrinho foi monitorada continuamente para garantir que o ciclo completo de irrigação ocorresse de maneira autônoma e eficiente. Esses testes integrados foram essenciais para validar o desempenho global do sistema 
como uma unidade coesa.
