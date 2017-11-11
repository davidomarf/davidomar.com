---
title: "Construyendo un extractor web con NodeJS, Cheerio, y Request"
categories:
  - Datos
  - Aplicaciones Web
tags:
  - extracción de datos
sidebar:
  nav: "extractor-web-estatico"
---

## Introducción y motivación
Desde hace ya casi un año, había tenido planeado desarrollar un bot para Messenger. Éste, recibiría un mensaje
con el nombre de un artista y una canción, y devolvería la letra.

Pero desde el momento en que lo consideré desarrollar, hasta hace una semana, se había quedado en la fase de "ojalá".

Pero, ya que en los últimos días había comenzado a desarrollar aplicaciones web con NodeJS gracias a [FreeCodeCamp](https://www.freecodecamp.org), aproveché y construí el bot que había planeado.

Lo primero que tuve que desarrollar, fue [mi propia API](https://gimme-the-lyrics.glitch.me). Parte de hacerlo, implicaba extraer datos de la web. Y sobre eso tratará este artículo.

Para esto, primero tuve dos acercamientos, a los que llamaré **estático** y **dinámico**.

El primero consiste en descubrir cómo se generan las direcciones web para cada canción. Después, aprovecharlo para generar las direcciones *'semi-programáticamente'*, y extraer la letra de esa dirección.

La razón por la que escribo *'semi-programáticamente'* se hará evidente a lo largo de la publicación.

El segundo, consiste en hacer una consulta al sitio web, y obtener la mejor coincidencia con nuestra búsqueda. Pero esta página es generada dinámicamente, después de la ejecución. Así que tratar de extraer datos se complica. Ya que no son parte del html, sino '*generados*'.

Si no ha quedado clara la diferencia, lo hará después de que explique ambos métodos.

Con el fin de mantener la legibilidad -*y satisfacer un poco mi ligera y reciente obsesión con la modularidad*-, separaré este artículo en dos partes, cada una cubriendo cada método.

------------------------

## El *acercamiento* dinámico