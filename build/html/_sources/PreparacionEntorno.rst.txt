*Preparación del entorno*
==========================

Una vez instalado en nuestro sistema:

    * Java 13 (versión de Java superior a 8)
    * Maven (version 3.6.1) 
    * IntelliJ IDEA

Podemos empezar a crear nuestro proyecto. 

Creación del proyecto FACTORIAL
--------------------------------

Vamos a resumir una serie de pasos a seguir: 

    1. Abrimos **IntelliJ IDEA**
    2. Creamos un nuevo proyecto 
    3. JDK de **JAVA** y arquetipo de **MAVEN** 
    4. Guardamos el proyecto en carpeta deseada

Una vez instalados en el entorno de IntelliJ IDEA y seleccionado crear un proyecto nuevo, tendremos que 
especificar la versión de Java a emplear y seleccionar el arquetipo de Maven que corresponde, señalados en la siguiente imagen.

.. figure:: /image/creacion1.jpg

Luego le damos el nombre al proyecto (en este caso *FACTORIAL(TDD)*) y lo situamos en la carpeta deseada. 
Nos aparecerá una ventana con la versión de Maven importada y solo tendremos que finalizar. 

.. figure:: /image/creacion2.jpg

Una vez realizado estos pasos, obtendremos un proyecto con la estructura ya definida y el fichero *pom.xml* en el 
que encontramos las dependencias necesarias de Maven.

.. figure:: /image/creacion3.jpg

JUnit Jupiter 5.6.2
---------------------

Nos fijamos en las dependencias de JUnit en el fichero pom.xml y observamos que la versión no corresponde con la 5.

.. figure:: /image/creacion4.jpg

Para la modificación de esta dependencia buscamos en el repositorio de Maven el código html que corresponde para 
la version de *JUnit.Jupiter versión 5.6.2*.

.. code-block:: HTML

    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.6.2</version> 
        <scope>test</scope>
    </dependency>
       
Este es el código que corresponde a la versión de JUnit a utilizar, y que tendríamos que modificar en las
dependencias de pom.xml. Una vez realizada esta modificación, probamos el test de prueba que el proyecto 
ha generado por defecto. Si nos da error, podemos volver a importar JUnit en a clase *AppTest*, seleccionando
el JUnit que hemos añadido en las dependencias. 
Una vez que ejecutamos el test sin errores, ya podemos adecuar el proyecto para nuestros test y nuestra clase FACTORIAL
a implementar. 

.. figure:: /image/creacion5.jpg

Por últirmo, creamos los nuevos paquetes y las clases *Factorial* y *FactorialTest*, donde trabajaremos en la aplicación 
de TDD a través de las pruebas de JUnit. 

.. topic:: Organización de nuestra carpeta **src**:

    * main
        - java
            + **org.FACTORIAL.TDD**
                - *Factorial*

    * test
        - java
            + **org.FACTORIAL.TDD**
                - *FactorialTest*









        
           
