# Push Changes To A Remote #

[![Video](http://img.youtube.com/vi/21TvMEtMRys/maxresdefault.jpg)](https://www.youtube.com/watch?v=21TvMEtMRys)

### Revisión de commits ###

Echemos un vistazo a los commits que tengo en mi repositorio.

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/4_1.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
La aplicación del terminal que muestra el registro de las confirmaciones del proyecto.
</p>
</div>

Usé el siguiente comando de registro para mostrar estos commits

```bash
$ git log --oneline --graph --decorate --all
```

Sin embargo, estas confirmaciones solo se encuentran en el repositorio local. Todavía no se han enviado al repositorio remoto. Cuando se envían confirmaciones al control remoto, aparecerá un indicador de bifurcación remota en el registro. Como no hay indicadores de ramas remotas, podemos decir que no hay confirmaciones en el repositorio remoto. Pero solo para estar 100% seguros veamos el repositorio remoto en GitHub para ver si hay algún compromiso.

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/4_2.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
El repositorio remoto no contiene ningún commit, por lo que GitHub muestra la pantalla de configuración del repositorio.</p>
</div>

Como no hemos enviado ninguna actualización de commits a GitHub, todavía nos muestra la pantalla de configuración para decirnos cómo podemos conectar nuestro repositorio local al repositorio remoto y enviar algunas confirmaciones. Como esta sigue siendo la pantalla de configuración, podemos saber que no hay conmits en el repositorio remoto.

### Comisiones de envío ###

Para enviar confirmaciones locales a un repositorio remoto, debe usar el comando `git push`. Usted proporciona el nombre corto remoto y luego proporciona el nombre de la sucursal que contiene las confirmaciones que desea enviar:`

```bash
$ git push <remote-shortname> <branch>
```
El norme corto de mi control remoto es `origin` y los commits que quiero enviar están en la rama `master`. Así que usaré el siguiente comando para enviar mis confirmaciones al repositorio remoto en GitHub:

```bash
$ git push origin master
```

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/4_3.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
La aplicación del terminal que muestra el comando `git push`. Solicita mi nombre de usuario, contraseña (que no se muestra), y luego muestra información sobre lo que está haciendo para enviar las confirmaciones.</p>
</div>

Aquí un par de cosas para notar:

- Dependiendo de cómo haya configurado GitHub y la URL remota que se está utilizando, es posible que deba ingresar su nombre de usuario y contraseña.
  - esto sucederá si usa la versión HTTP del control remoto (en lugar de la versión ssh)
  - Si ha configurado GitHub para usar el protocolo SSH y lo ha proporcionado con su clave SSH, entonces no necesita preocuparse por seguir este paso. Consulte la página de Conexión a GitHub con la documentación de SSH si está interesado en usar SSH con GitHub.
- Si tiene que ingresar su nombre de usuario y contraseña, su nombre de usuario aparecerá después de escribir pero su contraseña no lo hará. Así que sigue escribiendo tu contraseña y presiona intro cuando hayas terminado.
  - Si encuentra algún error con su contraseña, no se preocupe, solo le pedirá que la ingrese de nuevo
- Git comprime algo para hacerlo más pequeño y luego lo envía al control remoto
- Se crea una nueva rama: en la parte inferior dice `[nueva rama]` y luego `master -> master`

Ahora veamos GitHub:

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/4_4.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
¡Todo mi proyecto está en GitHub!</p>
</div>

Nuestro proyecto está en GitHub: ¡qué increíble y fácil fue eso! Una característica interesante que GitHub hace es que muestra automáticamente el contenido del archivo README que puede ser extremadamente útil.

GitHub también muestra muchos detalles sobre nuestro repositorio. Ahora mismo está mostrando que hay:

- tres confirmaciones 
- una rama
- un colaborador

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/4_5.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
La página principal del proyecto en GitHub muestra información sobre el repositorio.</p>
</div>

Ahora, antes de seguir adelante, revisemos el repositorio local para ver cómo cambió después de presionar.

Ejecute el siguiente comando:

```bash
$ git log --oneline --graph --decorate --todo
```

*Importante: asegúrese de incluir las banderas `--decorate` y -`-all`*.

<div class="figure">
<p align="center">
<img src="https://github.com/carlosal1015/GitHub-Collaboration/blob/master/images/4_6.png" width="700" alt="My caption"/></p>
<p align="center" class="caption">
La aplicación de terminal que muestra los resultados de ejecutar `git log --oneline --graph --decorate --all`. La nueva rama de seguimiento de origen/maestro ahora existe</p>
</div>

¡Ahora tenemos un nuevo marcador en la salida! Este marcador es `origin/master` y se denomina **ramal de seguimiento**. El nombre de una rama de seguimiento incluye el nombre corto del repositorio remoto, así como el nombre de la sucursal. Por lo tanto, el `origin/master` de la rama de seguimiento nos dice que el origen remoto tiene una rama maestra que apunta a confirmar `9b7d28f` (e incluye todas las confirmaciones antes de `9b7d28f`). Esto es realmente útil porque esto significa que podemos rastrear la información del repositorio remoto aquí mismo en nuestro local.

Una cosa muy importante que debe saber es que esta rama de rastreo de `origin/master` no es una representación en vivo de dónde existe la rama en el repositorio remoto. Si un cambio se realiza en el repositorio remoto no por nosotros, sino por otra persona, la rama de seguimiento de `origin/master` en nuestro repositorio local no se moverá. Tenemos que decirle que busque las actualizaciones y luego se moverá. Veremos cómo hacer esto en la siguiente sección.
¡Ahora tenemos un nuevo marcador en la salida! Este marcador es `origin/master` y se denomina **ramal de seguimiento**. El nombre de una rama de seguimiento incluye el nombre corto del repositorio remoto, así como el nombre de la sucursal. Por lo tanto, el `origin/master` de la rama de seguimiento nos dice que el origen remoto tiene una rama maestra que apunta a confirmar `9b7d28f` (e incluye todas las confirmaciones antes de `9b7d28f`). Esto es realmente útil porque esto significa que podemos rastrear la información del repositorio remoto aquí mismo en nuestro local.Una cosa muy importante que debe saber es que esta rama de rastreo de `origin/master` no es una representación en vivo de dónde existe la rama en el repositorio remoto. Si un cambio se realiza en el repositorio remoto no por nosotros, sino por otra persona, la rama de seguimiento de `origin/master` en nuestro repositorio local no se moverá. Tenemos que decirle que busque las actualizaciones y luego se moverá. Veremos cómo hacer esto en la siguiente sección.
¡Ahora tenemos un nuevo marcador en la salida! Este marcador es `origin/master` y se denomina **ramal de seguimiento**. El nombre de una rama de seguimiento incluye el nombre corto del repositorio remoto, así como el nombre de la sucursal. Por lo tanto, el `origin/master de la rama de seguimiento nos dice que el origen remoto tiene una rama maestra que apunta a confirmar 9b7d28f (e incluye todas las confirmaciones antes de `9b7d28f).
