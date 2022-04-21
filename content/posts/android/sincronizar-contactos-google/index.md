---
title: Sincronizar contactos con Google sin GMS
author: afi6cu
date: 2020-11-24T11:11:44+00:00
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
categories:
  - Android

---
Si estas leyendo esto, o bien tienes un teléfono Huawei con App Gallery, es decir, sin Google Mobile Services, o bien eres un entusiasta de la privacidad y llevas Lineage OS o similar. Sea como fuere, existe una app llamada DAVx5 que bien configurada te permite sincronizar contactos y calendarios en segundo plano. Configurarla sabiendo es facil, y es lo que te vengo a explicar.

## Descarga DAVx5

Puedes descargarlo de multiples sitios: Play Store, F-Droid, Huawei AppGallery, Samsung Galaxy Apps, &#8230; Sea como fuere, la gente de DAVx5 tiene todas las opciones en su web:

<a href="https://www.davx5.com/download" target="_blank" rel="noreferrer noopener">Descargar DAVx5</a>.

## Configurar DAVx5 con Google

Hacerlo es sencillo. Deberéis iniciar sesión con la opción «Acceder con URL y nombre de usuario». Si tenéis OTP o Google Autenthicator, generad una contraseña de aplicación <a href="https://myaccount.google.com/apppasswords?gar=1" target="_blank" rel="noreferrer noopener">aquí</a>.

Después hay que rellenar la url base con:

<pre class="wp-block-code"><code>https:&#47;&#47;www.google.com/calendar/dav/xxx@egmail.com/events</code></pre>

donde el **xxx** es el nombre de vuestro usuario en gmail. Después de eso conectáis, y a correr.