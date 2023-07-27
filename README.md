# SmartStreetLight
#define pir1 7
#define pir2 9
#define led1 5
#define led2 3
#define ldr A0

int pir1_status;
int pir2_status;
int ldr_val;

void setup() {
  // put your setup code here, to run once:
  pinMode(pir1, INPUT);
  pinMode(pir2, INPUT);
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
  ldr_val = analogRead(ldr);
  if(ldr_val<20){
    pir1_status = digitalRead(pir1);
    pir2_status = digitalRead(pir2);
    if(pir1_status==1){
      //pwm for led1 to glow at 100%
      analogWrite(led1, 255);
      Serial.println("led1 100");

    }
    else if(pir1_status==0){
      //pwm for led1 to glow at 5%
      analogWrite(led1, 15);
      Serial.println("led1 5%");
    }
    if(pir2_status==1){
      //pwm for led1 to glow at 100%
      analogWrite(led2, 255);
      Serial.println("led2 100");
    }
    else if(pir2_status==0){
      //pwm for led1 to glow at 5%
      analogWrite(led2, 15);
      Serial.println("led2 5%");
    }
    delay(200);
  }
  else{
    analogWrite(led1, 0);
    analogWrite(led2, 0);
    Serial.println(ldr_val);
  }
}
