---
title: "Construyendo un extractor de datos con NodeJS"
categories:
  - Datos
  - Aplicaciones Web
tags:
  - extracción de datos
---

Desde hace ya casi un año, había tenido planeado desarrollar un bot para Messenger. Éste, recibiría un mensaje
con el nombre de un artista y una canción, y devolvería la letra.

Pero desde el momento en que lo consideré desarrollar, hasta hace una semana, se había quedado en la fase de "ojalá".

Pero, ya que en los últimos días había comenzado a desarrollar aplicaciones web con NodeJS gracias a [FreeCodeCamp](https://www.freecodecamp.org), aproveché y construí el bot que había planeado.

Para esto, primero tuve dos acercamientos, a los que llamaré **estático** y **dinámico**.

En este artículo, me concentraré en el acercamiento **estático** por ser descomunalmente más fácil de desarrollar.

- Encontrar la manera en que [Genius](https://genius.com) genera las direcciones para cada letra. 