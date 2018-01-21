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
