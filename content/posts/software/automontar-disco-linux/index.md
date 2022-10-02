---
title: "Automontar Disco Linux"
date: 2022-10-02T11:10:33+02:00
draft: false
---
Cada vez que me instalo una máquina con linux, normalmente con Ubuntu, siempre suelo tener varios discos que configurar para que se automonten. Esto es personal, me refiero, como dice el refrán, "Cada maestrillo tiene su librillo" y yo suelo montar el / en un disco y tener discos secundarios para otras tareas, como por ejemplo, mis repos de código.

Hoy he reformateado una de mis torres y como me ha tocado buscar la info, he decidido dejarmela anotada aquí, y compartirtela por que posiblemente sea de utilidad. 

Vamos al lio

## Montar discos en linux de manera automática

*NOTA: partimos de la base de que ya teneis formateado el disco en `ext4` de no ser así, primero fromateadlo*

1. Lo primero es obtener el identificador del disco. Con `sudo fdisk -l` obtenemos el listado completo. En mi caso (haciendo truco para que no me salga todo y darte un ejemplo) tenemos algo así:

```
Disk /dev/sdc: 465,76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: STXX00820AS     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8C28528B-E9E5-4C2A-BA83-A97299B4A74
```

Mi identificador es `/dev/sdc/` asique nos quedamos con el dato.

2. Ahora necesitamos saber cual es el *UUID* del disco y para ello usamos el comando `sudo blkid` que nos da todos los identificadores unicos de los discos del sistema. Saldrán muchos pero nos quedamos con el que necesitamos:

```
/dev/sdc1: UUID="a105ad60-c417-4e92-9bXX-f9d68c1db42f" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="83110bde-57XX-4ded-afa4-790adcefa61b"
```

De este paso nos quedamos con el campo `UUID="a105ad60-c417-4e92-9bXX-f9d68c1db42f"` aunque notad que aqui el valor va entre comillas dobles y para el siguiente paso las quitaremos.

3. Decidimos donde queremos montarlo. En mi caso esto es un disco adicional que hará de repo de codifo, por lo que lo montaré en `/repo`. Para crear esa carpeta:

`mkdir /repo`

4. Abrimos con nuestro editor favorito el fichero `/etc/fstab` y añadimos lo siguiente
```
# HDD for storage
UUID=a105ad60-c417-4e92-9bXX-f9d68c1db42f /repo ext4 defaults 0 1
```

5. Probamos que va todo bien. Si dejamos incorrecto el ficher fstab en el proximo reboot nuestro pc no arrancará. Por ello este paso es *IMPORTANTÍSIMO*. Para probarlo hacemos:
`sudo mount -a`
Si va todo bien no habrá ningun mensaje, simplemente nos devolverá el cursor.

6. *BONUS:* Como soy un vago, no quiero tener que meter `cd /repo` para ir a la nueva carpeta, si no que con solo `repo` vaya. Para ello, añadimos esta linea en `~/.bash_aliases`:
`alias repo="cd /repo"`

Y listo. Con eso lo teneis todo listo.