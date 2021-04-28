# -SIT210-Task3.3D-CloudFunction
int led = D5;

void setup() {

    pinMode(led, OUTPUT);
    digitalWrite(led, LOW);
    
    Particle.subscribe("Fake_event", myHandler, MY_DEVICES);

}
void myHandler(const char *event, const char *data) {
 
  // check if what we are recieving is the same as what the photon is publishing
  // and if they are the same strcmp will return 0 and blink the led
  if (strcmp(data, "wave") == 0)
  {
    digitalWrite(led, HIGH);
    delay(1000);
    digitalWrite(led, LOW);
    delay(1000);
    digitalWrite(led, HIGH);
    delay(1000);
    digitalWrite(led, LOW);
    delay(1000);
    digitalWrite(led, HIGH);
    delay(1000);
    digitalWrite(led, LOW);
    delay(1000);
  }
  if (strcmp(data, "pat") == 0)
  {
    digitalWrite(led, HIGH);
    delay(500);
    digitalWrite(led, LOW);
    delay(500);
    digitalWrite(led, HIGH);
    delay(500);
    digitalWrite(led, LOW);
    delay(500);
  }
}
void loop() {
    
    Particle.publish("Fake_event","wave");
    delay(10000);
    Particle.publish("Fake_event","pat");
    delay(10000);

}
