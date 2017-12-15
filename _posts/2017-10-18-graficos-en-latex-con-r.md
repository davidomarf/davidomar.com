---
title: "Añadir gráficos a LaTeX creados con R automáticamente"
categories:
  - Blog
tags:
  - datos
  - web
---

Durante el último par de días comencé a aventurarme en la gran curva de aprendizaje de [LaTeX](https://www.latex-project.org). Después de pasar poco más de una hora instalando [MikTex](https://miktex.org) y **varios** paquetes que después no volví a ocupar, logré *entrar en la zona*.

Después de un rato sintiéndome ya un poco cómodo, quise incrustar gráficas hechas en R, pero la manera en la que lo estaba haciendo era lenta. Consistía básicamente en:

- Exportar la gráfica como "plot.png"
- Mover plot.png al directorio de mi proyecto TeX
- Incrustar la imagen

Si quería hacer múltiples gráficos, tenía que repetir todo eso por cada nuevo gráfico. Y peor aún si quería hacer ajustes estéticos.

Al final terminé pseudo-automatizando la incrustación y renderización de gráficos.

Consiste en:

- Crear todos los gráficos que vayas a necesitar usando R
- Imprimir un gráfico por página en un archivo PDF
- Incrustar una página del pdf como imagen en LaTeX

Aunque en esencia pueda parecer un proceso más largo, lo único que tenemos que hacer cada que queramos actualizar los gráficos es **ejecutar el programa** y **recompilar el archivo TeX**

## Estructura del directorio

En la carpeta donde está localizado el archivo .tex, crearás una carpeta llamada img -o como quieras llamarla, pero ahí guardarás las imágenes para tu documento.

Dentro de img, escribirás el script en R que creará tus gráficos.

Algo así:
```
-/
├── img/
│ ├── plot.r
├── miDocumento.tex
```
## Script en R

Los siguientes gráficos son algo básicos y sólo sirven para ejemplificar el proceso que utilizo.

Primero, crearé dos gráficos con el conjunto *iris*, y los almacenaré en el archivo "irisPlot.pdf":
<script src="https://gist.github.com/DavidOmarF/5615b1180014de11a25c4ccd977f9ca7.js"></script>


y luego dos gráficos con el conjunto *diamonds*, y los almacenaré en el archivo "diamondsPlot.pdf":
<script src="https://gist.github.com/DavidOmarF/0d8d77540f8943c0aaf0289a09d1fe9d.js"></script>

Los dos archivos resultantes son [irisPlot.pdf](https://drive.google.com/file/d/0BzX5n5sP6iUGMEp4S2xtYWZmODQ/view?usp=sharing) y [diamondsPlot.pdf](https://drive.google.com/file/d/0BzX5n5sP6iUGYnZVbHB2RG9fN3c/view?usp=sharing)

---------------------

De los dos gists anteriores, las líneas que merecen la atención son:

```r
pdf("miArchivo.pdf")
%...
%...
plot(figura)
```

El primero, escribe el archivo PDF, y el segundo, imprime «figura» en una página del PDF.

## Incrustarlos en documento TeX
Ahora tenemos que insertar los gráficos creados en nuestro documento .tex
<script src="https://gist.github.com/DavidOmarF/1858166ced5ea2dec69a4c0a021e2134.js"></script>
Y el resultado [se ve así](https://drive.google.com/open?id=0BzX5n5sP6iUGcW54U2lkRGtGU2M).


De nuevo, las líneas que merecen la atención son:

```TeX
\usepackage{graphicx}
\graphicspath{./img/}
%...
%...
\includegraphics[page = 1]{irisPlot}
```

Los primeros dos incluyen el paquete graphicx y especifican la ruta para los recursos gráficos.

La última línea es la manera en la que se incluye un gráfico desde un PDF especificando la página

## Conclusión

Tal vez no sea la manera más eficiente de elaborar y renderizar gráficos en nuestros documentos LaTeX. Tal vez haya mejores formas, más automatizadas. Sin embargo, este *método* funcionó para mí, y me consiguió ahorrar tiempo. Especialmente cuando se trataba de actualizar varios gráficos.