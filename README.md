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
https://wokwi.com/projects/335701949911401042 :- Potentiometer with LED<br>

https://wokwi.com/projects/337604163653337682 :-DHT22(Humidity and Temperature sensor ESP32 <br>

https://wokwi.com/projects/337604296859189842 :-DHT22(Humidity and Temperature sensor ESP32 with LCD<br>


Hardware:<br><br>
DHT11<br>

    #include <Adafruit_Sensor.h><br>
    #include <DHT.h>;<br>
    #define DHTPIN 13     // what pin we're connected to<br>
    #define DHTTYPE DHT11   // DHT 22  (AM2302)<br>
    DHT dht(DHTPIN, DHTTYPE); //// Initialize DHT sensor for normal 16mhz Arduino<br>
    //Variables<br>
    int chk;<br>
    float hum;  //Stores humidity value<br>
    float temp; //Stores temperature value<br>
    void setup()<br>
    {<br>
      Serial.begin(9600);<br>
      dht.begin();<br>
    }<br>
    void loop()<br>
   {<br>
       delay(2000);<br>
       //Read data and store it to variables hum and temp<br>
       hum = dht.readHumidity();<br>
       temp= dht.readTemperature();<br>
       //Print temp and humidity values to serial monitor<br>
       Serial.print("Humidity: ");<br>
       Serial.print(hum);<br>
       Serial.print(" %, Temp: ");<br>
       Serial.print(temp);<br>
       Serial.println(" Celsius");<br>
       delay(1000); //Delay 2 sec.<br>
   }<br>

**WIFI**
// Learn about the ESP32 WiFi simulation in
// https://docs.wokwi.com/guides/esp32-wifi

#include <WiFi.h>
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C LCD = LiquidCrystal_I2C(0x27, 16, 2);

#define NTP_SERVER     "pool.ntp.org"
#define UTC_OFFSET     0
#define UTC_OFFSET_DST 0

void spinner() {
  static int8_t counter = 0;
  const char* glyphs = "\xa1\xa5\xdb";
  LCD.setCursor(15, 1);
  LCD.print(glyphs[counter++]);
  if (counter == strlen(glyphs)) {
    counter = 0;
  }
}

void printLocalTime() {
  struct tm timeinfo;
  if (!getLocalTime(&timeinfo)) {
    LCD.setCursor(0, 1);
    LCD.println("Connection Err");
    return;
  }

  LCD.setCursor(8,0);
  LCD.println(&timeinfo, "%H:%M:%S");

  LCD.setCursor(0, 1);
  LCD.println(&timeinfo, "%d/%m/%Y   %Z");
}

void setup() {
  Serial.begin(115200);

  LCD.init();
  LCD.backlight();
  LCD.setCursor(0, 0);
  LCD.print("Connecting to ");
  LCD.setCursor(0, 1);
  LCD.print("WiFi ");

  WiFi.begin("Wokwi-GUEST", "", 6);
  while (WiFi.status() != WL_CONNECTED) {
    delay(250);
    spinner();
  }

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  LCD.clear();
  LCD.setCursor(0, 0);
  LCD.println("Online");
  LCD.setCursor(0, 1);
  LCD.println("Updating time...");

  configTime(UTC_OFFSET, UTC_OFFSET_DST, NTP_SERVER);
}

void loop() {
  printLocalTime();
  delay(250);
}
