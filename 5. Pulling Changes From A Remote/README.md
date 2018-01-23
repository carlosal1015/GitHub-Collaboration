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

> ### :warning: Prefiera trabajar a nivel local :warning: ###
> Debido a que GitHub tiene una interfaz web, te permite agregar confirmaciones manualmente a través de su interfaz. Pero solo porque puedas hacer algo, no significa que debas hacerlo. Hice la demostración de hacer estos cambios de esta manera para poder simular que las confirmaciones están en el repositorio remoto pero no en el repositorio local. Pero le recomiendo que siempre trabaje de forma local en un proyecto y luego inserte esos cambios en el repositorio remoto.

### Recuperar confirmaciones remotas ###

Ahora comparemos nuestro repositorio local y nuestro repositorio remoto. Solo tenemos tres confirmaciones en nuestro repositorio local:

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/5_1.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
Nuestro repositorio local solo tiene tres compromisos.</p>
</div>

Si bien hay cuatro commits en el repositorio remoto:

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/5_2.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
El repositorio remoto en GitHub tiene cuatro commits. Los tres de nuestro repositorio local y el que agregamos manualmente en GitHub.
</p>
</div>

### Tirando cambios con git pull ###

El commit local terminal en el commit `5a010d1` mientras que el remoto tiene dos commit adicionales: commit `4b81b2a` y commit `b847434`.

Además, observe que en nuestro repositorio local, cuando hicimos el `git log`, la rama de `origin/master` aún apunta hacia el commit `5a010d1`.

Recuerde que la rama de `origin/master` no es un mapeo en vivo de donde se encuentra la rama master del control remoto. Si el master del control remoto se mueve, la rama de `origin/master` local se mantiene igual. Para actualizar esta rama, necesitamos sincronizar los dos juntos.

`git push` sincronizará el repositorio remoto con el repositorio local. Para hacer con lo contrario (para sincronizar lo local con el control remoto), necesitamos usar `git pull`. El formato para `git pull` es muy similar al de `git push`: proporcionaste el nombre corto para el repositorio remoto y luego el nombre de la rama que deseas extraer en los commits.

```bash
$ git pull origin master
```

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/5_3.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
Ejecutando `git pull origin master` recuperará las confirmaciones de la rama `master` en el repositorio remoto `origin`.
</p>
</div>

Hay varias cosas que se deben tener en cuenta al ejecutar este comando:

- el formato es muy similar al de `git push`: cuenta, comprime y empaqueta artículos

- tiene la frase "avance rápido", lo que significa que Git hizo una fusión rápida (profundizaremos en esto en solo un segundo)

    - muestra información similar a `git log --stat` donde muestra los archivos que se han cambiado y cuántas líneas se agregaron o eliminaron en ellos.

Si no quiere fusionar automáticamente la rama local con la rama de seguimiento, entonces no usaría `git pull`, sino que usaría un comando diferente llamado `git fetch`. Es posible que desee hacer esto si hay commits en el repositorio que no tiene, pero también hay commits en el repositorio local que el remoto tampoco tiene.

Echemos un vistazo a `git fetch`.

## Resumen ##

Si hay cambios en un repositorio remoto que desea incluir en su repositorio local, entonces desea *incorporar* esos cambios. Para hacer eso con Git, usarías el comando `git pull`. Le dices a Git el nombre corto del control remoto del que deseas obtener los cambios y luego la rama que tiene los cambios que deseas:

```bash
$ git pull origin master
```

Cuando se ejecuta `git pull`, suceden las siguientes cosas:

- la(s) confirmación(es) en la rama remota se copian en el repositorio local
- la rama de seguimiento local `(origin/master)` se mueve para señalar el commit más reciente
- la rama de seguimiento local `(origin/master)` se fusiona en la rama local (`master`)

Además, los cambios se pueden agregar manualmente en GitHub (pero esto no se recomienda, así que no lo haga).
