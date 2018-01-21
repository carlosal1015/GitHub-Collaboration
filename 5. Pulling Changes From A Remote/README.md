### Extraiga los cambios de un control remoto ###

Supongamos que estamos en una situación en la que hay confirmaciones en el repositorio remoto que no tenemos en nuestro repositorio local. Esto puede suceder de varias maneras: puede estar trabajando en un equipo y un compañero de trabajo ha introducido nuevos cambios en el control remoto. Alternativamente, podría estar trabajando en el mismo proyecto pero desde diferentes computadoras; por ejemplo, supongamos que tiene una computadora de trabajo y una computadora personal, y contribuye con el repositorio de ambas. Si envía cambios al repositorio desde su computadora de trabajo, el repositorio local en su computadora personal no reflejará esos cambios. ¿Cómo sincronizamos los nuevos cambios que están en el control remoto en el repositorio local? Eso es exactamente donde vamos a mirar ahora. Primero veamos cómo funciona la teoría de los cambios remotos, ¡entonces lo haremos nosotros mismos!

[![Video](http://img.youtube.com/vi/MjNU2LTDVAA/maxresdefault.jpg)](https://www.youtube.com/watch?v=MjNU2LTDVAA)

Lo dije antes, pero lo diré de nuevo, la rama que aparece en el repositorio local está realmente rastreando una rama en el repositorio remoto (por ejemplo, el `origin/master` en el repositorio local se llama una rama de seguimiento porque está rastreando el progreso del rama `master` en el repositorio remoto que tiene el nombre corto "origin").

### Agregar cambios remotos ###

Como aún no tenemos ningún commit en nuestro repositorio remoto y no estamos colaborando con nadie, vamos a simularlo y agregar algunos commits manualmente a través de la interfaz de GitHub en la web.

A continuación se muestra un video de recorrido. Use los fragmentos de código para seguir el video.

### Nuevo contenido CSS ###

Agregue el siguiente nuevo conjunto de reglas:

```css
.destination:hover h2 {
    transform: rotate(0deg);
}
```
Agregar `transición: transformar 0.5s;` para el conjunto de reglas `h2`, por lo que ahora debería ser:

```css
h2 {
    margin: 0;
    transform: rotate(-45deg);
    transition: transform 0.5s;
    text-shadow: 0 0 5px #01579b;
}
```

[![Video](http://img.youtube.com/vi/UBYxcTg6VLU/maxresdefault.jpg)](https://www.youtube.com/watch?v=UBYxcTg6VLU)

> ### :warning: Prefiere trabajar a nivel local :warning: ###
> Debido a que GitHub tiene una interfaz web, te permite agregar confirmaciones manualmente a través de su interfaz. Pero solo porque puedas hacer algo, no significa que debas hacerlo. Hice la demostración de hacer estos cambios de esta manera para poder simular que las confirmaciones están en el repositorio remoto pero no en el repositorio local. Pero le recomiendo que siempre trabaje de forma local en un proyecto y luego inserte esos cambios en el repositorio remoto.

### Recuperar confirmaciones remotas ###

Ahora comparemos nuestro repositorio local y nuestro repositorio remoto. Solo tenemos tres confirmaciones en nuestro repositorio local:

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/5_1.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
</p>
</div>
