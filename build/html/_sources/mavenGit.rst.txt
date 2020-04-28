*Maven y control de versiones con Git*
======================================

Sería conveniente que llevasemos un control de las versioes de nuestro 
proyecto usando Git.
Esto podemos hacerlo desde el mismo terminal de IntelliJ, aunque también
podemos trabajar desde el terminal de nuestro ordenador o desde GitBash.

Uso de Git
----------

Lo primero que tenemos que hacer es iniciar un repositorio local en
nuestra máquina, esto lo hacemos con el comando ``git init``. El nuevo 
repositorio se creará en la carpeta que estemos usando como directorio 
de trabajo.

Una vez creado el repositorio, podemos ver en que estado está usando 
``git status``. En este momento, nos devolverá el siguiente mensaje:

.. code-block:: html

    On branch master
    No commits yet

    Untracked files:
    (use "git add <file>..." to include in what will be committed)

            .idea/

    nothing added to commit but untracked files present (use "git add" to
    track)

Esto nos indica que estamos en la rama principal y que todavía no hemos 
hecho ningún commit, además de indicarnos que tenemos archivos sin 
seguimiento de Git.

Para añadir estos archivos, usamos el commando ``git add`` (Podemos 
añadirlos todos usando ``git add --all``).
Nosotros vamos a añadir src y pom.xml

Una vez los hayamos añadido, tecleamos ``git commit -am "First com
mit"``. Podemos acceder al registro de cambios usando ``git log``.

Para subir los cambios al directorio remoto, debemos hacer un 
``git push origin master``.

Otros comandos de utilidad para trabajar con Git son:

Remote: Nos perimite gestionar repositorios remotos
Branch: Nospermite gestionar las ramas.



Uso de Maven
------------

Para trabajar con maven podemos hacerlo también desde el propio terminal
de IntelliJ o desde el teminal de nuestra máquina.

Los comando con los que vamos a trabajar principalmente son:

``mvn compile``, que compila nuestro proyecto (Valga la redundancia).
Después de compilar, podemos limpiar el proyecto antes de ejecutar los 
test usando ``mvn clean``. Los test pueden ejecutarse tecleando 
``mvn test``, que también compila nuestro código.

Por último, el comando ``mvn package`` compila nuestro código, ejecuta
los test y genera un jar.
