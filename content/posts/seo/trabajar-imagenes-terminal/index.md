---
title: "¿Cómo trabajar con Imágenes desde la Terminal de Ubuntu?"
date: 2022-10-14T15:11:41+02:00
draft: false
---

En este articulo te voy a enseñar cómo hacer un par de operaciones básicas con imágenes desde la terminal de ubuntu que son super fáciles e importantes.

Si estas leyendo este articulo o te ha picado la curiosidad, o puede que mantengas webs como esta mía, que usa hugo y donde los post están escritos en markdown.
Cómo es así, y todo lo manejo con un repositorio de git (incluso su deployment en producción), no quiero tener que pasar por windows para manejar las imagenes.
De hecho, concretamente trabajo con [Windows Subsystem Linux](https://learn.microsoft.com/en-us/windows/wsl/install) desde mi portatil con Windows 11.

## ¿Cómo convertir imágenes a webp?

Si quieres usar el formato de última hornada y que más se estila en internet, `webp` es la cosa más fácil que existe.
Lo primero es instalar la librería que nos hará la conversión, llamada `webp`. Para instalarla 
`sudo apt install webp`

Y lo siguiente ya es usarla. Suponiendo que tenemos una imágen llamada *image1.jpg*, para convertirla a webp lo haremos con:
`cwebp -q 60 image1.jpg -o image1.web`

Y listo, con eso lo tendremos.

> BONUS: con este snippet convertis todas las imágenes del directorio:
> ```
> for file in *.jpg; 
> do cwebp -q 60 `echo "$file" | cut -d'.' -f1`.jpg -o `echo "$file" | cut -d'.' -f1`.webp ; done
> ```

## ¿Cómo rotamos una imágen desde la terminal?

Lo de convertir las imágenes a webp llevo ya un tiempo haciendolo. Pero hoy, además, mi queridisimo iPhone ha decidido no rotar, y mis imágenes han salido rotadas.
Para solucionarlo, he encontrado la siguiente idea.

Primero hay que instalar la libreria imagemagick. Fácil con el siguiente comando:
`sudo apt install imagemagick-6.q16`

Y lo siguiente es usar su comando `convert`. Suponiendo que tenemos ahora *image1.webp* (funciona en casi cualquier formato):

```
convert image1.webp -rotate 90 image1-rotated.webp
```

donde el 90 son el número de grados que queremos girarla. Si esta en vertical, lo normal es que sea 90 o 270.

Y con estos trucos, os manejareis como pez en la terminal. ¡Espero os sea de ayuda!

