---
title: "Quitar repos de apt"
date: 2022-04-19:21:46+01:00
draft: false
---
A veces añadirmos repos en las distros basadas en Debian (aka Ubuntu) y dejamos ahi los repos aunque no funcionen. ¿Por qué no borrar los que no vayan? Pues vamos al lio.

Para hacerlo hay dos pasos, borrar el repo en sí y después borrar la key.

<h2>Quitar el repo</h2>

Pongamos que hemos añadido el repo `sudo add-apt-repository -y ppa:nemh/systemback` de este modo. Para quitarlo temeos que quitarlo del *sources.list*. Con lo cual el comando sería algo como `sudo rm /etc/apt/sources.list.d/nemh-systemback-precise.list`

<h2>Quitar la GPG Key</h2>

Para esto usamos `apt-key list` (aunque ya esta deprecado). Ahí te saldrá algo como ...

{{< figure src="./apt-list.jpg" title="Output Apt List" >}}

De donde nos quedamos con los 8 ultimos caracteres de la key y escribimos:

`sudo apt-key del B312C643`

Y listo
