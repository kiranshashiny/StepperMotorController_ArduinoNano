#
 StepperMotorController_ArduinoNano

This is my experimental stepper motor with an intent to create a 3 dimensional CNC lathe.

Typically lathes have 2 planes, and a 3-D printer has 3 planes.

This attempt is to see how I can create a 2 or 3 axis moving motor with a threaded rod.

Parts Needed :

A4988 Stepper Motor driver.
Arduino Nano.
Stepper Motor Nema-17

Connections were as follows :


The Arduino

Pin D3  goes to STEP pin of the Driver
Pin D4  goes to DIRection pin of the Driver.
Reset and Sleep were connected to each other.

Vdd and GND of the Arduino was connected to A4988.

Vmot and GND were connected to 12V wall mounted power supply.

The pins of the Stepper motor were connected to 2B, 2A, 1B and 1A of the A4988. 


Code : Arduino IDE.
	
	// defines pins numbers
	const int stepPin = 3; 
	const int dirPin = 4; 
	 
	void setup() {
	  
	  // Sets the two pins as Outputs
	  pinMode(stepPin,OUTPUT); 
	  pinMode(dirPin,OUTPUT);
	}
	#define ROTATIONS 12800
	void loop() {
	  digitalWrite(dirPin,HIGH); // Enables the motor to move in a particular direction
	  // Makes 200 pulses for making one full cycle rotation
	  for(int x = 0; x < ROTATIONS; x++) {
	    digitalWrite(stepPin,HIGH); 
	    delayMicroseconds(500); 
	    digitalWrite(stepPin,LOW); 
	    delayMicroseconds(500); 
	  }
	  delay(1000); // One second delay
	  
	  digitalWrite(dirPin,LOW); //Changes the rotations direction
	  
	  // Makes 400 pulses for making two full cycle rotation
	  for(int x = 0; x < ROTATIONS ; x++) {
	    digitalWrite(stepPin,HIGH);
	    delayMicroseconds(500);
	    digitalWrite(stepPin,LOW);
	    delayMicroseconds(500);
	    
	  }
	  delay(1000);
	}


References :

https://www.youtube.com/watch?v=_5H7ibWQgXo
