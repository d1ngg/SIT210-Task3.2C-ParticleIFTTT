    int photoresistor = A0;
    int led = A5;
    bool sunIsOn = false;

    void setup() {

        pinMode(led, OUTPUT);
        pinMode(photoresistor, INPUT);
    }

    void loop() {
        digitalWrite(led, HIGH);
        int light = analogRead(photoresistor);
        Particle.publish("light", String(light));

        if (light > 10 && !SunIsON){
            SunIsON = true;
            Particle.publish("SunIsON", "true");
        }else if(light < 10 && SunIsON){
            SunIsON = false;
            Particle.publish("SunIsON", "false");
        }
        delay(5000);
        digitalWrite(led, LOW);
        delay(5000);
    }
