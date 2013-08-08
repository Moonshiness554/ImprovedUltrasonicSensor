ImprovedUltrasonicSensor
========================

long cm;
long duration;
long distance;

int echoPin =2;
int triggerPin =3;

void setup()
{
  pinMode(echoPin,INPUT);
  pinMode(triggerPin,OUTPUT);
  Serial.begin(9600);
}
void loop()
{
  distance = getDistance();
   Serial.println(distance);
delay(10);
}

long getDistance()
{
  digitalWrite(triggerPin,LOW);
  delayMicroseconds(2);
  digitalWrite(triggerPin,HIGH);
  delayMicroseconds(10);
    digitalWrite(triggerPin,LOW);

  duration = pulseIn(echoPin,HIGH);
  
  cm = duration/57;
  if (cm< 1000)
  {
     return cm;
  }
    else
{
  return -1;
}
}
