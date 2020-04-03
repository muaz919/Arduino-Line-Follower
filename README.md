# Arduino-Line-Follower
example for the line follower using 4 infrared sensor module:

~~~c++
/*------ Arduino Line Follower Code----- */
/*-------definning Inputs------*/

//Sensor Connection
const int ProxSensor0 = A0;
const int ProxSensor1 = A1;
const int ProxSensor2 = A2;
const int ProxSensor3 = A3; 

int inputVal0 = 0;
int inputVal1 = 0;
int inputVal2 = 0;
int inputVal3 = 0;

#define Right_Dir 12
#define Right_Speed 10
#define Left_Dir 13
#define Left_Speed 11

int nom_Speed = 255;               //Max 255
int nom_HTurn = 200;               //Turn right and left
int nom_LTurn = 100;               //Turn lower right and lower left
int nom_Delay = 10;                //Delay before turn


void setup()
{
 pinMode(ProxSensor0, INPUT);
 pinMode(ProxSensor1, INPUT);
 pinMode(ProxSensor2, INPUT);
 pinMode(ProxSensor3, INPUT);

 pinMode(Right_Dir, OUTPUT);
 pinMode(Left_Dir, OUTPUT);

 Serial.begin(9600);
  
}

void loop(){
  
  inputVaL0 = analogRead(ProxSensor0);
  inputVal1 = analogRead(ProxySensor1);
  inputVal2 = analogRead(ProxySensor2);
  inputVal3 = analogRead(ProxySensor3);
  

  //going forward
  if(inputVal0 > 500 && inputVal1 > 500 && inputVal3 > 500 && inputVal4 > 500)      
  {
   
    digitalWrite(Left_Dir, LOW);
    digitalWrite(Right_Dir, HIGH);
    analogWrite(Left_Speed, nom_Speed);
    analogWrite(Right_Speed, nom_Speed);
    
  }

  //turn left
  if(inputVal0 > 500 && inputVal1 > 500  && inputVal2 < 500 && inputVal3 < 500)      
  {
    
    digitalWrite(Right_Dir, LOW);
    digitalWrite(Left_Dir, HIGH);
    analogWrite(Right_Speed, nom_Speed);
    analogWrite(Left_Speed, nom_Turn);

    delay(nom_Delay)
    
  }

  //turn right
  if(inputVal0 < 500 && inputVal1 < 500  && inputVal2 > 500 && inputVal3 > 500)
  {
    
    digitalWrite(Right_Dir, LOW);
    digitalWrite(Left_Dir, HIGH);
    analogWrite(Right_Speed, nom_Turn);
    analogWrite(Left_Speed, nom_Speed);

    delay(nom_Delay)

  }

  //stop
  else(inputVal0 < 500 && inputVal1 < 500  && inputVal2 < 500 && inputVal3 < 500)      
  {
    
    digitalWrite(Right_Dir, LOW);
    digitalWrite(Left_Dir, HIGH);
    analogWrite(Right_Speed, 0);
    analogWrite(Left_Speed, 0);

  }
}
~~~
