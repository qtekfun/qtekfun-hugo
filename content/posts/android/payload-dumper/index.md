---
title: Cómo instalar y usar Payload Dumper
author: afi6cu
date: 2020-11-23T07:54:25+00:00
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
categories:
  - Software

---
Si quieres extraer las particiones de una actualización de algún smartphone Android, Payload dumper es lo que necesitas si tienes un payload.bin dentro del zip de una Full OTA.

## Descargar Payload Dumper

Para descargarlo, lo mejor es ir al <a href="https://github.com/vm03/payload_dumper" target="_blank" rel="noreferrer noopener">Github del autor</a> y desde la terminal:

<pre class="wp-block-code"><code>git clone https://github.com/vm03/payload_dumper.git</code></pre>

## Instalar las dependencias

Suponiendo que tenemos Python 3, nos vamos a la carpeta del Payload Dumper y ahí ejecutamos:

<pre class="wp-block-code"><code>pip install -r requirements.txt</code></pre>

## Extraer las particiones

Tenemos que extraer el payload.bin del zip de la rom, por ejemplo:

<pre class="wp-block-code"><code>unzip OnePlus8TOxygen_15.E.21_OTA_0210_all_2011132216_d2e1e993.zip</code></pre>

Y ahora vamos a extraer las particiones. Para evitar el error «ImportError: No module named bsdiff4»

<pre class="wp-block-code"><code>Traceback (most recent call last):
  File "payload_dumper.py", line 7, in &lt;module>
    import bsdiff4
ImportError: No module named bsdiff4</code></pre>

lo que tenemos que hacer es lanzarlo con Python3 como sigue:

<pre class="wp-block-code"><code>python3 payload_dumper.py payload.bin</code></pre>

Y listo! ya podéis instalar Magisk Manager o lo que queráis.