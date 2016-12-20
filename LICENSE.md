#include <Adafruit_NeoPixel.h>//引用头文件

#define PIN 6   /*定义了控制LED的引脚，6表示Microduino的D6引脚，可通过Hub转接出来，用户可以更改 */

#define PIN_NUM 1 //定义允许接的led灯的个数

Adafruit_NeoPixel strip = Adafruit_NeoPixel(PIN_NUM, PIN, NEO_GRB + NEO_KHZ800);

const int vibrationPin = 10;     // the number of the pushbutton pin

int vibrationState = 0;

void setup() {

Serial.begin(9600);

pinMode(vibrationPin, INPUT);

strip.begin();

strip.show();

}

void loop() {

vibrationState = digitalRead(vibrationPin);

if (vibrationState == HIGH) {

Serial.println("ONONONON");

light();

} else {

stop();

}

}

//stop

void stop() {

strip.setPixelColor(0, strip.Color(0, 0, 0));//灭

strip.show();  //LED显示

delay(1000);  //延迟1秒输出

}

//light

void light() {

strip.setPixelColor(0, strip.Color(255, 0, 0));//红光

strip.show();   //LED显示

delay(1000);  //延迟1秒输出

}
