## El comando remoto de Git ##

El comando `git remote` te permitirá administrar e interactuar con repositorios remotos.

``
$ git remote
``

Intenta ejecutar este comando en un repositorio local que aún no has compartido con nadie. ¿Qué obtienes?

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/3_1.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
La aplicación Terminal que ejecuta el comando `git remote`. No se muestra ninguna salida ya que este repositorio no tiene conexión con un control remoto.</p>
</div>

Si no ha configurado un repositorio remoto, este comando no mostrará nada. Una advertencia a esto es si ha clonado un repositorio. Si tiene, entonces su repositorio tendrá automáticamente un control remoto porque fue clonado desde el repositorio en la URL que proporcionó. Miremos un repositorio que ha sido clonado.

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/3_2.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
La aplicación Terminal que ejecuta el comando `git remote`. Muestra la palabra `origin`.</p>
</div>

El proyecto en el que estoy es un clon de un proyecto de Google llamado `Lighthouse`. Este proyecto fue clonado de GitHub y es para la auditoría, las métricas de rendimiento y las mejores prácticas para las aplicaciones web progresivas.

## Nombres cortos remotos ##

La salida de `git remote` es solo la palabra `origin`. Bueno, eso es raro. La palabra "origin", aquí, se conoce como "nombre corto". Un shortname es solo una forma corta y fácil de referirse a la ubicación del repositorio remoto. Un nombre corto es local al repositorio actual (como en su repositorio local). La palabra "origin" es el nombre por defecto que se utiliza para referirse al repositorio remoto principal. Es posible cambiarle el nombre a algo más, pero generalmente se deja como "origen".

¿Por qué nos importa lo fácil que es referirse a una ubicación de repositorios remotos? Bueno, pronto descubrirá que necesitaremos la ruta al repositorio remoto en muchos de nuestros comandos. Y es mucho más fácil usar solo un nombre en lugar de la ruta completa al repositorio remoto.

Por ejemplo, cuál de estos es más fácil de entender:
- Dirígete hacia el norte durante aproximadamente un cuarto de milla, luego gira a la izquierda, sigue recto por esa carretera durante unos 5 kilómetros, luego gira a la derecha, continúa recto unos 300 pies hasta pasar el buzón azul, gira a la izquierda en Jack Street, ve 50 pies luego gire nuevamente a la izquierda en Owen Road, que se curvará hasta llegar a Finn Lane. La estructura que es la tercera a la izquierda
- Casa de la abuela

Puede ver que es mucho más fácil referirse a una ubicación con solo un nombre corto, como la casa de la abuela, en lugar de la forma completa de llegar desde su ubicación actual. :wink:

Si desea ver la ruta completa al repositorio remoto, entonces usted tiene que hacer es usar la bandera `-v`:

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/3_3.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
La aplicación Terminal que ejecuta el comando `git remote`. La salida incluye el nombre corto y la URL completa a la que se refiere.</p>
</div>

Aquí puede ver que si se usa la palabra `origin`, lo que realmente se usa es la ruta a `https://github.com/GoogleChrome/lighthouse.git`. También puede parecer un poco extraño que ahora haya dos controles remotos, ambos de "origin" y que van a la misma URL. La única diferencia está justo al final: la parte `(fetch)` y la parte `(push)`.

Observaremos tanto `fetch` como `push` en las próximas secciones.

Hemos hecho lo suficiente buscando ahora. ¡Hagamos algo activo y creemos nuestro propio proyecto simple y enviémoslo a un repositorio remoto!

## Crear un proyecto simple ##

Vamos a necesitar un proyecto de muestra para usar durante este curso para probar el trabajo con repositorios remotos, enviar actualizaciones al repositorio remoto y obtener cambios del repositorio remoto también.

#### PREGUNTA 1 DE 5 ####

¡Si no tienes un proyecto que quieras usar, entonces puedes seguirme!

#### Contenido del archivo README ####

# Travel Destinations

``# Destinos de viaje
Una aplicación simple para realizar un seguimiento de los destinos que me gustaría visitar.
``

#### Contenido de archivos HTML ####

Agregue el siguiente contenido al archivo index.html:

``html
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Travels</title>
    <meta name="description" content="">
    <link rel="stylesheet" href="css/app.css">
</head>
<body>

    <div class="container">
        <div class="destination-container">
            <div class="destination" id="florida">
                <h2>Florida</h2>
            </div>

            <div class="destination" id="paris">
                <h2>Paris</h2>
            </div>
        </div>
    </div>

</body>
</html>
``
