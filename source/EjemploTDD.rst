*Ejemplo de TDD*
================

Una vez preparado el entorno, ya podemos empezar a programar.

Como ya hemos dicho anteriormente, vamos a aplicar el TDD a un pequeño programa 
que nos devuelva el factorial de un número. vamos a desarrollar nuestro proyecto 
en diferentes fases:

    1. Un solo caso básico.
    2. Más de un caso.
    3. Caso general

.. code-block:: language
    package org.example;

    /**
    * Hello world!
    *
    */
    public class Factorial
    {

        public long compute(long value) {
            long result=0;
            if(value==0 || value==1){
                result=1;
            }else {
                result = value*compute(value-1);
            }
            return result;
        }
    }
