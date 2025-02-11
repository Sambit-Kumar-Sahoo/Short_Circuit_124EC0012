# Short_Circuit_Street_Light_Task


## BIO
- [NAME : Sambit Kumar Sahoo]
- [ROLL : 124EC0012]
- [DEPARTMENT : Electronics and Communications Engineering]

## TASK
-[TinkerCAD Link](https://www.tinkercad.com/things/ipNdsOq9TZl-shortcircuittask124ec0012?sharecode=VumglJ95_jBoMZalGJHDlCMsYqRoLo2Bgrbbj9X5aVs)

-[CODE :]
#### **C++**
```md
```cpp
int redled=13;
int yellowled=12;
int greenled=8;
int button=2;
int greenint=2500;
int yellowint=1000;
int redint=2500;
unsigned long start=0;
bool buttonpress=false;
String light="green";

void setup()
{
  Serial.begin(9600);
  pinMode(redled, OUTPUT);
  pinMode(yellowled, OUTPUT);
  pinMode(greenled, OUTPUT);
  pinMode(button, INPUT_PULLUP);
}

void loop()
{
  unsigned long time=millis();
  
  if(digitalRead(button)==HIGH){
    buttonpress=true;
  }
  
  if(light=="green"){
    digitalWrite(greenled,HIGH);
    digitalWrite(yellowled,LOW);
    digitalWrite(redled,LOW);
    if(buttonpress==true){
      light="red";
      buttonpress=false;
    }
    else if(time - start >= greenint){
      start=time;
      light="yellow";
    }
  }
  else if(light=="yellow"){
    digitalWrite(yellowled,HIGH);
    digitalWrite(redled,LOW);
    digitalWrite(greenled,LOW);
    if(buttonpress==true){
      light="red";
      buttonpress=false;
    }
    else if(time - start >= yellowint){
      start=time;
      light="red";
    }
  }
  else if(light=="red"){
    digitalWrite(redled,HIGH);
    digitalWrite(greenled,LOW);
    digitalWrite(yellowled,LOW);
    if(time - start >= redint){
      start=time;
      light="green";
    }
  }
  
}
