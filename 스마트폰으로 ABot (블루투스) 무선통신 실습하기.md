> ## 1. 실습 유튜브 :  
[스마트폰으로 ABot 움직이기 유튜브 링크](https://youtu.be/kyGNYXmMNtE)
* * *
> ## 2. 실습에 대한 자세한 설명(카페 참고, 개별)  
> ### 2-1. 아두이노 코드 :  
```c
#include <Servo.h>
Servo sr, sl;
void setup() {
  Serial.begin(9600);
  sr.attach(13); sl.attach(12);
}

void loop() {
  if (Serial.available()) {
    char b[2];  //pitch b[0], roll b[1]
    int p, r;
    Serial.readBytes(b, 2);
    p = b[0] * 3; // 피치값 -90~0~90, 전 후진  // 1500-270 ~ 1500+270
    r = b[1];        // 롤 값 -90~0~90, 좌 우회전  // 1500-90 ~ 1500+90
    sr.write(1500 + p - r);
    sl.write(1500 - p - r);
    Serial.write('1');
  }
}
```  
> ### 2-2. 앱인벤터 블럭코딩 :  

* * *
> ## 3. 실습 소감(개별)
