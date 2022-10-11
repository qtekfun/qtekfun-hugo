---
title: "¿Cómo seleccionar cualquier versión de Windows 11 cuando lo instalamos?"
date: 2022-10-11T07:58:04Z
draft: false
---

Detrás de este titulo hay una cuestión muy curiosa que me ha costado bastante tiempo solucionar y aprender.
Por ello os lo quiero explicar en este post.

## ¿Por qué no puedo seleccionar cualquier versión de Windows 11?

*Me refiero a Windows 11 pero aplica también a Windows 10.*

Antaño, cuando ibamos a instalar Windows, nos salia un selector donde elegíamos la versión a instalar.
Esto sigue siendo así, pero, hay algo que hace que no salga ese selector. Y es la licencia de Windows embebida en la BIOS.
Los PCs nuevos traen directamente la licencia de Windows en la BIOS, por lo que el instalador, lee la licencia que tienes y directamente selecciona esa versión.
Pero si eres una persona como yo, que te gusta hacer las cosas de un modo concreto, es decir, odio instalar Windows 11 Home para luego hacer el upgrade a Pro si puedo instalar Windows 11 Pro directamente.
Y sí, hay forma, y os la quiero contar.

## ¿Cómo ignorar la licencia de Windows en la BIOS?

Para ello, los pasos son:

1. Crear el instalador de Windows 11 como más os guste. Yo os recomendaría [Rufus](https://rufus.ie/es/) que además en sus últimas versiones tiene cosas muy chulas como saltarte las preguntas de inicio, las limitaciones de Windows 11 como el TPM 2.0 o la necesidad de cuenta online.

2. Crear un fichero llamado `ei.cfg` con el siguiente contenido:
```
[Channel]
_Default
[VL]
0
```

3. Guardar ese fichero en el escritorio.

4. Mover ese fichero al usb instalador dentro del path: `sources`

Y listo. Con eso, el instalador te preguntará por la version de Windows que quieres instalar.
