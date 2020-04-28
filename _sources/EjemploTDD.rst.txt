*Ejemplo de TDD*
================

Una vez preparado el entorno, ya podemos empezar a programar.

Como ya hemos dicho anteriormente, vamos a aplicar el TDD a un pequeño programa 
que nos devuelva el factorial de un número. Para ello, vamos plantear distintos
casos de prueba:
    1. El factorial de 0.
    2. El factorial de 1.
    3. El factorial de 2.
    4. El factorial de 4.
    5. El factorial de un número negativo.


Una vez planteados nuestros casos de prueba, vamos a desarrollar nuestro 
proyecto en diferentes fases:

    1. Un solo caso básico.
    2. Más de un caso.
    3. Caso general



Un solo caso básico
-------------------

El primer caso que vamos a ver va a ser que la prueba de que el factorial 
de 0 devuelva un fallo en JUnit.

Para ello tenemos escribir el siguiente código:

Clase Factorial
^^^^^^^^^^^^^^^

.. code-block:: java

    package org.example;
 
    /**
    *Devolvemos 0 por defecto
    */
    public class Factorial
    {

        public long compute(long value) {
            return 0;
        }
    }

Clase FactorialTest
^^^^^^^^^^^^^^^^^^^

.. code-block:: java

    package org.example;

    import org.junit.Test;

    import static org.junit.Assert.*;

    public class FactorialTest {

        @Test
        public void shouldFactorialOf0Return1(){
            Factorial factorial = new Factorial();

            long expectedValue=1;
            long obtainedValue = factorial.compute(0);

            assertEquals(expectedValue,obtainedValue);
        }
    }

Cuando ejecutemos como JUnit test, debería aparecer el siguiene mensaje:

.. figure:: /image/ErrorJUnit.jpg

Esto ocurre porque el valor esperado y el real no coinciden, por lo que 
nuestra prueba falla.

.. note::

    Si clicamos en el error, este nos redirige a la parte del codigo que
    ha hecho que nuestro test falle y no explica porqué.

Esto nos indica que nuestro programa no está contemplando el caso de 
prueba, por lo que tendremos que modificar nuestro código para que si 
lo haga (Es decir,tendremos que modificar el método compute para que devuelva 
el valor correcto).

Clase Factorial
^^^^^^^^^^^^^^^

.. code-block:: java

    package org.example;
 
    /**
    *Devolvemos 0 por defecto
    */
    public class Factorial
    {

        public long compute(long value) {
            return 1;
        }
    }

Cuando ejecutemos como JUnit test, debería aparecer el siguiene mensaje:

.. figure:: /image/SuccessJUnit.jpg

Esto nos indica que nuestra prueba ha sido un éxito.

Más de un caso
--------------

Vamos a ampliar nuestro código para que nos devuelva también el factorial
de 1.

Clase Factorial
^^^^^^^^^^^^^^^

.. code-block:: java

    package org.example;
 
    /**
    *   En este caso no tenemos que cambiar el valor que devuelve la 
    *   función, ya que !0 y !1 son 1.
    */
    public class Factorial
    {
        public long compute(long value) {
            return 1;
        }
    }

Clase FactorialTest
^^^^^^^^^^^^^^^^^^^

Modificamos la clase FactorialTest para poder ejecutar la prueba del 
factorial de 1.

.. code-block:: java

    package org.example;

    import org.junit.Test;

    import static org.junit.Assert.*;

    public class FactorialTest {

        @Test
        public void shouldFactorialOf0Return1(){
            Factorial factorial = new Factorial();

            long expectedValue=1;
            long obtainedValue = factorial.compute(0);

            assertEquals(expectedValue,obtainedValue);
        }

        @Test
        public void shouldFactorialOf1Return1(){
            Factorial factorial = new Factorial();

            long expectedValue=1;
            long obtainedValue=factorial.compute(1);

            assertEquals(expectedValue,obtainedValue);
        }

    }
    
Cuando ejecutemos shouldFactorialOf1Return1() se nos mostrará un mensaje 
éxito por pantalla, al igual que en el caso anterior.

.. code-block:: java

    public void shouldFactorialOf2Return2(){
        Factorial factorial = new Factorial();

        long expectedValue=2;
        long obtainedValue=factorial.compute(1);

        assertEquals(expectedValue,obtainedValue);
    }

Si ejecutamos esta prueba nos dará un fallo, ya que con el código que 
tenmos ahora mismo en nuestra función no devuelve el factorial de 2, por
lo que nuestro siguiente paso será modificar la función compute de la 
clase Factorial.


.. code-block:: java

   package org.example;

   public class Factorial
   {
   	public long compute(long value) {
	    long result;
	if(value==0 || value==1){
	    result=1;
	}else {
	    result = 2;
	}
	return result;
       }
    }	

Si volvemos a ejecutar a prueba debe devolver un mensaje de éxito.

Caso general
------------

Llegados a este punto, ejecutar pruebas con cuarquier otro número nos
devolvería un fallo, ya que no hemos contemplado ningún caso más a parte
del 0,el 1 y el 2, por lo que debemos implementar una función que sirva 
para el caso general.

Clase FactorialTest
^^^^^^^^^^^^^^^^^^^

.. code-block:: java

    package org.example;

    public class Factorial
    {
        public long compute(long value) {
	    long result;
	    if(value==0 || value==1){
	         result=1;
	    }else {
	         result = value*compute((value-1));
	    }
	    return result;
        }
    }

Clase FactorialTest
^^^^^^^^^^^^^^^^^^^

Como hemos eliminado la rama del if que correspondía a value==2, tendremos
que volver a ejecutar el test ``shouldFactorialOf2Return2()`` para comprobar
que no hemos introducido un nuevo fallo en el código que no estuviese antes.

.. code-block:: java

    package org.example;

    import org.junit.Test;

    import static org.junit.Assert.*;

    public class FactorialTest {

        @Test
        public void shouldFactorialOf0Return1(){
            Factorial factorial = new Factorial();

            long expectedValue=1;
            long obtainedValue = factorial.compute(0);

            assertEquals(expectedValue,obtainedValue);
        }

        @Test
        public void shouldFactorialOf1Return1(){
            Factorial factorial = new Factorial();

            long expectedValue=1;
            long obtainedValue=factorial.compute(1);

            assertEquals(expectedValue,obtainedValue);
        }

        @Test
        public void shouldFactorialOf2Return2(){
            Factorial factorial = new Factorial();

            long expectedValue=2;
            long obtainedValue=factorial.compute(1);

            assertEquals(expectedValue,obtainedValue);
        }

        @Test
        public void shouldFactorialOf4Return24(){
            Factorial factorial = new Factorial();

            long expectedValue=24;
            long obtainedValue=factorial.compute(4);

            assertEquals(expectedValue,obtainedValue);
        }

    }

Si queremos hacer nuestro caso aún más general, deberíamos contemplar 
que ocurriría si queremos calcular el factorial de un número negativo,
ya que ahora mismo entraría por la rama del else:

Clase FactorialTest
^^^^^^^^^^^^^^^^^^^

.. code-block:: java

    package org.example;

    public class Factorial
    {
        public long compute(long value) {
            long result;
            if (value<0){
                throw new RuntimeException("Negative number:"+value);
            }else if(value==0 || value==1){
                result=1;
            }else {
                result = value*compute((value-1));
            }
            return result;
        }
    }

En este caso, queremos que si el número es negativo el sistema lance
una excepción.

Podemos comprobar que nuestro código funciona con añadiendo una nueva 
prueba a FactorialTest:

.. code-block:: java

    package org.example;

    import org.junit.Test;
    import org.junit.jupiter.api.BeforeEach;

    import static org.junit.jupiter.api.Assertions.*;

    public class FactorialTest {
    
        private Factorial factorial;

        @BeforeEach
        public void setUp(){
            factorial=new Factorial();
        }
        @Test
        public void shouldFactorialOf0Return1(){
            long expectedValue=1;
            long obtainedValue = factorial.compute(0);

            assertEquals(expectedValue,obtainedValue);
        }
        @Test
        public void shouldFactorialOf1Return1(){
            long expectedValue=1;
            long obtainedValue=factorial.compute(1);

            assertEquals(expectedValue,obtainedValue);
        }
        @Test
        public void shouldFactorialOf2Return2(){
            long expectedValue=2;
            long obtainedValue=factorial.compute(2);

            assertEquals(expectedValue,obtainedValue);
        }
        @Test
        public void shouldThrowException(){
        assertThrows(RuntimeException.class, () -> factorial.compute(-1));
        }
    }

Donde ``shouldThrowException()`` comprueba si se está lanzando la 
excepción.

.. note::

    Como añadido hemos creado una variable ``factorial`` que se inicializa
    antes de cada test (``@BeforeEach``) para ahorrar código.           

Si ejecutamos la clase FactorialTest nos devolverá el siguiente mensaje:

.. figure:: /image/successFinal.jpg

Con lo que habremos concluido el desarrollo de nuestro programa con éxito.
