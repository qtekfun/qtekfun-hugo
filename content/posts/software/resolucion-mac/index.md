---
title: "¿Cómo ver la resolución de pantalla en un mac?"
date: 2022-02-04T17:48:25+01:00
draft: false
---
Si tienes un Mac y quieres ver la resolución real de la pantalla que estás utilizando lo único que debes hacer es:

Pasos para ver la resolución de pantalla en Mac

1. Abrir terminal
    Podemos buscar «terminal» en el Launchpad o abrir Spotloght con CMD + Espacio y buscar Terminal
2. Introducir el siguiente comando

    `system_profiler SPDisplaysDataType | grep Resolution`

{{< figure src="./resolucion-pantalla-mac.png" title="Resolución Pantalla Mac" >}}

Y listo, el resultado debe de ser como el de la foto anterior. También funciona con un monitor externo conectado.
