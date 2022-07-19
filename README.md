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


#Ultrasonic sensor<br>
const int trigPin = D6;<br>
const int echoPin = D5;<br>

//define sound velocity in cm/uS<br>
#define SOUND_VELOCITY 0.034<br>
#define CM_TO_INCH 0.393701<br>

long duration;<br>
float distanceCm;<br>
float distanceInch;<br>

void setup() {<br>
  Serial.begin(9600); // Starts the serial communication<br>
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output<br<br>>
  pinMode(echoPin, INPUT); // Sets the echoPin as an Input<br>
}

void loop() {<br>
  // Clears the trigPin<br>
  digitalWrite(trigPin, LOW);<br>
  delayMicroseconds(2);<br>
  // Sets the trigPin on HIGH state for 10 micro seconds<br>
  digitalWrite(trigPin, HIGH);<br>
  delayMicroseconds(10);<br>
  digitalWrite(trigPin, LOW);<br>
  
  // Reads the echoPin, returns the sound wave travel time in microseconds<br>
  duration = pulseIn(echoPin, HIGH);<br>
  
  // Calculate the distance<br>
  distanceCm = duration * SOUND_VELOCITY/2;<br>
  
  // Convert to inches<br>
  distanceInch = distanceCm * 0.393701;<br>
  
  // Prints the distance on the Serial Monitor<br>
  Serial.print("Distance (cm): ");<br>
  Serial.println(distanceCm);<br>
  Serial.print("Distance (inch): ");<br>
  Serial.println(distanceInch);<br>
  
  delay(1000);<br>
}<br>

