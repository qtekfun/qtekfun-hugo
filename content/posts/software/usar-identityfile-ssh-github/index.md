---
title: "Cómo usar una ssh-key con github correctamente"
date: 2022-10-02T20:33:50+02:00
draft: true
---

Hoy me he vuelto a configurar otro pc con linux, en concreto con Ubuntu 22.04. De hecho, ya expliqué en este post [cómo automontar un disco en ubuntu](https://qtekfun.com/posts/software/automontar-disco-linux/) porque al tener varios discos los monto con distintos usos.

Pero para mantener esta web que está hecha con hugo, tenía que clonarme el repo de guthub, y para que fuese más facil, quería hacerlo con un `ssh-key`. Hasta ahí guay. Es facil hacerlo siguiendo los pasos del [post de github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

Sin embargo no queria tener que estar ejecutando el `eval "$(ssh-agent -s)"` cada vez que me logueaba o abría una terminal. Aunque podemos meterlo en un fichero de entorno, no me parecía coherente ni correcto. Así que buscando he logrado la forma más "correcta".

Para hacerlo, es sencillo. Hay que usar un fichero, que por defecto no está creado, llamado config. Este fichero le dice a ssh para un host concreto como ha de configurar la conexión. En el caso de tener una clave ssh para github llamada "github" (teniendo en cuenta que tendreis su clave publica asociada llamada github.pub y que la habréis configurado en github.com como se debe) tendremos que crear este fichero de la siguiente manera:

1. Creamos el fichero config:
`touch ~/.ssh/config`
2. Creamos la entrada para github:
```
Host github.com
        User git
        IdentityFile /home/<user>/.ssh/github
        IdentitiesOnly yes
```

¡Y ya esta! con eso, cuando ssh vaya a conectar contra el host "github.com" utilizará la configuración que le hemos puesto.

*NOTA: editad el path del IdentityFile con el path a vuestras claves*
*NOTA2: la linea es `IdentityFile` no `IdentifyFile` como he visto por ahí*

¡Espero que os haya sido útil!
