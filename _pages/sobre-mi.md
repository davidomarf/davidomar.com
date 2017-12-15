---
layout: archive
permalink: /sobre-mi
title: "Sobre mí"
header:
  overlay_image: images/unsplash-image-1.jpg
  # overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background
  caption: "Créditos: [**Unsplash**](https://unsplash.com)"
  cta_label: "More Info"
  cta_url: "https://unsplash.com"
---

<script>
var description = [
  "sé cocinar un buen desayuno en sólo 4 minutos",
  "jamás he podido entender LoL", 
  "amante de la <i>música de abuelitos</i>",
  "sólo ocupo Instagram para mirar fotos de animalitos"
];
var randomNumber = Math.floor(Math.random() * description.length);
</script>
<script>
window.onload = function() {
  var a = document.getElementById("random-description-switcher");
  a.onclick = function() {
    if (randomNumber < description.length - 1) {
      randomNumber++;
      document.getElementById("random-description").innerHTML =
        description[randomNumber];
    } else {
      randomNumber = 0;
      document.getElementById("random-description").innerHTML =
        description[randomNumber];
    }
    return false;
  };
};
</script>

¡Hola! Mi nombre es David. Soy desarrollador, escritor de pasatiempo y <script>document.write('-<a id="random-description-switcher" href="#">entre otras cosas</a>-, <span id="random-description"> ' + description[randomNumber] + '</span>');</script>.

Probablemente te interese leer los [proyectos en los que estoy involucrado](), sin embargo, antes te platicaré un poco más sobre mí.

Mis intereses profesionales han variado enormemente durante toda mi vida. Desde la lingüística y la antropología; hasta la neurología y la física.

Sin embargo, con el tiempo, se redujeron a solo dos: la construcción, y la computación.

Durante dos años estudié una carrera técnica en construcción, donde cursé un par de materias que resultaron ser increíblemente interesantes para mí: la topografía y el diseño arquitectónico.

Me había encantado todo, pero aún quería darle un vistazo a otros intereses. Así que decidí estudiar ingeniería y ciencias en la computación. Y tras tan sólo unas semanas, me di cuenta de cuán apasionante era.

Cuando comencé a escribir mis primeros programas en C, me emocionaba imaginando el potencial de la computación. Y me emociona más ahora, al darme cuenta de que aún mis ideas más ambiciosas, se quedan bastante cortas a la realidad.

Durante mi primer año estudiando, realicé una investigación que originalmente trataría sobre **Las implicaciones éticas y morales de la inteligencia artificial**.

Para ese entonces, no tenía ni idea de lo que eso significaba. Incluso, he de aceptar que pequé más de una vez imaginando escenarios apocalípticos, rayos láser, y robots oji-rojos. ¡Cuán equivocado estaba!

Durante la investigación, leí y miré artículos, libros, conferencias y vídeos al respecto. Ahí aprendí un poco sobre [algoritmos genéticos](), [datos masivos](), [redes neuronales](), [visión artificial](), [neurología](), etc.

Una de esas charlas, [Las maravillosas y pavorosas consecuencias de los computadores que pueden aprender](), impartida por Jeremy Howard, hizo que en mí naciera un nuevo y más fuerte interés: la ciencia de datos.

## Proyectos

### Does it close? [<i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/DavidOmarF/does-it-close)

Aplicación web para estudiantes y profesionales de la topografía. Revisa y corrige levantamientos topográficos. Genera hojas de cálculo y escribe scripts para CAD descargables.

**Tecnologías:** NodeJS

Puedes [ver el proyecto en GitHub](https://github.com/DavidOmarF/does-it-close), [leer la documentación](https://davidomarf.gitbooks.io/does-it-close/content/), o [probar la aplicación](https://does-it-close.herokuapp.com)

### Autómata Determinista Finito [<i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/hectoraldairah/Deterministic-Finite-Automaton)

Aplicación web para definir autómatas de estado finito y evaluar cadenas con el autómata.

Puedes [ver el proyecto en GitHub](https://github.com/DavidOmarF/does-it-close), o [leer la documentación](https://davidomarf.gitbooks.io/does-it-close/content/).

## Cuadernos

Los cuadernos que aquí menciono, son proyectos en [Visualización de datos]() y [Aprendizaje Máquina](), escritos en Jupyter Notebook y alojados en Kaggle.

### Familias de lenguas a través del mundo