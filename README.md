# Ultrasonic-Distance-Sensor---HC-SR04
Ultrasonic Sensor Ultrasonic Sensors measure the distance to the target by measuring the time between the emission and reception. An optical sensor has a transmitter and receiver, whereas an ultrasonic sensor uses a single ultrasonic element for both emission and reception.



     #define echoPin 2 // attach pin D2 Arduino to pin Echo of HC-SR04
     #define trigPin 3 //attach pin D3 Arduino to pin Trig of HC-SR04
     int led_green = 13;
     int led_yello = 12;
     int led_red = 11;
     // defines variables
     long duration; // variable for the duration of sound wave travel
     int distance; // variable for the distance measurement
     void setup() 
       {
         pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
         pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT
         Serial.begin(9600); // // Serial Communication is starting with 9600 of baudrate speed
         Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in Serial Monitor
         Serial.println("with Arduino UNO R3");
         pinMode(led_green, OUTPUT);
         pinMode(led_yello, OUTPUT);
         pinMode(led_red, OUTPUT);
     }
     
     void loop() 
     {
       // Clears the trigPin condition
       digitalWrite(trigPin, LOW);
       delayMicroseconds(2);
       // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
       digitalWrite(trigPin, HIGH);
       delayMicroseconds(10);
       digitalWrite(trigPin, LOW);
       // Reads the echoPin, returns the sound wave travel time in microseconds
       duration = pulseIn(echoPin, HIGH);
       // Calculating the distance
       distance = duration * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)
       // Displays the distance on the Serial Monitor
       Serial.print("Distance: ");
       Serial.print(distance);
        if(distance > 8)
        {
           digitalWrite(led_green, HIGH); // turn ON Arduino's LED
           digitalWrite(led_yello, LOW); // turn ON Arduino's LED
           digitalWrite(led_red, LOW); // turn ON Arduino's LED
        }
        else  if(distance < 8)
       {
           digitalWrite(led_green, LOW); // turn ON Arduino's LED
           digitalWrite(led_yello, HIGH); // turn ON Arduino's LED
           digitalWrite(led_red, LOW); // turn ON Arduino's LED
           if(distance < 4)
                  {
                     digitalWrite(led_green, LOW); // turn ON Arduino's LED
                     digitalWrite(led_yello,LOW ); // turn ON Arduino's LED
                     digitalWrite(led_red, HIGH); // turn ON Arduino's LED
                  }
      }
  
       Serial.println(" cm");
     }
