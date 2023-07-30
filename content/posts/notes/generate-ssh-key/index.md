---
title: "Generate Ssh Key"
date: 2023-07-30T20:05:03+02:00
draft: false
---

No sé la de veces que he consultado la [guía de github acerca de cómo generar una ssh-key y añadirla al ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
sobre todo en Windows. Hoy me he decidido a hacer mi post para dejar de darles visitas :P. En realidad es por tener
documentado todo en el mismo sitio, ya que cada vez que quiero repetir este proceso, tengo las cosas manga por
hombro y no soy capaz ni de encontrarlo entre mis marcadores.

## Generar una ssh-key en Powershell

Los pasos son muy sencillos:

1. Abrir Powershell
2. Ejecutar `ssh-keygen -t ed25519 -C "your_email@example.com"`
3. Poned el nombre que identifique esta ssh-key. Pongamos que es para usar con github, yo pondría algo como: `C:\Users\Qtekfun/.ssh/github`
4. Es muy interesante que cuando nos pregunte, pongamos una password. Si quereis obviar este paso, simplemente
   pulsad "Enter"

Y listo, ya tenemos tanto la clave privada ("github") como la clave pública ("github.pub") que debemos darle a los
servidores o servicios donde nos queramos autenticar.

## Añadir ssh-key al ssh-agent de windows

Lo primero sería verificar en los servicios de Windows, que teneomos el Ssh-agent corriendo. En Windows recibe el
nombre de "OpenSSH Authentication Agent".

Una vez hecho esto, simplemente usaríamos el comando `ssh-add C:\Users\Qtekfun\.ssh\github` y ya tendríamos la llave
ssh añadida. Si tenía clave, nos la pedirá al añadirla y en cada inicio del agente.

## Usar esta clave en github

Lo siguiente que necesitarás al usar ssh es decirle al cliente que para X server, en este caso github.com, quieres
usar esta clave. La manera de hacerlo es creando (o modificando) el fichero "/c/Users/YOU/.ssh/config". En el,
creariamos una entrada como la que sigue:

```
Host github.com
  HostName github.com
  User git
  IdentityFile C:\Users\YOU\.ssh\github
```

Sí es para un server que po ejemplo no tiene habilitado el ssh en el puerto 22, podríamos añadir la linea `Port 22`
para indicar que con el servidor de la linea Host hay que aplicar las configuraciones que vienen a continuación.

Y con eso y un bizcocho, ya tenéis el ssh configurado como es debido.
