# Índice

- [Introducción](#introducción)
- [Estructura](#estructura)
- [Softwares e instalación](#softwares-e-instalación)
- [Visualizar](#visualizar)
- [Server de pruebas](#server-de-pruebas)
- [Comentarios](#comentarios)
- [Variables PHP](#variables-php)
- [Print y Echo](#print-y-echo)
- [Concatenar](#concatenar)
- [Imprimir literales](#imprimir-literales)
- [Flujo de ejecución](#flujo-de-ejecución)
- [Funciones](#funciones)
- [Bloques de PHP](#bloques-de-php)
- [Include](#include)
- [Require](#require)
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()

# Introducción

`PHP (Hypertext Preprocessor)` es un lenguaje de programación de código abierto, ampliamente utilizado para el desarrollo web. Se ejecuta en el servidor y permite crear sitios dinámicos e interactivos.

Características de PHP:

- **Lenguaje del lado del servidor**: Se ejecuta en el servidor y genera contenido HTML dinámico antes de enviarlo al navegador.

- **Fácil de aprender**: Tiene una sintaxis similar a `C` y `JavaScript`, lo que facilita su aprendizaje.

- **Compatibilidad con bases de datos**: Se integra con `MySQL`, `PostgreSQL`, `SQLite`, y otros sistemas de bases de datos.

- **Código embebido en HTML**: Puede mezclarse con código `HTML`, facilitando la creación de páginas dinámicas.

- **Multiplataforma**: Funciona en `Windows`, `Linux` y `macOS` sin problemas.

- **Extensible**: Permite el uso de bibliotecas y frameworks como `Laravel`, `Symfony` y `CodeIgniter`.

> [Volver al Índice](#índice)

# Estructura

El código `PHP` se encuentra en el body del `HTML`:

```
<html>
    <head>
    </head>

    <body>

        <?php

        ?>

    </body>
</html>
```

> [Volver al Índice](#índice)

# Softwares e instalación

> [Volver al Índice](#índice)

# Visualizar

> [Volver al Índice](#índice)

# Server de pruebas

Desde dreamweaver, pulsando f12, abre el navegador sin necesidad de escribir la url localhost. Siempre y cuando los servidores estén arrancados.

> [Volver al Índice](#índice)

# Comentarios

```
<?php

    //Esto es un comentario.

?>
```

```
<?php

    /*
    
    Esto es un comentario.

    */

?>
```

> [Volver al Índice](#índice)

# Variables PHP

Declaración:

```
$nombre = "Cristina";

$edad = 28;
```

Ámbito:

- Local: 
    Se declara dentro de una función. visible y accesible desde dentro de esta.

- Global:
    En este lenguaje, puede ser declarada en cualquier parte del código (dentro o fuera de una función).
    Visible y accesible desde cualquier parte del código.

- Super global:
    Declarada como Array desde la versión `PHP 4.0`. Visible y accesible desde fuera del archivo `PHP`. 
    Por ejemplo, útil para el envío de datos de formularios entre archivos.

> [Volver al Índice](#índice)

# Print y Echo

`print` es una función que siempre devuelve el valor `1` tras su finalización, debido a que debe hacer varios procesos internos.

```
print "Este es el nombre de usuario: " . $nombre;
```

`echo` es una expresión que toma poco tiempo en imprimir, por lo que es conveniente para programas grandes para no ocupar muchos recursos.

```
echo $nombre, $edad;
```

> [Volver al Índice](#índice)

# Concatenar

```
print "El nombre del usuario es " . $nombre;
```

`Print` permite imprimir las variables dentro de la propia cadena sin tener que formatear la salida:

```
print "El nombre del usuario es $nombre";
```

> [Volver al Índice](#índice)

# Imprimir literales

```
print 'Esto se imprime de forma literal $nombre';
```

> [Volver al Índice](#índice)


# Flujo de ejecución

Es secuencial, por lo que dependiendo de dónde estructuremos el php dentro del html, se ejecutará antes o después de otros elementos.

> [Volver al Índice](#índice)

# Funciones

```
//Declaración
function nombreFuncion (){
    //Código
}


//Llamada a la función
nombreFuncion ();
```

> [Volver al Índice](#índice)

# Bloques de PHP

Dentro del documento `HTML`, puede haber varios bloques `PHP`. 
Por ejemplo, en un bloque podemos tener las declaraciones de las funciones, mientras que en el siguiente bloque, realizar las llamadas y el resto del código:

```
<html>
    <head>

    </head>

    <body>

        <?php
            funcion nombreFuncion (){
                //Código
            }
        ?>


        <?php
            nombreFuncion ();
        ?>

    </body>
</html>
```

# Include

Podemos importar archivos `PHP` externos para utilizarlos dentro del documento `HTML`.
Por ejemplo, teniendo el archivo `funcionalidades.php` siguiente:

```
<?php
            funcion nombreFuncion (){
                //Código
            }
        ?>
```

Y teniendo el archivo `index.html` siguiente:

```
<html>
    <head>

    </head>

    <body>

        <?php
            
        ?>

    </body>
</html>
```

Podemos importar el contenido del archivo `funcionalidades.php` para ser utilizado dentro del `index.html` de la siguiente forma:

```
<html>
    <head>

    </head>

    <body>

        <?php

            include ("funcionalidades.php"); //Debemos proporcionar la URL del archivo

            //Ahora podemos invocar las funciones desarrolladas dentro del archivo importado
            nombreFuncion();
        ?>

    </body>
</html>
```

> [Volver al Índice](#índice)

# Require

Parecido a la función `include`, con la diferencia de que, si no se encontrase el archivo especificado en la URL especificada, el flujo del programa se detendría por completo. Proporcionando un error en ejecució fatal:

```
<html>
    <head>

    </head>

    <body>

        <?php

            require ("???.php"); //URL errónea

            //El programa se detiene abruptamente
        ?>

    </body>
</html>
```

El archivo es REQUERIDO para la ejecución del programa.

> [Volver al Índice](#índice)

# Conflicto entre variables

Debido a que al importar archivos externos, puede haber conflicto entre variables que tengan el mismo identificador o sobreescritura de valores que produzcan errores inesperados y difíciles de detectar.

`PHP` soluciona este problema cambiando el ámbito de las variables mediante el modificador `global`:

```
<?php

    $nombre = "Cristina";



    function imprimeNombre (){
        
        global $nombre; //Modificador de ámbito

        $nombre = "El nombre es " . $nombre;

    }

    imprimeNombre(); //Se imprimirá el texto "El nombre es Cristina"
?>
```

NOTA: Debido a razones de seguridad, no funcionaría de la siguiente manera:

```
<?php

    global $nombre;  //Modificador de ámbito

    $nombre = "Cristina";



    function imprimeNombre (){

        $nombre = "El nombre es " . $nombre;

    }

    imprimeNombre(); //ERROR
?>
```

El modificador `global` solo puede ser usado dentro de funciones.

> [Volver al Índice](#índice)


> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)

# 

> [Volver al Índice](#índice)