---
title: "Visualizando la ley de Zipf en los proyectos alojados en GitHub"
categories:
  - Blog
tags:
  - datos
  - web
toc: true
---
<!-- * TOC
{:toc} -->


<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>


## Prefacio

Hace un par de años me topé con un vídeo de VSauce en el que trata el tema de [«El misterio de Zipf»](https://www.youtube.com/watch?v=fCn8zs912OE). Durante todo ese tiempo, hasta esta madrugada de noviembre en la que mezclaba mi quinta taza de café, había permanecido en mi cabeza como algo recurrente pero irrelevante.

Apareció una pequeña idea, y creo que me siento preparado para llevarla a cabo: tratar de visualizar la ley de Zipf en códigos fuente. Incluso, más allá de eso, tratar de visualizar la propensión de algunos lenguajes a *cumplir* con la ley de Zipf.

O si el número de colaboradores, número de estrellas, *forkeos*, y más, tiene relación con ello.

Este pequeño proyecto estará compuesto de tres fases *básicas*:

* el minado de datos en GitHub,
* el procesamiento de los archivos,
* la visualización de los datos.

## Introducción

La Ley de Zipf fue popularizada por George Zipf, lingüista en la Universidad de Harvard. Ésta, refleja la manera en que se distribuyen las ocurrencias de distintos «eventos».

Por ejemplo, en el uso del lenguaje natural, la palabra **más utilizada**, se utiliza dos veces más que la segunda más utilizada. Y tres veces más, que la tercera. Y cuatro veces más que la cuarta...

En general, la n-ésima palabra más utilizada en cualquier lenguaje, se utiliza aproximadamente (1/n) veces, las veces que se utiliza la palabra más utilizada:

$$
\begin{align*}
  P_n \approx 1 / n^a
\end{align*}
$$

donde $$P_n$$ es la frecuencia de la n-ésima palabra más frecuente, y
$$a$$, un número real positivo ligeramente mayor a 1.

## Minado de datos

Lo primero es construir una araña web. Yo decidí construirla en Python, por ser un lenguaje con el que tengo una mediana familiaridad, en el que nunca he programado algo así.

Después, crearemos un conjunto de datos, que contendrá el lenguaje de programación, el repositorio al que pertenece, el número de colaboradores, la fecha de creación, la fecha de la última actualización, número de estrellas y *forkeos* del repositorio, y, **lo más importante**: las ocurrencias de cada palabra clave.

Por ahora, la propiedad del número de ocurrencias quedará pendiente, ya que ésta la generaré en pasos siguientes.

Para lo que pretendo usar, seguramente no utilizaré ni siquiera la mitad de *propiedades* que voy a minar. Pero es que durante el desarrollo, se me ocurrió compartir el conjunto de datos. Así podré ver qué análisis pueden darle otras personas.

### Esquematización del proceso

1. **Escoger repositorios aleatoriamente**: Crear un archivo .csv, que contenga **n** direcciones web, apuntando a repositorios aleatorios. **Nota**: será importante ignorar los repositorios «recién nacidos»
1. **Minar todos los repositorios de la lista**: Obtener todos los archivos dentro de un repositorio, y procesar cada uno.

### Obtener direcciones de repositorios

Estaba comenzando a morir pensando cómo podía obtener una lista de repositorios *aleatoria*. Lista en la que no hubiera ninguna tendencia hacia ningún extremo en número de estrellas, forks, o fecha de actualización.

Los resultados de una búsqueda varían cada vez que sea hace una consulta, así que definitivamente no era una opción.

Después, encontré la API de GitHub. Específicamente [List all public repositories](https://developer.github.com/v3/repos/#list-all-public-repositories).

Así que, escribo un programa para consultar la API recurrentemente, y me dedico a otras cosas mientras lo dejo ejecutando.

```python
import csv
import requests
import json

api = "https://api.github.com/repositories?since="
since = 0

url_csv = open("urls.csv", 'w+')

url = api + str(since)
response = requests.get(url, auth=('davidomarf','mi llave que no puedo compartirte :('))

while response.ok:
    url = api + str(since)
    response = requests.get(url, auth=('davidomarf','mi llave que no puedo compartirte :('))

    reposList = json.loads(response.content)
    for repo in reposList:
        url_csv.write(repo['html_url'] + '\n')

    since = since + len(reposList)

url_csv.close()
```

## Procesamiento del archivo crudo

Una vez habiendo obtenido el archivo crudo, tenemos que procesarlo, de forma que podamos contabilizar **sólo** las palabras clave.

Es importante ignorar los comentarios, ya que si uno de ellos contiene una palabra clave, se contará, a pesar de que no es parte del código.

Se me ocurren varias maneras de procesar cada cadena para encontrar las ocurrencias de cada palabra clave, pero la única que me parece sensata, para mantener la eficiencia, es el uso de un *trie* -- no me siento realmente cómodo pronunciando ese término.

Cada lenguaje contendrá su propio *trie* de palabras clave. Puedo hacerlo manualmente, o puedo hacerlo programáticamente. Primero, crearé un arreglo con todas las palabras clave para cada lenguaje.

Algo así:

```python
kws.py = ['def', 'for', 'if', ...]
kws.js = ['function', 'for', 'break', ...]
kws.go = ['packge', 'string', 'append', ...]
```

Eso también podría hacerlo manualmente o programáticamente. Pero hacerlo de la segunda manera vencería el propósito: ahorrar tiempo, así que no.

Después, definiría una función que me permita crear un *trie* dado un arreglo de palabras:

```python
_end = '_end_'
 
def make_trie(words):
    root = dict()

    for word in words:
        current_dict = root
        for letter in word:
            current_dict = current_dict.setdefault(letter, {})
        current_dict[_end] = _end

    return root
```
**Función robada de [senderle](https://stackoverflow.com/a/11016430)
 
Y después, sólo actualizaría los valores de mi objeto `kws` usando esa función:

```python
kws.py = make_trie(kws.py)
```

```json
{
  "a": {
    "n": {
      "d": {
        "_end_": "_end_"
      }
    },
    "s": {
      "_end_": "_end_",
      "s": {
        "e": {
          "r": {
            "t": {
              "_end_": "_end_"
}}}}}}}
```