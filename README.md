# Projeto-de-Circuitos-Eletrõnicos-IoT

Projeto de Circuitos Eletrônicos - IoT
Neste projeto, simulando uma estufa de hortaliças, deve ser desenvolvido no
simulador TinkerCad (https://www.tinkercad.com/) um circuito eletrônico envolvendo
um sensor de temperatura, uma buzina, um LED e um motor, controlados por meio
de um Arduino. O projeto deve seguir a seguinte funcionalidade:
(a) Fazer a leitura da temperatura;
(b) Fazer o acionamento de um motor de ventilador caso a temperatura seja igual
ou maior a 30 °C;
(c) Caso a temperatura ultrapasse os 50 °C, um LED vermelho e uma buzina
devem acionar avisando uma situação de emergência. 


segue o link do projeto https://www.tinkercad.com/things/jfeFMGfo3KD-projeto-eletronica-basica

codigo do projeto: 
// C++ code
//
#define motor 5
#define buzina 4
#define led 3
#define sensorTemp A0
int leitura;


void setup()
{
  pinMode(motor, OUTPUT);
  pinMode(buzina, OUTPUT);
  pinMode(led, OUTPUT);  
  Serial.begin(9600);
}

void loop()
{
  leitura = analogRead(sensorTemp);
  
  float tensao = leitura * (5000.0 / 1024.0);
  float temperaturaC = (tensao - 500.0) / 10.0;
  Serial.print("temperatura: ");
  Serial.println(temperaturaC);
  
  if (temperaturaC >= 30){
    
    digitalWrite(motor, HIGH);
    
  } else{
  
  	digitalWrite(motor, LOW);
  }
  
  if(temperaturaC >= 50){
    
    digitalWrite(led, HIGH);
    tone(buzina, 261); // C note
  	delay(200);
  	noTone(buzina);
  
  } else{
    
      digitalWrite(led, LOW);
  }
 
}
