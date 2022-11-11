---
title: "Sincronizar Ipod Con Ubuntu 22.10"
date: 2022-11-11T19:55:37+01:00
draft: false
---

Si eres fanático como yo de los iPods o si has recuperado uno del cajón, quieres meterle música como es debido. ¡Normal! Y como llevo 3 horas intentandolo y apenas hay info, te voy a contar cómo lo he conseguido yo, para que no mueras en el intento.

![Couldn't find the iPod firewire ID](images/couldnt-find-the-ipod-firewire-id.webp)

## Primer paso: resolver el mensaje "Couldn't find the iPod firewire ID"
Si te pasa esto, tranquilo. Solucionarlo es un poco "tricky" pero es fácil.

### Causa de "Couldn't find the iPod firewire ID"
El problema es que alguno de los programas que te piden que selecciones el modelo, te ha jorobado el fichero `SysInfo` localizado en `<punto de montaje del ipod>/iPod_Control/Device`. En concreto lo que te falta es la linea:
`FirewireGuid: 0xFFFFFFFFFFFFFFFF` donde las Fs son el numero de serie de tu dispositivo.

### Solución de "Couldn't find the iPod firewire ID"
Para arreglarlo, fácil, averiguamos el numero de serie y después escribimos esa linea en el fichero.

#### Obtener el número de serie del iPod
En muchos sitios te dice que uses el comando `sudo lsusb -v | grep -i iSerial` y uno de los que salgan, es tu número de serie, pero ¿Cuál? Por ello, mejor usar el `sudo lsusb -v` y vas buscando la linea que ponga "Bus 001 Device XXX: ID XXXX:XXXX Apple, Inc. iPod Classic" donde las X tomaran valores distintos. Unas pocas lineas más abajo tinees el iSerial. te quedas con los numeros que empiezan por 00 y son 16 dígitos normalmente.

Despues abrimos el SysInfo con el editor que prefieras: `vim <punto de montaje del ipod>/iPod_Control/Device/SysInfo` y añadimos la linea `FirewireGuid: 0xFFFFFFFFFFFFFFFF`. Guardamos y listo. Con eso ya podremos copiarle música al iPod.

En concreto, esto me ha pasado con un iPod Classic de 6ª gen y con Ubuntu 22.10. Al final he conseguido pasarle música con clementine.

Espero que os haya servido. Si me ocurren más cosas, edito el post. ¡Have fun!