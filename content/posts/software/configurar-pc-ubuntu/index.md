---
title: ¿Cómo configuro mi PC con Ubuntu?
author: afi6cu
date: -001-11-30T00:00:00+00:00
draft: false
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
stick-header-meta:
  - default
categories:
  - Uncategorized

---
En general cuando usas un PC con alguna distribución de Linux como puede ser ubuntu, los inicios siempre son instalar miles de cosas. Para abreviar, y mas que nada, para recordarlo, he pensado apuntarmelo en este post y que termine de ayudar a todos los que vengaís, así que vamos al lio.

## Instalar aplicaciones más utiles en Ubuntu 2021 {#h-instalar-aplicaciones-m-s-utiles-en-ubuntu-2021}

Lo primero de todo, actualizar lo que falte con:

<pre class="wp-block-code"><code>sudo apt-get update && sudo apt-get upgrade -y</code></pre>

Lo siguiente que debemos hacer es instalar las aplicaciones más útiles que no vienen por defecto en Ubuntu. Entre ellas:

<pre class="wp-block-code"><code>sudo apt-get install keepassxc nextcloud-desktop terminator vim-gtk3 git android-sdk-platform-tools telegram-desktop ubuntu-restricted-extras tlp tlp-rdw vlc rar unrar p7zip-full p7zip-rar ttf-mscorefonts-installer pinta && sudo fc-cache -f -v</code></pre>

Y como yo siempre uso portatil por eso instalamos tlp. Después de instalarlo, lo arrancamos con:

<pre class="wp-block-code"><code>sudo tlp start</code></pre>

Y para que se inície al arrancar el sistema:

<pre class="wp-block-code"><code>sudo systemctl enable tlp</code></pre>

Si además vas a compilar lineageOS, lo mejor que puedes hacer es instalar esto:

<pre class="wp-block-code"><code>sudo apt-get install git-core g++-multilib libc6-dev-i386 x11proto-core-dev libx11-dev libgl1-mesa-dev unzip fontconfig bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5 libncurses5-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev python-is-python3</code></pre>

Además es muy interesante la extensión para Firefox de KeepassXC que permite que se autocompleten las contraseñas. La podeis <a href="https://addons.mozilla.org/es/firefox/addon/keepassxc-browser/" target="_blank" rel="noreferrer noopener">descargar desde aquí</a>.

También muy interesante es limpiar lo que sobra después de todo con:

<pre class="wp-block-code"><code>sudo apt autoremove</code></pre>

## Encender el Firewall de Ubuntu {#h-encender-el-firewall-de-ubuntu}

Por defecto Ubuntu tiene un buen firewall pero este viene deshabilitado. Para activarlo, lo único que tenemos que hacer es:

<pre class="wp-block-code"><code>sudo ufw enable</code></pre>

y con este otro comando, comprobamos su estado:

<pre class="wp-block-code"><code>sudo ufw status</code></pre>