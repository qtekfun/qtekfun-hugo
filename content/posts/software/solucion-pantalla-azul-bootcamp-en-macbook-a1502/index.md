---
title: SOLUCIÓN Imposible instalar BOOTCAMP en MacBook A1502
author: afi6cu
date: 2020-12-02T08:22:33+00:00 
ampforwp-amp-on-off:
  - default
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
uag_style_timestamp-css:
  - 1614672053
categories:
  - Software

---
Si tienes un Apple MacBook A1502 de 2014 o 2015 muy posiblemente comprases la versión de 128Gb o la de 256Gb. Puedes ampliar por poco dinero a 512Gb o a 1Tb con un simple adaptador y un disco NVMe PCI Express. Pero hay varias cosas que me han costado años descubrir, desde cómo configurarlo adecuadamente hasta cómo solucionar la Pantalla Azul en Bootcamp.

## ¿Cómo cambiar el disco en un MacBook A1502?

Esta es la parte fácil. Con abrir la tapa inferior y quitar el tornillo del SSD ya está toda la parte HW casi hecha. Lo siguiente es **montar el adaptador**, **montar el nuevo SSD,** e **Instalar el sistema operativo.**

NOTA: Recuerda hacer un disco de arranque de MacOS antes de quitar el disco.

Respecto a qué disco elegir, te dejo a continuación un adaptador como el que tengo yo y un SSD como el mio:

* <a href="https://amzn.to/3lsiUNS" rel="noreferrer noopener nofollow">Adaptador</a>
* <a href="https://amzn.to/3lsiUNS" rel="noreferrer noopener nofollow">SSD</a>

## Ajustes necesarios en MacOS para el SSD

En este caso, lo que necesitamos es un solo comando que habilite en MacOS el TRIM que hará que el SSD te dure mucho más y que vaya mucho más rápido y consiga mayor velocidad de lectura y escritura.

### ¿Cómo activar TRIM en MacOS?

Para ello abre una terminal y escribe:

`sudo trimforce enable`

Después de esto, te pedirá la contraseña, te preguntará si queremos habilitarlo a lo que deberemos pulsar «Y» y después se nos reiniciará el PC. Con eso en el SO de Apple estamos listos.

{{< figure src="activarTrimMacOS.png" title="Activar Trim MacOS" >}}

### Solucionar Pantalla Azul en Bootcamp en MacBoook A1502 (2014 - 2015)

Y si intentas instalar Bootcamp no lo vas a lograr de serie. Al cambiar el disco SSD algo se rompe por dentro. Llega un momento en el que no salta una pantalla azul, se reinicia el Mac y despues nos suelta un mensaje de que <strong>«no se puede continuar con la instalación»</strong>. Pero con un pequeño truco estando ahí, podéis hacerlo. Solo tenéis que seguir los pasos:

* Cuando tengas el mensaje de error en pantalla, pulsa <strong>Shift + F10</strong>
* En la ventana del CMD de Windows que se abrirá, teclea <strong>regedit</strong> y pulsa Intro para abrir el Registro de Windows.


{{< figure src="RegistroWindows.jpg" title="Registro Windows" >}}


* En el árbol de carpetas de la izquierda, busca la ruta `«HKEY_LOCAL_MACHINE\SYSTEM\Setup\Status\ChildCompletion»`
* En la ruta anterior, busca <strong>«setup.exe» </strong>en la parte de la derecha y haz doble click en él.
* Edita su valor. Pon un 3. (normalmente tiene valor 1).
* Reinicia el equipo y disfruta de Bootcamp.

Con esos pasos, tienes listo Bootcamp y has concluido con el cambio del SSD en tu Mac.