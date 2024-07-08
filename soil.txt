int WET = 12;
int DRY = 2;
int motor = 13;
int Sensor = 0; // Soil Sensor input at Analog PIN A0
int value = 0;

void setup() {
  Serial.begin(9600);
  pinMode(WET, OUTPUT);
  pinMode(DRY, OUTPUT);
  pinMode(motor,OUTPUT);
  delay(2000);
}

void loop() {
  Serial.print("MOISTURE LEVEL : ");
  value = analogRead(Sensor);
  value = value / 10;
  Serial.println(value);
  delay(1000);
  if (value < 70)
  {
    Serial.println("Soil Reached Wet - Water Pump OFF");
    delay(2000);
    digitalWrite(motor, LOW);

    delay(1000);
  }
  else
  {
    Serial.println("Soil Reached Dry - Water Pump ON");
    digitalWrite(motor, HIGH);
  }
  delay(1000);
  digitalWrite(WET, LOW);
  digitalWrite(DRY, LOW);
}
