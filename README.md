# Laboratorio 5 - Microprocesadores
## FIT
### Universidad Católica del Uruguay

## Comunicación serial
### Objetivo general:
Implementar un sistema de comunicación serial de un solo hilo (sin señal de reloj), revisar conceptos
de manejo de tablas en memoria.
### Materiales:
    # 2x Placa de desarrollo ATmega328P Xplained Mini
    # 2x Módulo multifunción para Arduino
    # 2x Cable micro USB
    # Herramienta de desarrollo Microchip Studio
### Introducción
Un protocolo de transmisión serie transmite datos de un CPU a un periférico de 1 bit a la vez. En
protocolos de 1 solo cable (o 1 hilo), no hay una señal de reloj dedicada, los bits van uno tras otro
siguiendo alguna convención. La comunicación de 1 hilo necesita una referencia a tierra común
entre los dos dispositivos. Este tipo de puertos serie asíncronos siguen el estándar RS232 y se
implementan en microcontroladores mediante el bloque USART (Universal
Synchronous/Asynchronous Receiver/Transmitter).

## Implementación Tx
Observe el programa ejemplo; esta reserva espacio en memoria RAM para un buffer de 512 bytes.
La idea es completar este buffer con caracteres consecutivos aleatorios. Luego transmitirlos a la
placa receptora.

Implemente en la placa de desarrollo del curso, un sistema de comunicación serial con las siguientes
características: 
###     Parte 1
            Utilizar en lenguaje ensamblador el algoritmo que en vez de generar números
            consecutivos, genera números pseudo-aleatorios en un buffer de 512 bytes provisto
            (https://en.wikipedia.org/wiki/Xorshift (1)). Aunque puede utilizar otro algoritmo simple. La
            rutina debe guardar en el buffer 512 bytes “aleatorios”. Luego implementar una rutina que
            muestre la suma de los 512 números del buffer (Checksum) en el display de la placa. 

###     Parte 2
            Desarrollar un método de transmisión de datos entre dos placas con un solo cable
            (unidireccional, una placa transmite (maestro), otra recibe), utilizando el puerto USART.
            Transmitir los 512 bytes generados previamente y desplegar en el display de la placa
            receptora la suma de los 512 bytes recibidos como verificación. El mecanismo de
            transmisión se iniciará al pulsar un botón en la placa maestra. 

###     Parte 3
            (a) Agregar al final del mensaje a enviar los 4 bytes de la suma de los 512 números
            originalmente generados para verificar en el receptor la integridad del mensaje
            completo.
            (b) Pruebe transmitir a la máxima velocidad posible, datos entre una placa y otra. Investigue
            y calcule la velocidad máxima a la que se puede transmitir sin necesidad de hacer
            detección y corrección de errores, considerando las limitaciones del hardware y del
            protocolo USART utilizado

###     Parte 4 (Opcional)
            Implementar un bit de paridad en la transmisión de cada byte para detectar errores simples.
            Este paso es opcional. 

## Implementación Rx
###     Parte 1
            (a) Configurar el receptor para recibir 512 bytes de datos y almacenarlos en un buffer de 512
            bytes.
            (b) Mostrar la suma de los 512 números recibidos en el display de la placa para verificar la
            correcta recepción de los datos.

###     Parte 2
            Configurar el puerto USART para recibir los 512 bytes transmitidos por la placa transmisora y
            almacenarlos en un buffer de 512 bytes.

###     Parte 3
            Recibir los 4 bytes adicionales (Checksum) y comparar la suma de los 512 bytes recibidos con
            el Checksum recibido. Si coinciden, indicar que la transmisión fue correcta; de lo contrario,
            indicar un error de integridad.
###     Parte 4 Verificación opcional del bit de paridad
            Configurar el receptor para verificar el bit de paridad de cada byte recibido. Si se detecta un
            error de paridad, se debe indicar de alguna manera (por ejemplo, encendiendo un LED o
            mostrando un mensaje de error en el display).