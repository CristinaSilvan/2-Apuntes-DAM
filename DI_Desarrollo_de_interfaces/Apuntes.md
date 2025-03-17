# Índice
- [Tema 1 (Repaso HTML y CSSCarpeta)](#tema-1-repaso-html-y-csscarpeta)
- [Tema 2 (Desarrollo de interfaces)](#tema-2-desarrollo-de-interfaces)
- [Tema 3 (Usabilidad)](#tema-3-usabilidad)
- [Tema 4 (Accesibilidad)](#tema-4-accesibilidad)
- [Tema 5 (JavaScript)](#tema-5-javascript)
- [Tema 6 (Árbol de Nodos)](#tema-6-árbol-de-nodos)

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