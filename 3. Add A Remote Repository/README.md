## El comando remoto de Git ##

El comando `git remote` te permitirá administrar e interactuar con repositorios remotos.

```bash
$ git remote
```

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

### Crear un proyecto simple ###

Vamos a necesitar un proyecto de muestra para usar durante este curso para probar el trabajo con repositorios remotos, enviar actualizaciones al repositorio remoto y obtener cambios del repositorio remoto también.

#### PREGUNTA 1 DE 5 ####

¡Si no tienes un proyecto que quieras usar, entonces puedes seguirme!

#### Contenido del archivo README ####

```
# Destinos de viaje
Una aplicación simple para realizar un seguimiento de los destinos que me gustaría visitar.
```

#### Contenido de archivos HTML ####

Agregue el siguiente contenido al archivo index.html:

```html
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
```

#### Contenido de archivo CSS ####

Agregue la siguiente información al archivo CSS:

```css
html {
    box-sizing: border-box;
    height: 100%;
}

*,
*::before,
*::after {
    box-sizing: inherit;
}

body {
    display: flex;
    margin: 0;
    height: 100%;
}

.container {
    margin: auto;
    padding: 1em;
    width: 80%;
}

.destination-container {
    display: flex;
    flex-flow: wrap;
    justify-content: center;
}

.destination {
    background: #03a9f4;
    box-shadow: 0 1px 9px 0 rgba(0, 0, 0, 0.4);
    color: white;
    margin: 0.5em;
    min-height: 200px;
    flex: 0 1 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

h2 {
    margin: 0;
    transform: rotate(-45deg);
    text-shadow: 0 0 5px #01579b;
}

#florida {
    background-color: #03a9f4;
}

#paris {
    background-color: #d32f2f;
}
```

En este punto, así es como se ve mi proyecto, pero recuerde que su proyecto puede ser lo que usted quiera, solo necesita asegurarse de tener un proyecto con algunas confirmaciones.

Una aplicación web simple que muestra los destinos a los que quiero ir (Florida y París) se abrió en el navegador Chromium.

#### Alojamiento en GitHub ####

Hay varias opciones para nosotros para alojar proyectos de Git. Pero uno de los sitios de alojamiento más populares es un servicio llamado [GitHub](https://github.com) del que quizás hayas oído hablar antes. Ahora el problema con GitHub es que el nombre es tan similar a Git que a veces las personas confunden a Git y GitHub y piensan que son lo mismo cuando en realidad son bastante diferentes.

-   Git es una herramienta de control de versiones
-   GitHub es un servicio para alojar proyectos de Git

Si ya está familiarizado con GitHub y sabe cómo crear un repositorio sin inicializar un archivo README, puede omitir este video y seguir adelante y hacer su repositorio con el mismo nombre que su proyecto de muestra, y recuerde no inicializar un archivo readme.

Si todavía no tienes una cuenta, regístrate para obtener una en la página de unirse a GitHub. Hay diferentes tipos de cuentas de GitHub para las que puede suscribirse, pero el nivel gratuito es todo lo que necesitamos para este curso. Y una cuenta gratis es lo que la mayoría de la gente usa de todos modos. Una vez que haya creado su cuenta, inicie sesión en GitHub y estará en la página de inicio:


Esto es lo que mi cuenta muestra justo después de iniciar sesión. Su información será diferente dependiendo de la cantidad de repositorios que tenga y de otros usuarios y repositorios que siga.

Al igual que todos los sitios web, GitHub actualiza su interfaz con bastante frecuencia, por lo que si lo que usted dice no se ve exactamente como en la imagen anterior, no se preocupe, las características importantes serán las mismas. Lo importante que debemos analizar en este momento es cómo crear un nuevo repositorio. En realidad, hay dos formas de hacerlo desde la página de inicio:

-   de la barra de navegación
-   el botón verde "nuevo repositorio" parte de la página en el lado derecho

GitHub tiene dos ubicaciones donde puedes crear un nuevo repositorio. El icono más ubicado en el encabezado de la página y el botón "Nuevo repositorio" en el medio de la página.


Utilizo el botón en la barra de navegación porque la barra de navegación está disponible en cada página, lo que facilita el acceso al nuevo enlace de repositorio.

En el menú desplegable, el enlace `new repository` lo lleva a la página de creación del repositorio. Solo necesitamos completar un campo de esta forma: el campo de nombre del repositorio.

GitHub crea una nueva página de repositorio. El único campo obligatorio es el campo de `Repository name`.

Normalmente, desea utilizar el nombre de su proyecto como el nombre del repositorio. Crear un repositorio, modificarlo más tarde o eliminarlo es relativamente fácil, así que no sienta que tiene que obtener el nombre perfecto aquí en esta página. Voy a crear un repositorio llamado "my-travel-plans" que es el mismo nombre que el proyecto de muestra que creé.

Está bien dejar la descripción vacía por el momento (aunque puede proporcionar una si lo desea). Como estoy en el plan de niveles gratuito, mi repositorio debe ser público (lo que significa que mi repositorio y todo mi código estarán disponibles de forma gratuita para que cualquiera pueda verlos). Si quiero que sea un repositorio privado, elegiría "Privado", lo que provocará que GitHub solicite la información de mi tarjeta de crédito y también me actualizará a un plan pago.

También voy a dejar sin marcar la opción "Inicializar este repositorio con el archivo README" porque no quiero que GitHub agregue un archivo README para mí.

## :warning: No inicializar con un README :warning: ##

Asegúrese de dejar desactivada la opción "Inicializar este repositorio con el archivo README". Proporcionaremos nuestro propio archivo README, por lo que no queremos que GitHub proporcione uno automáticamente.

Además, si permitimos que GitHub genere automáticamente un nuevo archivo README, entonces no se nos proporcionarán los comandos de configuración para ejecutar en el terminal. Todavía es posible obtener esa información, pero estará oculta.

Así que solo asegúrate de dejar este campo sin marcar, ¡y estarás listo para empezar!

¡Ahora solo hizo clic en ese gran botón "Crear repositorio" para crear su repositorio remoto!

[![Video](http://img.youtube.com/vi/myuGLZLYpYY/maxresdefault.jpg)](https://www.youtube.com/watch?v=myuGLZLYpYY)

Recuerde que el comando `git remote` se usa para crear y administrar repositorios remotos. Así que usaré el siguiente comando para crear una conexión desde mi repositorio local al repositorio remoto que acabo de crear en mi cuenta de GitHub:

```
$ git remote add origin https://github.com/richardkalehoff/RichardsFantasticProject.git
```
#### :warning: Remotos y Permisos :warning: ####

Advertencia: es importante que use la URL para el nuevo repositorio que creó en su perfil de GitHub. No use el de arriba porque eso es para el proyecto que acabo de crear en mi cuenta. Como este proyecto está en mi cuenta, no tiene acceso para enviarle cambios. Así que asegúrese de usar la URL de su proyecto. Los amigos Kagure, Jack, Owen y Finn tienen cada uno su propio proyecto de planes de viaje en:

-   https://github.com/kagure/my-travel-plans.git
-   https://github.com/jack/my-travel-plans.git
-   https://github.com/owen/my-travel-plans.git
-   https://github.com/finn/my-travel-plans.git

Hay un par de cosas que notar sobre el comando que acaba de ejecutar en la línea de comando:

1.  primero, este comando tiene el sub comando `add`

2.  la palabra `origin` que se usa; esto es establecer el nombre corto que discutimos anteriormente.

    1.  Recuerde que la palabra `origin` no está aquí, no es especial de ninguna manera.
    
    2.  Si desea cambiar esto a `repo-on-GitHub`, entonces (antes de ejecutar el comando) simplemente cambie la palabra "origin" por "repo-on-GitHub":
    
    ```$
    git remote add repo-on-GitHub
    https://github.com/richardkalehoff/RichardsFantasticProject.git
    ```
    
    3.  En tercer lugar, se agrega la ruta completa al repositorio (es decir, la URL al repositorio remoto en la web)
 
 Ahora usaré `git remote -v` para verificar que he agregado el repositorio remoto correctamente :
    ```En tercer lugar, se agrega la ruta completa al repositorio (es decir, la URL al repositorio remoto en la web) Ahora usaré git remote -v para verificar que he agregado el repositorio remoto correctamente:

`git remote add` se usó para crear un nombre corto de `origin` que apunta al proyecto en GitHub. La ejecución de `git remote -v` muestra tanto el nombre corto como la URL.

¡Fantástico! Todo se ve bien. Agregué un enlace a mi repositorio remoto con el comando `git remote add`, y luego verifiqué que todo se veía correcto con `git remote -v`.

