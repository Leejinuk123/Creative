#include <Servo.h> // Include servo library
Servo sl, sr; // Declare left and right servos
void setup()
{   
  sl.attach(13);
  sr.attach(12);
  pinMode(10, INPUT); 
  pinMode(9, OUTPUT);
  pinMode(3, INPUT); 
  pinMode(2, OUTPUT);
  Serial.begin(9600);
}
int irDetect(int irLedPin, int irReceiverPin, long frequency)
{
  tone(irLedPin, frequency, 8);
  delay(1);
  int ir = digitalRead(irReceiverPin);
  delay(1);
  return ir;
}
void loop()
{
  int wl = irDetect(9, 10, 42000);
  Serial.print(wl);
  int wr = irDetect(2, 3, 42000);
  Serial.print("  ");
  Serial.println(wr);
  delay(100);

  if ((wl == 0) && (wr == 0)){

    backward(500); // Back up 1 second

    turnLeft(800); // Turn left about 120 degrees

  }

  else if (wl == 0){

    backward(500); // Back up 1 second

    turnRight(400); // Turn right about 60 degrees

  }

  else if (wr == 0){

    backward(500); // Back up 1 second

    turnLeft(400); // Turn left about 60 degrees

  }

  else{

    forward(20); // Forward 1/50 of a second

  }

}

void forward(int time){

  sl.write(1700);

  sr.write(1300);

  delay(time);

}

void turnLeft(int time){

  sl.write(1300);

  sr.write(1300);

  delay(time);

}

void turnRight(int time){

  sl.write(1700);

  sr.write(1700);

  delay(time);

}

void backward(int time) {

  sl.write(1300);

  sr.write(1700);

  delay(time);

}
