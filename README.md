# GitHub Collaboration #

## Configuración de colaboración ##

Como desarrollador solitario, probablemente se sienta cómodo trabajando con un repositorio local. En esta primera lección, vamos a hablar de repositorios remotos e interactuar con estos repositorios remotos. Digamos que tienes un amigo, la llamaremos Laura, y un día ustedes dos estuvieron juntos y le mostraron en qué han estado trabajando. Ella tenía algunas ideas sobre las características que podría contribuir al proyecto. Pero no quiere darle su computadora para que haga estos cambios, quiere que trabaje en su computadora. Y, no desea tener que esperar a que ella agregue estas características, quiere seguir trabajando en el proyecto y luego fusionarse en sus cambios cuando haya terminado. Entonces, ¿cómo podemos hacer eso? Bueno, déjame decirte que enviar por correo electrónico el proyecto de ida y vuelta sería una pesadilla de mantenimiento después de dos correos electrónicos. Ya estás rastreando tu proyecto con Git, así que lo usaremos para administrar todo. Así que Laura trabajará en el proyecto en una sucursal específica y cualquier cambio que haga lo agregará a esa sucursal. Mientras trabaja en su sucursal, trabajará en el proyecto, pero en su propia sucursal específica. Y luego puedes unir estas ramas cuando obtengas la rama de Farrin.

>>💡 Utilice siempre ramas de tema

Recuerde que es increíblemente útil realizar todas sus confirmaciones en ramas temáticas denominadas descriptivamente. Las ramas ayudan a aislar los cambios no relacionados entre sí. Por lo tanto, cuando colabora con otros desarrolladores, asegúrese de crear una nueva rama que tenga un nombre descriptivo que describa los cambios que contiene.

## ¿Qué es un repositorio remoto? ##

Git es un sistema de control de versiones distribuidas, lo que significa que no hay un repositorio principal de información. Cada desarrollador tiene una copia del repositorio. Para que pueda tener una copia del repositorio (que incluye los commits publicados y el historial de versiones) y su amigo también puede tener una copia del mismo repositorio. Cada repositorio tiene exactamente la misma información que los demás, no hay un único repositorio que sea el principal. Hasta este punto, probablemente solo ha estado trabajando localmente en un repositorio local. Un repositorio remoto es el mismo repositorio de Git como el suyo, pero existe en otro lugar.

Se puede acceder a las formas de acceder a los Remote Remotes de varias maneras: con una ruta URL a un sistema de archivos. Aunque es posible crear un repositorio remoto en su sistema de archivos, es muy raro que se use. Con mucho, la forma más común de acceder a un repositorio remoto es a través de una URL a un repositorio que está fuera de la web. La forma en que podemos interactuar y controlar un repositorio remoto es a través del comando remoto de Git:

``
$ git remote
``
