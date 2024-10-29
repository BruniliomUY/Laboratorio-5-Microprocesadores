# Laboratorio 5 - Microprocesadores
## FIT
### Universidad Católica del Uruguay

## Comunicación serial
### Objetivo general:
Implementar un sistema de comunicación serial de un solo hilo (sin señal de reloj), revisar conceptos
de manejo de tablas en memoria.
### Materiales:
 2x Placa de desarrollo ATmega328P Xplained Mini
 2x Módulo multifunción para Arduino
 2x Cable micro USB
 Herramienta de desarrollo Microchip Studio
### Introducción
Un protocolo de transmisión serie transmite datos de un CPU a un periférico de 1 bit a la vez. En
protocolos de 1 solo cable (o 1 hilo), no hay una señal de reloj dedicada, los bits van uno tras otro
siguiendo alguna convención. La comunicación de 1 hilo necesita una referencia a tierra común
entre los dos dispositivos. Este tipo de puertos serie asíncronos siguen el estándar RS232 y se
implementan en microcontroladores mediante el bloque USART (Universal
Synchronous/Asynchronous Receiver/Transmitter).
Implementación Tx
Observe el programa ejemplo; esta reserva espacio en memoria RAM para un buffer de 512 bytes.
La idea es completar este buffer con caracteres consecutivos aleatorios. Luego transmitirlos a la
placa receptora.

Implemente en la placa de desarrollo del curso, un sistema de comunicación serial con las siguientes
características: 


## Desafío(s)

Este ejemplo es el mismo que hemos utilizado hasta ahora, pero el código tiene modificaciones resultantes de aplicar los principio y patrones anteriores.

La clases que implementan IPrinter, como ConsolePrinter, dependen de la clase Recipe: un mensaje string GetTextToPrint() es enviado a una instancia de Recipe en el método void PrintRecipe(Recipe).

➡️ **Apliquen el principio de inversión de dependencia para que la clase ConsolePrinter no dependa de la clase Recipe.**
