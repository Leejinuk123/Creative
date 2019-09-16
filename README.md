1. 시나리오 및 작성 소감.
조도 센서가 실제로 사물인터넷이 발전된 현대 사회에서 많이 사용되고있습니다. 더 많은 실생활에 적용시키기 위해서 아두이노와 프로세싱을 다루는 방법을 
배우는 수업에서 기초를 다지기 위해 조도 센서를 활용하는 예제 활동 수업을 진행했습니다. 이 수업을 해보면서 직접 아두이노와 프로세싱 코딩을 해보면서
수업이 더 입체적이고 자발적으로 무언가 한다는 느낌을 받았습니다. 그래서 더 재미있었고 더 배우고싶은 학구열이 자극되었습니다. 교수님의 창의융합 수업이
너무 재밌습니다. 감사합니다~


2. 아두이노 코드
void setup() {  
  Serial.begin(9600);
}
void loop() {
  int a = analogRead(A0);
  Serial.println(a); //a=a+1;
  delay(500);
}


3. 프로세싱 코드

import processing.serial.*;
Serial p;
void setup(){
  size(300,300);
  p=new Serial(this,"COM6",9600);
}
void draw(){
  if(p.available()>0){
    String m=p.readString();
    int a = int(m.trim());
    println(a);
    if(a>250) fill(0,255,0);
    else      fill(255,0,0);
    ellipse(150,150, 200,200);
  }
}
