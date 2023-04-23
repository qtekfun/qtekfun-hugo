---
title: "Trucos para Windows 11"
slug: "trucos-w11"
date: 2023-04-23T20:41:03+02:00
draft: false
---

En este post iré añadiendo a lo largo del tiempo los trucos para Windows 11 más interesantes que me he ido encontrando;

## Notificación de uso de la Webcam

Windows nos puede notificar cuando algún programa está haciendo uso de nuestra webcam. Para habilitarlo, solo hay que seguir los siguientes pasos:

    1. Abre regedit. Para ello en el menú de inicio escribe `regedit`
    2. Una vez dentro navega a `Equipo\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OEM\Device\Capture`
    3. Cambia el valor de `NoPhysicalCamera` de 0 a 1.

Y listo, con eso nos notificará el uso de la webcam

## Actualizaciones desde la consola

Con estos pasos, vas a poder lanzar todas las actualizaciones del software de tu pc sin tener que ir una a una. Los pasos son:

    1. Abre Powershell
    2. Ejecuta `winget update`
    3. Acepta los terminos de uso cuando te pregunte con `Y`
    4. Ahora para ejecutar todas las actualizaciones lanzamos `winget update --all --include-unknown`

Y listo, con eso se nos actualizará todo.
