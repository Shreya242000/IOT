# IOT

https://wokwi.com/projects/333715360946586195
<br>
https://wokwi.com/projects/333715360946586195 :- Traffic led
<br>
https://wokwi.com/projects/333801426044060243  :-RGB LED
<br>
https://wokwi.com/projects/333805190238962259  :-RGB LED2
<br>
https://wokwi.com/projects/334977593624232530 : servo motar <br>
<br>
https://wokwi.com/projects/334977593624232530  :-    servo motar using for loop<br>
<br>
https://wokwi.com/projects/334977602579071570 :-Servo motor with slide potentiometer<br>
<br>
https://wokwi.com/projects/334977602579071570 :-Servo motor with slide potentiometer<br>
<br>
https://wokwi.com/projects/335702826545054292 :-Servo meter with pushbutton
<br>
https://wokwi.com/projects/335065707348755026 :-BUZZER<br>
<br>
https://wokwi.com/projects/335065844754154067 :-BUZZER with Push button<br>
<br>
https://wokwi.com/projects/335131064102027860 :-Ultrasonic<br>
<br>
https://wokwi.com/projects/335070139005272658 :-Ultrasonic sensor with buzzer<br>
<br>
https://wokwi.com/projects/335075055329346132 :-varring with intensity of Ultrasonic with buzzer<br>
<br>
https://wokwi.com/projects/335611619397599827 :-varring with distance using led<br>
<br>
https://wokwi.com/projects/335615459073196626 :-2 Ultrasonic sensor buzzer and led
<br>
https://wokwi.com/projects/335701949911401042 :- Potentiometer with LED


#Ultrasonic sensor
const int trigPin = D6;
const int echoPin = D5;

//define sound velocity in cm/uS
#define SOUND_VELOCITY 0.034
#define CM_TO_INCH 0.393701

long duration;
float distanceCm;
float distanceInch;

void setup() {
  Serial.begin(9600); // Starts the serial communication
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
  pinMode(echoPin, INPUT); // Sets the echoPin as an Input
}

void loop() {
  // Clears the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin on HIGH state for 10 micro seconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  
  // Calculate the distance
  distanceCm = duration * SOUND_VELOCITY/2;
  
  // Convert to inches
  distanceInch = distanceCm * 0.393701;
  
  // Prints the distance on the Serial Monitor
  Serial.print("Distance (cm): ");
  Serial.println(distanceCm);
  Serial.print("Distance (inch): ");
  Serial.println(distanceInch);
  
  delay(1000);
}

