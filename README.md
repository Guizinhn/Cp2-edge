Projeto Arduino – Sistema de Monitoramento de Luminosidade
📋 Descrição do Projeto
Este projeto foi desenvolvido com o objetivo de criar um sistema simples de monitoramento de luminosidade, utilizando componentes eletrônicos básicos controlados por uma placa Arduino Uno.
A proposta principal é simular uma situação em que a variação de luz no ambiente aciona diferentes sinais visuais (LEDs) e sonoros (buzzer).

🧰 Componentes Utilizados
Arduino Uno: Microcontrolador responsável por processar os dados do sensor de luz e acionar LEDs e buzzer conforme a lógica programada.

Protoboard (Placa de Ensaio): Utilizada para a montagem e organização dos circuitos eletrônicos.

LEDs (verde, amarelo e vermelho): Indicadores visuais que representam diferentes faixas de intensidade luminosa.

Buzzer: Emissor de som utilizado como alerta sonoro em situações de luminosidade elevada.

Sensor de Luz (LDR – Light Dependent Resistor): Mede a quantidade de luz no ambiente. Sua resistência varia conforme a intensidade luminosa.

Resistores: Protegem os LEDs e garantem a leitura correta do sensor LDR.

⚙️ Funcionamento
O sistema realiza leituras constantes da luminosidade ambiente por meio do sensor LDR.
Com base no valor obtido, ele executa as seguintes ações:

Baixa luminosidade: Acende o LED verde.

Luminosidade média: Acende o LED amarelo.

Alta luminosidade: Acende o LED vermelho e aciona o buzzer por 3 segundos, seguido de uma pausa de 2 segundos.

💻 Código Arduino
cpp
Copiar
Editar
const int pinoSensorLuz = A0;
const int ledVerde = 2;
const int ledAmarelo = 3;
const int ledVermelho = 4;
const int buzina = 5;

const int limiarBaixo = 500;
const int limiarMedio = 800;

void setup() {
  pinMode(ledVerde, OUTPUT);
  pinMode(ledAmarelo, OUTPUT);
  pinMode(ledVermelho, OUTPUT);
  pinMode(buzina, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int leituraLuz = analogRead(pinoSensorLuz);
  Serial.println(leituraLuz);

  digitalWrite(ledVerde, LOW);
  digitalWrite(ledAmarelo, LOW);
  digitalWrite(ledVermelho, LOW);
  digitalWrite(buzina, LOW);

  if (leituraLuz < limiarBaixo) {
    digitalWrite(ledVerde, HIGH);
  } else if (leituraLuz < limiarMedio) {
    digitalWrite(ledAmarelo, HIGH);
  } else {
    digitalWrite(ledVermelho, HIGH);
    digitalWrite(buzina, HIGH);
    delay(3000);
    digitalWrite(buzina, LOW);
    delay(2000);
  }

  delay(1000);
}
🔗 Links Úteis
💡 Tinkercad do Projeto:
👉 Acessar Circuito e Código no Tinkercad

🎥 Vídeo de Demonstração:
📽️ Assistir no Google Drive

🐙 Repositório no GitHub:
🔗 https://github.com/Guizinhn/Cp2-edge

👥 Integrantes
Guilherme Moura Badia – RM: 561568

Enzo Ramos – RM: 565832

João Verardo – RM: 563700

Lucca Fernandes – RM: 563961

Murilo Mendes – RM: 564193
