# Fading-Led
Two fading led controlled by PIR motion sensor


#define led1 5
#define led2 3
const int PIRSensor =2;

int brightness1 = 0;
int brightness2 = 0;
int sensorValue = 0;

void setup() {
  Serial.begin(9600);
  pinMode (led1, OUTPUT);
  pinMode (led2, OUTPUT);
  pinMode (PIRSensor, INPUT);
 

}

void loop() {
  analogWrite(led1, brightness1);
  analogWrite(led2, brightness2);

  sensorValue = digitalRead(PIRSensor);
  Serial.println( PIRSensor );
  if ( sensorValue == HIGH ) {
    brightness1 = 255;

  } else {
    brightness1 -= 5;
    if ( brightness1 < 0 ) brightness1 = 0;
    delay( 100 );
  } 
  
  if ( sensorValue == HIGH ) {

    brightness2 = 255;
  }else {
    brightness2 -= 10;
    if ( brightness2 < 0) brightness2 = 0;
    delay( 100 );

  }

}
