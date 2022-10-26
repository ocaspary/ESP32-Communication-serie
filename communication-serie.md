# Communication série

La communication série est utilisée pour faire communiquer un PC avec le microcontrôleur via le port série avec un câble USB-miniUSB. Il s’agit de liaisons RX TX de niveau logique à 3,3 V avec des données contenues dans des buffers FIFO. Cette communication est réalisée par un UART (_**Universal Asynchronous Receiver Transmitter**_) avec une trame bien définie. L’UART Transmetteur convertit les données parallèles provenant du PC en données série à l’UART Receveur qui les convertit à nouveau en données parallèles pour le microcontrôleur. Ceci est valable dans les deux sens. Deux fils sont suffisants pour transmettre les données entre deux UART. Leur vitesse de transmission doit être identique, par exemple 115200 bauds. Il n’y a pas de signal d’horloge pour synchroniser la transmission mais des bits start et stop peuvent être ajoutés.

L’ESP32 dispose de 3 UART sous les noms d’UART0, UART1 et UART2 qui fonctionnent comme des périphériques. Les broches de l’UART peuvent être mappées logiquement à n’importe quelle broche disponible de l’ESP32. Cependant, il existe aussi des accès directs qui améliorent légèrement les performances :

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Sur la plupart des cartes de développement ESP32, l’UART2 est présent avec les GPIO 16/17 comme Serial2.

Remarque : Pour la programmation, afin d’accéder aux références du langage Arduino, il est conseillé de créer un compte ou de se connecter au site officiel avec ses identifiants Gmail :

[https://www.arduino.cc/reference/en/](https://www.arduino.cc/reference/en/)
