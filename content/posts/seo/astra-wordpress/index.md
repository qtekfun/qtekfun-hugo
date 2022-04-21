---
title: Astra WordPress evitar que carge Astra.woff y más
date: 2020-11-27T09:45:10+00:00
ampforwp-amp-on-off:
  - default
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
categories:
  - SEO
---
Este post es todas las cosas que he tenido que irle haciendo a Astra para que rule en condiciones. 

## Desactivar astra.woff

Quitar esta fuente que nos fastidia el pagespeed es facil. Primero hay que poner un tema hijo. Para ello, Astra nos lo da todo. Hay que bajarlo desde aqui:

<div class="wp-container-2 wp-block-buttons aligncenter">
  <div class="wp-block-button">
    <a class="wp-block-button__link" href="https://wpastra.com/child-theme-generator/" target="_blank" rel="noreferrer noopener">Astra child theme</a>
  </div>
</div>

Después en el editor de php hay que añadir:

<pre class="wp-block-code"><code>add_filter( 'astra_enable_default_fonts', '__return_false' );</code></pre>

Y no olvideis ¡borrar la caché!