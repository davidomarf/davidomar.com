---
title: "Construyendo un \"sastre\" de imágenes"
categories:
  - vision artificial
  - imagen
tags:
  - proyectos
# header:
#   overlay_image: images/redes-neuronales.jpg
#   overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background
#   caption: "Photo by [Jingyi Wang](https://unsplash.com/@jingyi) on [Unsplash](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)"
---

Durante los próximos meses trataré de construir algo a lo que llamé "sastre" de imágenes, por no llamarlo "proyecto de *photo-stitching*".

¿Por qué sastre? Bueno, tiene que ver con el significado de *stitch*: puntada de costura. Podría haberlo llamado costurero, pero al imaginar un costurero junto a un sastre, el sastre me inspira mayor talento. Y eso es lo que es: la mejor wea.

Para empezar, debo de familiarizarme con los fundamentos del photo stitching, y qué mejor manera que escribiendo sobre ello.

Además, es la primera vez que escribiré sobre un proyecto **antes** de si quiera comenzar con la creación del repositorio, espero que el escribir una serie de publicaciones al respecto, me haga mantener un compromiso más fuerte hasta completarlo.

Así que bien, demasiado cuchichear, vamos al grano.

## ¿Qué es el *photo-stitching*?

Es un proceso en el que se combinan diferentes imágenes con áreas traslapadas, para generar una imagen de mayor dimensión.

![Ejemplo de photo-stitching](http://www.arcsoft.com/resource/image/technology/stitching/selfie_3.jpg)

Sus usos pueden ser la fotografía médica, la cartografía, o la estabilización de vídeo.

## El proceso

### Registro de imagen

Consiste en encontrar la función que alínea el contenido de una imagen con el contenido de otra.

Desde un punto de vista más técnico, el registro de imagen es una función que recibe como entrada dos imágenes diferentes, y produce como salida, una transformación geométrica.

### Calibración

Es tal vez el paso más *truculento* de todos en cuestión de intuición.

El objetivo es reducir las discrepancias en todas las áreas de traslape, encontrando los parámetros de la cámara como distancia focal, relación de aspecto.[^fn1]
[^fn2]
[^fn3]
[^fn4]
[^fn5]
[^fn6]
[^fn7]
[^fn8]

### Mezclado

El paso final, y tal vez el único en el que pensé al momento de idear el proyecto.

Aquí es donde se mezclan las imágenes de una manera dulce y suave como la mantequilla, para evitar que queden rastros de la operación en los puntos en donde se unieron las imágenes.

## Referencias

[^fn1]: [<i class="fa fa-link" aria-hidden="true"></i>](http://matthewalunbrown.com/papers/ijcv2007.pdf){: target="_blank"} Brown, M., & Lowe, D. G. (2007). Automatic panoramic image stitching using invariant features. International journal of computer vision, 74(1), 59-73.

[^fn2]: [<i class="fa fa-link" aria-hidden="true"></i>](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.96.6746&rep=rep1&type=pdf){: target="_blank"} Rankov, V., Locke, R. J., Edens, R. J., Barber, P. R., & Vojnovic, B. (2005, March). An algorithm for image stitching and blending. In Proceedings of SPIE (Vol. 5701, pp. 190-199).

[^fn3]: [<i class="fa fa-link" aria-hidden="true"></i>](https://pdfs.semanticscholar.org/2b0c/9c57572b156680e10f711b13ae205849493d.pdf){: target="_blank"} Szeliski, R. (2006). Image alignment and stitching: A tutorial. Foundations and Trends® in Computer Graphics and Vision, 2(1), 1-104.

[^fn4]: [<i class="fa fa-link" aria-hidden="true"></i>](http://www.cs.cmu.edu/~yx/papers/pstitcher.pdf){: target="_blank"} Xiong, Y., & Turkowski, K. (1998, October). Registration, calibration and blending in creating high quality panoramas. In Applications of Computer Vision, 1998. WACV'98. Proceedings., Fourth IEEE Workshop on (pp. 69-74). IEEE.

[^fn5]: [<i class="fa fa-link" aria-hidden="true"></i>](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.464.5408&rep=rep1&type=pdf){: target="_blank"} Fitzpatrick, J. M., Hill, D. L., & Maurer Jr, C. R. (2000). Image registration. Handbook of medical imaging, 2, 447-513.

[^fn6]: [<i class="fa fa-link" aria-hidden="true"></i>](https://en.wikipedia.org/w/index.php?title=Image_stitching&oldid=809039739){: target="_blank"} Image stitching. (2017, November 6). In Wikipedia, The Free Encyclopedia. Retrieved 20:00, December 26, 2017, from https://en.wikipedia.org/w/index.php?title=Image_stitching&oldid=809039739

[^fn7]: [<i class="fa fa-link" aria-hidden="true"></i>](http://ksimek.github.io/2013/08/13/intrinsic/){: target="_blank"} Simek, K. (2013, August 13). Sightations, A Computer Vision Blog. Retrieved December 26, 2017, from http://ksimek.github.io/2013/08/13/intrinsic/

[^fn8]: [<i class="fa fa-link" aria-hidden="true"></i>](https://hypjudy.github.io/2017/05/10/panorama-image-stitching/){: target="_blank"}HYPJUDY. (2017, May 10). [CVPR] Panorama Image Stitching. Retrieved December 26, 2017, from https://hypjudy.github.io/2017/05/10/panorama-image-stitching/