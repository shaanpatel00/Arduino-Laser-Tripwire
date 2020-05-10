# Arduino-Laser-Tripwire
An arduino code and build instructions for a laser tripwire

# Code
# Initialization
The first thing I needed to do was set the pin numbers to the designated part.
I set an led to pin 13, the enA from the L298N motor drive to 11, in1 to 7, in2 to 8, the photoresistor to pin A0, and the initial value for x to 0.
# Setup
In the setup, I set the baud rate to 9600, and the pinmodes for each component.

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
  pinMode(enA, OUTPUT);
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(lightReader, INPUT);
  delay(5000);
}

void loop() {
  x = analogRead(lightReader); // this is for serial monitoring purpose
  Serial.print("Reading: "); 
  Serial.println(x);
  
  if (x < 790) 
    {
      digitalWrite(ledPin, HIGH);
      analogWrite(enA, 255);
      digitalWrite(in1, HIGH);
	    digitalWrite(in2, LOW);
    }
  /*else 
    {
      digitalWrite(ledPin, LOW);
      analogWrite(enA, 255);
      digitalWrite(in1, LOW);
	    digitalWrite(in2, LOW);
    }*/
}
