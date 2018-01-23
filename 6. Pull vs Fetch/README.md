## Pull vs Fetch ##

[![Video](http://img.youtube.com/vi/kxXdk2HcOBo/maxresdefault.jpg)](https://www.youtube.com/watch?v=kxXdk2HcOBo)

Git fetch se usa para recuperar commits de la rama del repositorio remoto, pero no fusiona automáticamente con la rama de seguimiento remoto una vez que se han recibido esas confirmaciones.

El párrafo anterior es un poco denso, ¿por qué no lo vuelves a leer una vez más?

Proporcionas la misma información exacta a `git fetch` como lo haces para `git pull`. Así que proporciona el nombre corto del repositorio remoto desde el que desea recuperar y luego la rama que desea recuperar:

```bash
$ git fetch origin master
```

Cuando se ejecuta `git fetch`, suceden las siguientes cosas:

- la (s) confirmación (es) en la rama remota se copian en el repositorio local
- la rama de seguimiento local (por ejemplo, origen / principal) se mueve para señalar el compromiso más reciente

Lo importante a tener en cuenta es que la sucursal local no cambia en absoluto.

Puedes pensar en `git fetch` como la mitad de un `git pull`. La otra mitad de `git pull` es el aspecto de fusión.

Un punto principal cuando se quiere usar `git fetch` en vez de `git pull` es si su sucursal remota y su sucursal local tienen cambios que ninguno de los otros tiene. En este caso, desea buscar los cambios remotos para obtenerlos en su sucursal local y luego realizar una combinación manualmente. Luego puede enviar esa nueva fusión al control remoto.

Echemos un vistazo a eso.

[![Video](http://img.youtube.com/vi/jwyQUfE1Eqw/maxresdefault.jpg)](https://www.youtube.com/watch?v=jwyQUfE1Eqw)

#### Resumen ####

Puedes pensar en el comando `git pull` haciendo dos cosas:

1.  obteniendo cambios remotos (que agrega los commits al repositorio local y mueve la rama de seguimiento para que apunte a ellos)
2.  fusionar la sucursal local con la sucursal de seguimiento

El comando `git fetch` es solo el primer paso. Simplemente recupera los commits y mueve la rama de seguimiento. No fusiona la sucursal local con la rama de seguimiento. La misma información proporcionada a `git pull` se pasa a `git fetch`:

- el shorname del repositorio remoto
- la rama con se compromete a recuperar

```bash
$ git fetch origin master
```
