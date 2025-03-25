# Índice
- [Tema 1 (Repaso HTML y CSSCarpeta)](#tema-1-repaso-html-y-csscarpeta)
- [Tema 2 (Desarrollo de interfaces)](#tema-2-desarrollo-de-interfaces)
- [Tema 3 (Usabilidad)](#tema-3-usabilidad)
- [Tema 4 (Accesibilidad)](#tema-4-accesibilidad)
- [Tema 5 (JavaScript)](#tema-5-javascript)
- [Tema 6 (Árbol de Nodos)](#tema-6-árbol-de-nodos)

<br>

- [Cuestionario 1 (Concepto de Interface)](#cuestionario-1-concepto-de-interface)
- [Cuestionario 2 (Accesibilidad)](#cuestionario-2-accesibilidad)
- [Cuestionario 3 (Árbol de nodos)](#cuestionario-3-árbol-de-nodos)

<br>

- [Autoevaluación 1](#autoevaluación-1)
- [Autoevaluación 2](#autoevaluación-2)

---
---
---

# Tema 1 (Repaso HTML y CSSCarpeta)

[Volver al Índice](#índice)

---
---
---

# Tema 2 (Desarrollo de interfaces)

[Volver al Índice](#índice)

---
---
---

# Tema 3 (Usabilidad)

[Volver al Índice](#índice)

---
---
---

# Tema 4 (Accesibilidad)

[Volver al Índice](#índice)

---
---
---

# Tema 5 (JavaScript)

[Volver al Índice](#índice)

---
---
---

# Tema 6 (Árbol de Nodos)

## Acesso directo a nodos

Una vez se ha accedido al nodo, el siguiente paso consiste en acceder y/o modificar sus atributos y propiedades.

Desde el DOM, es posible acceder a todos los atributos HTML y todas las propiedades CSS de cualquier elemento de la página.

Los atributos HTML de los elementos, se transforman automáticamente en propiedades de los nodos.


- Ejemplo acceso a un atributo de un elemento HTML:
```
var enlace = document.getElementById("enlace");

alert(enlace.href);
```

```
<a id="enlace" href="http://www...com"> Enlace </a>
```

- Ejemplo acceso a una propiedad CSS:

```
var imagen = document.getElementById("imagen");
alert(imagen.style.margin);
```

```
<img id="imagen" style="margin:0; border:0;" src=logo.png />
```
Las propiedades CSS definidas en línea (dentro del atributo style) son accesibles directamente mediante **elemento.style**


- Si el nombre de una propiedad CSS, es compuesto, se transforma eliminando el guión y convirtiéndo el nombre a estilo **CamelCase**:
    - font-weight pasa a **fontWeight**
    - line-height pasa a **lineHeight**
    - border-top-style pasa a **borderTopStyle**
    - ...


```
var parrafo = document.getElementById("parrafo");

alert(parrafo.style.fontWeight);
```

```
<p id="parrafo" style="font-weight: bold;"> ... </p>
```

El único atributo HTML que no tiene el mismo nombre en el Dom, es el atributo **class**.
Como la palabra class está reservada en JavaScript, no es posible utilizarla para acceder al atributo class del elemento HTML. En su lugar, DOM utiliza el nombre **className**.

```
var parrafo = document.getElementsByClassName("resaltado");
```

```
<p class="resaltado">Este es un párrafo con clase "resaltado".</p>
<div class="resaltado">Este div también tiene la misma clase.</div>
```

Ejemplo de cómo cambiar la clase de un elemento:

```
<div id="miDiv" class="resaltado"></div>
```

```
document.getElementById("miDiv").className = "nuevoEstilo";
```

Ejemplo de cómo añadir/eliminar una clase a un elemento:

```
document.getElementById("miDiv").classList.add("otraClase");
```

```
document.getElementById("miDiv").classList.remove("resaltado");
```

## Eventos

Los elementos hacen posible que los usuarios transmitan información a los programas.
JavaScript define numerosos eventos que permiten una interacción completa entre el usuario y las aplicaciones web.

JavaScript permite asignar una función a cada uno de estos eventos, de esta forma se ejecuta una función asociada, conocidas como **event handlers** o **manejadores de eventos**.

El nombre de cada elemento se construye mediante eñ prejijo **On** seguido del nombre en inglés de la **acción asociada al evento** 

- Los eventos más utilizados en las aplicaciones web son:

    - onLoad: cuando ha cargado la página o activity por completo

    - onClick: el usuario ha clicado el ratón sobre el elemento

    - onMouseOver: el usuario ha posado el ratón encima del elemento

    - onMouseOut: el usuario ha movido el ratón fuera del área del elemento

    - onSubmit: el usuario ha pulsado el botón **enviar** sobre un formulario

    - onKeyDown, onKeyPress, onReset, ...

Algunos eventos tienen **acciones por defecto** que pueden ser sobreescritas

Cada elemento o etiqueta HTML define su propia lista de posibles eventos. Estos pueden tener un event handler particular o común con otros elementos, dependiendo de las funcionalidades que queramos definir.

## Método tradicional: Inline event handlers

No es recomendable definir los events handlers dentro del propio HTML ya que, aunque es una posibilidad, se complica fácilmente y dificulta la mantenibilidad:

```
function muestraMensaje(){
    alert('Gracias por pinchar');
}

```

```
<input type="button" value="Pinchame y verás" onclick="muestraMensaje()"/>
```

## Manejadores semánticos: Propiedades DOM

Esta técnica es una evolución del método de las funciones externas, ya que se basa en utilizar las propiedades DOM de los elementos HTML para asignar todas las funciones externas que se actúan como manejadores de eventos.

Separar el JavaScript del HTML es una buena práctica. Se logra asignando funciones directamente a las propiedades de eventos del DOM:

1. Asignar un identificafor único al elemento HTML

2. Crear una función de JavaScript encargada de manejar el evento

3. Asociar la función al event handler

```
function muestraMensaje(){
    alert("Gracias por pinchar");
}

document.getElementById("pinchable").onclick = muestraMensaje;
```

```
<input id="pinchable" type="button" value="Pinchame y verás"/>
```

## Event Listeners (Recomendado)

Es más flexible y recomendado, especialmente cuando necesitas asignar múltiples event handlers a un mismo evento

```
document.getElementById("pinchable").addEventListener("click", function() {
    alert("Gracias por pinchar");
});
```

[Volver al Índice](#índice)

---
---
---


> NOTA:
>
> JavaScript no tiene la potencia para conectarse con una Base de Datos relacional,
> pero si puede acceder a fuentes de datos externos menos complejas como archivos
> XML o JSON

---
---
---


# Cuestionario 1 (Concepto de Interface)

1. ¿Qué significa UI en el contexto del diseño de software?

        a. Unified Interaction


        b. User Interface


        c. Universal Integration

- La respuesta correcta es:
User Interface

---

2. ¿Cuál de los siguientes es un principio fundamental del diseño de UI?

        a. Complejidad


        b. Complejidad


        c. Consistencia

- La respuesta correcta es:
Consistencia

---

3. ¿Cuál de estos elementos no es una parte común de una interfaz de usuario gráfica (GUI)?

        a. Hilos


        b. Botones


        c. Enlaces

- La respuesta correcta es:
Hilos

---

4. ¿Qué herramienta se utiliza comúnmente para prototipar interfaces de usuario?

        a. Eclipse


        b. Adobe XD


        c. Git

- La respuesta correcta es:
Adobe XD

---

5. ¿Cuál de los siguientes es un componente clave de la experiencia de usuario (UX)?

        a. Rendimiento del hardware


        b. Complejidad del código


        c. Usabilidad

- La respuesta correcta es:
Usabilidad

---

6. ¿Qué aspecto de la UX se enfoca en cómo los usuarios perciben y responden a la interfaz visual de un producto?

        a. Diseño visual


        b. Arquitectura de la información


        c. Accesibilidad

- La respuesta correcta es:
Diseño visual

---

7. ¿Qué componente de la UX se refiere a la organización y estructura del contenido?

        a. Arquitectura de la información


        b. Diseño visual


        c. Diseño de interacción

- La respuesta correcta es:
Arquitectura de la información

---

8. ¿Qué componente de la UX se ocupa de cómo los usuarios interactúan con un producto?

        a. Diseño visual


        b. Usabilidad


        c. Diseño de interacción

- La respuesta correcta es:
Diseño de interacción

---

9. ¿Qué aspecto de la UX se enfoca en hacer que los productos sean utilizables por personas con diversas capacidades?

        a. Diseño visual


        b. Arquitectura de la información


        c. Accesibilidad

- La respuesta correcta es:
Accesibilidad

---

10. ¿Qué componente de la UX se encarga de investigar y entender las necesidades y comportamientos de los usuarios?

        a. Diseño visual


        b. Accesibilidad


        c. Investigación de usuarios

- La respuesta correcta es:
Investigación de usuarios

- [Volver al índice](#índice)

---
---
---

# Cuestionario 2 (Accesibilidad)

1. ¿Qué es la accesibilidad en el contexto de la web?

        a.
        La velocidad de carga de un sitio web


        b.
        La capacidad de acceder a un sitio web desde cualquier dispositivo.


        c.
        La práctica de hacer sitios web utilizables por personas con diversas discapacidades.

- La respuesta correcta es:
La práctica de hacer sitios web utilizables por personas con diversas discapacidades.

---

2. ¿Qué es WCAG?

        a. Un estándar de diseño gráfico.


        b. Un programa de certificación para desarrolladores web.


        c. Un conjunto de directrices para hacer contenido web más accesible.

- La respuesta correcta es:
Un conjunto de directrices para hacer contenido web más accesible.

---

3. ¿Cuál de los siguientes es un principio de las directrices de accesibilidad WCAG?

        a. Perceptible


        b. Costoso


        c. Atractivo

- La respuesta correcta es:
Perceptible

---

4. ¿Qué herramienta se puede usar para probar la accesibilidad de un sitio web?

        a. Google Analytics


        b. Sketch


        c. WAVE

- La respuesta correcta es:
WAVE

---

5. ¿Qué significa "contenido perceptible" en términos de accesibilidad?

        a. El contenido debe ser atractivo visualmente.


        b. El contenido debe ser presentado de manera que los usuarios puedan percibirlo.


        c. El contenido debe ser fácil de editar.

- La respuesta correcta es:
El contenido debe ser presentado de manera que los usuarios puedan percibirlo.

---

6. ¿Qué es un lector de pantalla?

        a. Un software que aumenta la velocidad de un sitio web


        b. Un hardware utilizado para mejorar la resolución de la pantalla.


        c. Un software que lee en voz alta el contenido de la pantalla para personas con discapacidades visuales.

- La respuesta correcta es:
Un software que lee en voz alta el contenido de la pantalla para personas con discapacidades visuales.

---

7. ¿Cuál es una práctica recomendada para mejorar la accesibilidad de las imágenes en un sitio web?

        a. Usar imágenes de alta resolución únicamente.


        b. Evitar el uso de imágenes


        c. Incluir texto alternativo (alt text) descriptivo para cada imagen.

- La respuesta correcta es:
Incluir texto alternativo (alt text) descriptivo para cada imagen.

---

8. ¿Qué significa "operable" en el contexto de la accesibilidad web?

        a. Los usuarios deben poder interactuar con todos los controles y elementos de la interfaz.


        b. El contenido debe ser visualmente atractivo.


        c. El sitio web debe ser fácil de programar.

- La respuesta correcta es:
Los usuarios deben poder interactuar con todos los controles y elementos de la interfaz.

---

9. ¿Cuál es una técnica para hacer que los formularios web sean más accesibles?

        a. Proveer etiquetas claras y descriptivas para todos los campos del formulario.


        b. Usar solo campos de texto.


        c. Hacer los formularios lo más cortos posible.

- La respuesta correcta es:
Proveer etiquetas claras y descriptivas para todos los campos del formulario.

---

10. ¿Qué se debe evitar para mejorar la accesibilidad del contenido multimedia en un sitio web?

        a. Incluir subtítulos para videos.


        b. Usar contenido multimedia sin descripciones alternativas.


        c. Proveer descripciones de audio.

- La respuesta correcta es:
Usar contenido multimedia sin descripciones alternativas.

- [Volver al índice](#índice)

---
---
---

# Cuestionario 3 (Árbol de nodos)

1. ¿Qué método se utiliza para seleccionar un único elemento por su ID en JavaScript?

        a. querySelector


        b. getElementsByTagName


        c. getElementById

- La respuesta correcta es:
getElementById

---

2. ¿Qué método devuelve una lista de elementos que coinciden con el nombre de la etiqueta especificada?

        a. getElementById


        b. getElementsByTagName


        c. querySelector

- La respuesta correcta es:
getElementsByTagName

---

3. ¿Qué método se utiliza para seleccionar el primer elemento que coincide con un selector CSS?

        a. querySelector


        b. getElementsByTagName


        c. querySelectorAll

- La respuesta correcta es:
querySelector

---

4. ¿Qué método devuelve todos los elementos que coinciden con un selector CSS?

        a. querySelectorAll


        b. getElementsByTagName


        c. querySelector

- La respuesta correcta es:
querySelectorAll

---

5. ¿Cuál es el tipo de valor que devuelve getElementById?

        a. Element


        b. NodeList


        c. HTMLCollection

- La respuesta correcta es:
Element

---

6. ¿Cuál de los siguientes métodos devuelve una NodeList en lugar de una HTMLCollection?

        a. getElementsByTagName


        b. getElementById


        c. querySelectorAll

- La respuesta correcta es:
querySelectorAll

---

7. ¿Cuál de los siguientes métodos permite seleccionar elementos utilizando un selector de clase?

        a. querySelector


        b. getElementsByTagName


        c. getElementById

- La respuesta correcta es:
querySelector

---

8. ¿Qué método es más adecuado para seleccionar todos los elementos de un tipo específico, como <div>?

        a. querySelector


        b. getElementById


        c. getElementsByTagName

- La respuesta correcta es:
getElementsByTagName

---

9. ¿Qué método se utiliza para seleccionar elementos que coinciden con un selector complejo, como "div.classname"?

        a. getElementsByTagName


        b. getElementById


        c. querySelectorAll

- La respuesta correcta es:
querySelectorAll

---

10. ¿Cuál es la diferencia principal entre querySelector y querySelectorAll?

        a. querySelector selecciona elementos por ID, mientras que querySelectorAll selecciona por clase.


        b. querySelector devuelve todos los elementos coincidentes, mientras que querySelectorAll devuelve solo el primero.


        c. querySelectorAll devuelve todos los elementos coincidentes, mientras que querySelector devuelve solo el primero.

- La respuesta correcta es:
querySelectorAll devuelve todos los elementos coincidentes, mientras que querySelector devuelve solo el primero.

- [Volver al índice](#índice)


---
---
---

<br>

# Autoevaluación 1

<br>

1. La interfaz gráfica de usuario se define como:
**Respuesta:** a. GUI

- La respuesta correcta es:

---

2. ¿Qué significan las siglas UX?
**Respuesta:** c. user experience

- La respuesta correcta es:

---

3. ¿Qué significan las siglas IPO?
**Respuesta:** c. Interacción persona Ordenador

- La respuesta correcta es:

---

4. ¿Qué es una interfaz alfanumérica?
**Respuesta:** d. Interfaces que usan comandos

- La respuesta correcta es:

---

5. JavaScript es un lenguaje orientado a objetos y eventos.
**Respuesta:** Verdadero

- La respuesta correcta es:

---

6. ¿Qué es una ruta amigable?
**Respuesta:** d. Una ruta que describe el contenido

- La respuesta correcta es:

---

7. ¿Cuántos principios son los principios de WGAG?
**Respuesta:** d. 4

- La respuesta correcta es:

---

8. Señala el método que pertenece al objeto document:
**Respuesta:** b. getElementById();

- La respuesta correcta es:

---

9. ¿Cómo se declara una variable en JavaScript?
**Respuesta:** b. Las dos anteriores son correctas

- La respuesta correcta es:

---

10. Las siglas UX significan User Experience o Experiencia de Usuario en español.
**Respuesta:** Verdadero

- La respuesta correcta es:

---

11. ¿Qué es un wireframe en diseño de interfaces?
**Respuesta:** d. Un esquema visual básico que muestra la estructura de una página web o aplicación

- La respuesta correcta es:

---

12. ¿Cuál es el propósito principal de un wireframe?
**Respuesta:** a. Organizar los elementos clave de una interfaz para enfocarse en la funcionalidad y disposición

- La respuesta correcta es:

---

13. ¿Qué NO suele incluir un wireframe?
**Respuesta:** c. Contenidos específicos y colores finales

- La respuesta correcta es:

---

14. ¿Qué herramienta podría usarse para crear wireframes?
**Respuesta:** c. Figma

- La respuesta correcta es:

---

15. ¿Cuál es la diferencia principal entre un wireframe y un prototipo?
**Respuesta:** a. Un wireframe es un esquema básico, mientras que un prototipo incluye interactividad y detalles visuales

- La respuesta correcta es:

---


16. ¿Qué es la accesibilidad web?
**Respuesta:** a. La práctica de hacer los sitios web utilizables por personas con discapacidades

- La respuesta correcta es:

---

17. ¿Cuál de las siguientes pautas es parte de las WCAG (Web Content Accessibility Guidelines)?
**Respuesta:** c. Proporcionar información textual alternativa para contenido no textual

- La respuesta correcta es:

---

18. ¿Qué etiqueta HTML se usa para mejorar la accesibilidad de imágenes?
**Respuesta:** a. <alt>

- La respuesta correcta es:

---

19. ¿Qué tecnología ayuda a los usuarios con discapacidad visual a navegar en un sitio web?
**Respuesta:** b. Screen readers (lectores de pantalla)

- La respuesta correcta es:

---

20. ¿Cuál de estas prácticas mejora la accesibilidad en un formulario web?

- La respuesta correcta es:
Asignar etiquetas `<label>` correctamente asociadas con los campos del formulario


<br>

[Volver al Índice](#índice)

<br>

---
---
---

# Autoevaluación 2

<br>

1. Un evento es:

a.
Una función


b.
Una acción que desencadena una instrucción

c.
Una instrucción

d.
Una acción

- La respuesta correcta es:

---

2. ¿Cómo se accede al primer hijo de un nodo en JavaScript?

a.
Utilizando el método setAtritutte()


b.
Utilizando el método getElementByTag

c.
Utilizando el método setAttribute

d.
Utilizando el método getElementById

- La respuesta correcta es:

---

3. ¿Cuál es el comando que se utiliza para crear un nodo?


a.
apendChild


b.
CreateElement


c.
CreateElements


d.
createNode

- La respuesta correcta es:

---

4. ¿Cuál de las siguientes opciones es la forma correcta de cambiar el texto de un elemento con el ID "titulo" usando getElementById()?

a.
document.getElementById('titulo').textContent = 'Nuevo Título';

b.
getelementById('titulo').textContent = 'Nuevo Título';


c.
document.getElementById('#titulo').innerHTML = 'Nuevo Título';

d.
document.C

- La respuesta correcta es:

---

5. ¿Qué permite el método SetAtributte?


a.
Modificar una propiedad position


b.
Las dos son correctas


c.
Modificar un parámetro html


d.
Modificar un parámetro img

- La respuesta correcta es:

---

6. ¿Qué propiedad se utiliza para acceder al contenido de un nodo de texto en JavaScript?

a.
textContent

b.
inerText


c.
innerText

d.
Ambas son correctas

- La respuesta correcta es:

---

7. ¿Qué representa un nodo en JavaScript y DOM?

a.
Una operación matemática. invocamos TOGGLECLASS(X), entonces a ese elemento se le añadirá la clase

b.
Una entidad en la estructura jerárquica de un documento HTML

c.
Un elemento de bloque


d.
Una operación matemática

- La respuesta correcta es:

---

8. Dado el siguiente código, ¿que falta?function casillas(){
if(document.miformulario.__________.checked==true)
{alert("La edad seleccionada es: " + document.miformulario.edad[0].value)}
else{ if(document.miformulario.edad[1].checked==true) { alert("La edad seleccionada es: " + document.miformulario.edad[1].value) }
else { if(document.miformulario.edad[2].checked==true) { alert("La edad seleccionada es:" + document.miformulario.edad[2].value) }
else { alert("La edad seleccionada es:" + document.miformulario.edad[3].value ) } }}}

a.
edad[-1]


b.
edad[1]

c.
edad[0]

d.
edad

- La respuesta correcta es:

---

9. En el siguiente bloque de código, ¿que valor tiene i, cuando se sale del bucle?for(i=0;i<array.length;i++){if(parseInt(array[i])>mayor) mayor=array[i];}

a.
j tiene que ser menor que la longitud del array


b.
i tiene que ser mayor que la longitud del array

c.
i tiene que ser igual que la longitud del array

d.
i tiene que ser menor que la longitud del array

- La respuesta correcta es:

---

10. ¿Cómo se puede cambiar el contenido de un nodo de texto en JavaScript?

a.
node.textContent = "Nuevo texto"

b.
nodetextContent = "Nuevo texto"


c.
node.text = "Nuevo texto";

d.
node.textContent = "Nuevo texto";

- La respuesta correcta es:

---

11. JavaScript es un lenguaje:

a.
Es un lenguaje independiente

b.
Es un lenguaje de programación para trabajar con eventos

c.
Es un lenguaje ensamblador

d.
Es un lenguaje compilado

- La respuesta correcta es:

---

12. Con el método setAtribute, ¿Qué tipos de atributos se pueden modificar?

a.
Todos los atributos html

b.
Solo atributos de tipo caja en css


c.
Todos los atributos css

d.
Solo atributos de posicion

- La respuesta correcta es:

---

13. ¿Qué tipos de datos se pueden almacenar en un Array?


a.
Solamente de tipo numérico


b.
Solamente de tipo texto


c.
De diferente naturaleza


d.
Solamente de tipo boolean

- La respuesta correcta es:

---

14. Si no hay ninguna opción seleccionada en un elemento de tipo select, ¿qué valor tendrá selectedIndex?

a.
0

b.
-1

c.
-2


d.
1

- La respuesta correcta es:

---

15. Señala el método que pertenece al objeto document:

a.
Las respuestas anteriores son correctas!!

b.
getID();


c.
alert()

d.
getElementById();

- La respuesta correcta es:

---

16. ¿Qué significan las siglas DCU?

a.
Definición de patrones de accesibilidad

b.
Diseño centrado en el usuario

c.
Definición de patrones de usabilidad


d.
Diseño Centrado en el código

e.
Definición de patrones de usabilidad

- La respuesta correcta es:

---

17. ¿Qué devuelve el método document.getElementById() si no encuentra ningún elemento con el ID especificado?

a.
Una cadena vacía ""

b.
null

c.
undefined

d.
Error

- La respuesta correcta es:

---

18. En JavaScript, ¿cómo se accede a una propiedad CSS de un elemento?

a.
Utilizando documentById() y la propiedad style


b.
Utilizando document.getElmentById() y la propiedad style

c.
Utilizando documentById() y el método setAtribute

d.
Utilizando documentById()

- La respuesta correcta es:

---

19. ¿Cómo puedes cambiar la opción seleccionada de un elemento de tipo select a la tercera opción utilizando selectedIndex?

a.
selectElement.selectedIndex = 2;

b.
selectElement.selectedIndex = '2';

c.
selectElement.selectedIndex = 4;


d.
selectElement.selectedIndex = 3;

- La respuesta correcta es:

---

20. ¿Cuál de las siguientes opciones se utiliza para crear un nuevo elemento en JavaScript?

a.
createText

b.
removeChild()


c.
AppendChild()

d.
createElement()

- La respuesta correcta es:


<br>

[Volver al Índice](#índice)

<br>

---
---
---