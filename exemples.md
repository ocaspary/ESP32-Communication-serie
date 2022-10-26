# Exemples

_**Exemple d’utilisation possible de l’UART2, fichier Serial2\_example.ino**_&#x20;

```arduino
/* There are three serial ports on the ESP known as U0UXD, U1UXD and U2UXD.
 * 
 * U0UXD is used to communicate with the ESP32 for programming and during reset/boot.
 * U1UXD is unused and can be used for your projects. Some boards use this port for SPI Flash access though
 * U2UXD is unused and can be used for your projects.
*/
 
#define RXD2 16
#define TXD2 17
 
void setup() {
  // Note the format for setting a serial port is as follows: Serial2.begin(baud-rate, protocol, RX pin, TX pin);
  Serial.begin(115200);
  //Serial1.begin(9600, SERIAL_8N1, RXD2, TXD2);
  Serial2.begin(9600, SERIAL_8N1, RXD2, TXD2);
  Serial.println("Serial Txd is on pin: "+String(TX));
  Serial.println("Serial Rxd is on pin: "+String(RX));
}
 
void loop() { //Choose Serial1 or Serial2 as required
  while (Serial2.available()) {
    Serial.print(char(Serial2.read()));
  }
}

```

Source de l’exemple : [https://circuits4you.com/2018/12/31/esp32-hardware-serial2-example/](https://circuits4you.com/2018/12/31/esp32-hardware-serial2-example/)

Description des trames :  [https://www.youtube.com/watch?v=eUPAoP7xC7A](https://www.youtube.com/watch?v=eUPAoP7xC7A)

_**Exemple du fichier SerialBaudrate.ino** (affiche la vitesse de transmission dans le moniteur Série) **:**_

```arduino
void setup() { 
Serial.begin(115200);  
} 
void loop() { 
  int baud = Serial.baudRate(); 
  Serial.print("Current Baud:"); 
  Serial.println(baud); 
  delay(1000); 
}

```

Maintenant, un exemple intéressant où chaque caractère de la liaison série est lu. Les caractères Y et N permettent soit d’allumer la LED du microcontrôleur, soit de l’éteindre. Aussi, une suite de caractères telle que "YNYNYN" fera clignoter la LED trois fois. Les caractères sont saisis dans le moniteur série. Comprendre le rôle des fonctions associées à Serial : Serial.begin(), Serial.available(), Serial.Print(), Serial.read().

_**Fichier Serial\_Turn\_LED.ino :**_

```arduino
int incomingByte = 0;   // for incoming serial data
const int LED_BUILTIN = 2;

void setup() {
        Serial.begin(9600);     // opens serial port, sets data rate to 9600 bps
        pinMode(LED_BUILTIN,OUTPUT); 
        Serial.println("Type characters to send");
}

void loop() {

        // send data only when you receive data:
        if (Serial.available() > 0) {

                Serial.print("Number of characters to read: ");
                Serial.println(Serial.available());
                
                // read the incoming byte:
                incomingByte = Serial.read();

                // say what you got:
                Serial.print("I received: ");
                Serial.println(char(incomingByte));
                
                if(incomingByte=='Y'){  	// Character Y for Yes and turn on the LED
                  digitalWrite(LED_BUILTIN,HIGH); //LED on
                  Serial.println("ON");                 
                }
                
                if(incomingByte== 'N'){  	// Character N for No and turn off the LED
                  digitalWrite(LED_BUILTIN,LOW); //LED off
                  Serial.println("OFF");                 
                }
        }
        delay(1000);
}
```
