> ## 1. PC에서 숫자 입력받으면 LED에 점멸하기    
LED 긴 다리 13 짧은 다리 그라운드

```c
void setup() {
  Serial.begin(9600);
  pinMode(13,OUTPUT); //LED
}
void loop() {
  String m;
  if(Serial.available()>0){
    String m = Serial.readString();
    if(m.indexOf('0')==0)digitalWrite(13,LOW);
    if(m.indexOf('1')==0)digitalWrite(13,HIGH);
  }
}
```  
* * *  
> ## 2. 아두이노와 프로세싱 통신 프로세싱 코딩  
```Processing
import processing.serial.*;
import processing.net.*; //와이파이 사용시 넣어야댐. 
Serial p;
void setup(){
  p = new Serial(this,"COM6", 9600);
  textSize(64); //글자 크기
}
void draw(){
}
void keyPressed(){
  background(0);
  p.write(key);
  text(key,10,60);
}
```  
스마트폰 = 클라이언트 , PC = 서버  
* * *  
> ## 3. 아두이노와 프로세싱 통신 간에 클라이언트 추가 버전(스마트폰)  
```Processing
import processing.serial.*;
import processing.net.*; //와이파이 통신
Serial p;
Client c; //스마트폰
Server s; //PC
void setup(){
  p = new Serial(this,"COM6", 9600);
  s = new Server(this, 12345); //서버 생성
  textSize(64);
}
void draw(){
 c = s.available(); //스마트폰에서 통신 받아오기
 if(c!=null){
   String m=c.readString();
   m = m.substring(m.length()-1);
   p.write(m);
}
void keyPressed(){
  background(0);
  p.write(key);
  text(key,10,60);
}
```  
![제목 없음](https://user-images.githubusercontent.com/50895677/68105338-814fb900-ff21-11e9-98a6-b3aec945c099.png)  
![캡처](https://user-images.githubusercontent.com/50895677/68105343-83b21300-ff21-11e9-92fd-dc10c258d6cc.PNG)
