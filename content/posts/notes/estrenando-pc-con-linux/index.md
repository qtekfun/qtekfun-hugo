---
title: "Estrenando Pc Con Linux"
date: 2022-11-07T17:38:13+01:00
draft: false
---

Este post es una nota a mi yo futuro. Cada vez que estreno y formateo un nuevo pc hay muchas cosas que quiero instalar. Intenté hacerlo con ansible en este [proyecto de github](https://github.com/qtekfun/prov-my-ubuntu) pero es un tostón mantenerlo. Por ello prefiero dejarme aqui todo apuntado y que os sea de utilidad a los que lo leeis.

## Instalando Apps
Aquí algunas de las cosas que uso:

```
sudo apt install terminator vim git build-essential \
nextcloud-desktop net-tools unzip virtualbox wireguard \
ca-certificates curl android-sdk-platform-tools \
android-sdk-platform-tools-common dnsutils imagemagick \
meld gparted ffmpeg python3-pip libreoffice webp thunderbird \
exfatprogs
```

## Instalando Snaps
Y aqui instalando algunos snaps:
```
sudo snap install spotify bitwarden
sudo snap install --classic code
```

## Enable and configure UFW
```
sudo ufw enable
sudo ufw default deny incoming
```

## Git y sus alias
Para eso ya hice un post que dejo aqui con los [mejores alias para git](https://qtekfun.com/posts/notes/git-basics/)
