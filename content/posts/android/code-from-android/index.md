---
title: "¿Cómo programar desde tu teléfono Android?"
date: 2022-10-04T11:45:21Z
draft: false
---
Ya hace un tiempo que me ronda la cabeza poder publicar posts desde el movil en esta web, y como está en hugo, al final lo que hago es editar markdowns y subirlos a github como un commit de git.

Para esto, en resumen necesito dos elementos: una terminal donde poder manejar los commits y un edito de textos a la altura de la circunstancia. Y creo que he conseguido la combinación perfecta.

## Usar Git y Github en Android

Lo más facil es usar un git en entorno unix de toda la vida. Para ello, solo hay una app posible. Esa es [Termux](https://f-droid.org/en/packages/com.termux/). Esta app ejecuta, basandose en proot, un linux. Además, desde las ultimas versiones, podemos usar apt como gestor de paquetes, por lo que para instalar git:

ˋapt install gitˋ

Y como querremos clonar repos de Github, no está de más:

ˋapt install opensshˋ

## IDEs de programación en Android
En el apartado de IDEs, la verdad es que no hay mucha variedad pero recientemente he encontrado un par de alternativas que merecen la pena.

La primera de ellas es, en la que he escrito este post, *A-Code*. A-Code es un ide que tiene pestañas y explorador lateral para el manejo de ficheros. Además, es compatible con el storage de Termux, pieza fundamental en este setup.

{{< figure src="Acode.png" title="A-Code IDE" >}}

Otra de las posibilidades es *Squircle IDE*. Es un idea también muy parecido al anterior, pero lo he descartado por incompatibilidad de usar el storage de Termux.

{{< figure src="Squircle.png" title="Squircle IDE" >}}

La tercera de las opciones es intallar vim o neovim dentro de Termux, cosa que también he hecho por si las moscas. Para ello, basta con usar el siguiente comando:

ˋapt install neovimˋ

¡Y listo! esto es todo lo que os puedo contar hasta el momento. Si acaso lo probais, me gustaría leeros.
Y si sois usuarios de git, mi [lista de comandos y alias de git](https://qtekfun.com/posts/notes/git-basics/) os puede ser de utilidad.