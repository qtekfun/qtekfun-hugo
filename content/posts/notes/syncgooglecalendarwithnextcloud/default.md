---
title: "Ver calendario de Google en Calendario de Nextcloud"
date: 2022-08-24T21:00:00+02:00
draft: false
---
Si te migras al calendario de Nextcloud (noralmente "self-hosted") la gente te seguirá mandando eventos a Google Calendar. Para ver esos eventos en tu calendario de Nextcloud hay una manera muy sencilla (se presupone que lo haces desde el PC/MAC):

* Ve al calendario en Google Calendar
* Pulsa el engranaje (arriba a la derecha) y a continuación "Configuración"
* En la barra lateral izquierda pulsa en "Configuración de mis calendarios"
* Despliega el calendario al que te quieres sincronizar y selecciona "Integrar el calendario"
* Aqui tendremos que copiar la "Dirección secreta en format iCal" que aparece oculta.

En este punto nos vamos a Nextcloud Calendar:

* En la barra lateral seleccionamos "New Calendar"  -> "New subscription from link (read-only)"
* Pegamos el enlace que tenemos en portapapeles copiado de Google

Y en tan solo unos segundos tendremos el calendario sincronizado.

## Bonus extra: cambiar la frecuencia de sincronización

Por defecto, Nextcloud sondea a Google una vez por semana como nos indica en <a href="https://docs.nextcloud.com/server/latest/admin_manual/groupware/calendar.html#refresh-rate" rel="noreferrer noopener" > la documentación oficial </a>. Para cambiar este ajuste a, por ejemplo, 6 horas basta con conectarse al contenedor de Nextcloud (si lo tienes en contenedores docker) e introducir este comando:

`occ config:app:set dav calendarSubscriptionRefreshRate --value "PT6H"`

{{< figure src="./refreshRate.jpg" title="Output Refresh Rate" >}}

El PT6H sale de la <a href="https://www.php.net/manual/en/dateinterval.construct.php" rel="noreferrer noopener" > documentación oficial de php</a>.

Con ello lo cambiamos a 6 horas y listo. Espero que os sea de ayuda.