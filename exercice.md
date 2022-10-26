# Exercice

**Exercice : contrôle de la LED bleue d’un ESP32 par un autre ESP32 via l’UART2**

A partir des exemples précédents et vus en cours, faites communiquer deux ESP32 via une liaison série. Vous utiliserez l’UART2 avec Serial2 pour établir cette liaison série. Les taux de transmission (en bauds) doivent être identiques.&#x20;

Description : quand vous touchez un fil de l’ESP32 (voir l’exemple Touch\_sensitive\_LED.ino), celui-ci envoie un caractère Y pour Yes, sinon un caractère N pour No à un deuxième ESP32. Le second ESP32 lit le caractère via l’UART2 et allume la led bleue si celui-ci est Y. Vérifier son fonctionnement avec le moniteur série.

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption><p><em>Schéma de la communication série (avec Touch sensitive)</em></p></figcaption></figure>

Montage : Relier les deux masses GND des deux ESP. Relier ensuite TX2 - RX2 d’un ESP à RX2 - TX2 de l’autre ESP. Autrement dit, croisez les 2 fils. Voir le montage final ci-dessous :

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Vous aurez besoin de téléverser vos programmes sur chaque ESP32 séparément, à partir du même port COM. Les deux ESP32 doivent être alimentés pour que les programmes fonctionnent.

Fonctions utilisées pour l’UART2 :&#x20;

Serial2.begin() , Serial2.available() , Serial2.write() , Serial2.read().

Pour rappel, Serial.begin() concerne l’UART0 et permet la communication série avec le PC, notamment l’affichage avec le moniteur série et le traceur de l’IDE Arduino.
