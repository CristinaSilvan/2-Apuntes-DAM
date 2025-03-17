1. Propiedades de Color y Fondo
    - color
        - Valores: nombre de color (red), código hexadecimal (#ff0000), rgb(255,0,0), hsl(0,100%,50%)

        - Función: Define el color del texto.

    - background-color
        - Valores: Igual que color

        - Función: Define el color de fondo del elemento.

    - background-image
        - Valores: url('imagen.jpg'), none

        - Función: Especifica una imagen de fondo.

    - background-size
        - Valores: auto, cover, contain, valores en px o %

        - Función: Define el tamaño de la imagen de fondo.

    - background-position
        - Valores: top, left, right, bottom, coordenadas (50% 50%, 10px 20px)

        - Función: Establece la posición de la imagen de fondo.

    - background-repeat
        - Valores: repeat, no-repeat, repeat-x, repeat-y

        - Función: Controla la repetición de la imagen de fondo.

---

2. Propiedades de Texto y Fuente
font-size
    Valores: small, medium, large, px, em, rem, %
    Función: Define el tamaño de la fuente.
font-family
    Valores: "Arial", "Times New Roman", "Verdana", sans-serif, serif
    Función: Especifica la tipografía del texto.
font-weight
    Valores: normal, bold, lighter, bolder, 100-900
    Función: Controla el grosor del texto.
font-style
    Valores: normal, italic, oblique
    Función: Define si el texto es normal o en cursiva.
text-align
    Valores: left, right, center, justify
    Función: Alinea el texto dentro de su contenedor.
text-decoration
    Valores: none, underline, overline, line-through
    Función: Añade decoraciones al texto.
letter-spacing
    Valores: normal, 1px, -1px
    Función: Ajusta el espacio entre letras.
line-height
    Valores: normal, 1.5, 150%, 20px
    Función: Define la altura de línea del texto.

---

3. Propiedades de Espaciado
margin
    Valores: auto, 10px, 1em, %
    Función: Define el espacio externo del elemento.
padding
    Valores: Igual que margin
    Función: Define el espacio interno del elemento.
border
    Valores: none, 1px solid black, 2px dashed red
    Función: Define el borde del elemento.
border-radius
    Valores: 0, 10px, 50%
    Función: Redondea las esquinas del elemento.

---

4. Propiedades de Dimensión
width
    Valores: auto, 100px, 50%, max-content
    Función: Define el ancho del elemento.
height
    Valores: Igual que width
    Función: Define la altura del elemento.
max-width / max-height
    Valores: none, 100px, 100%
    Función: Define el tamaño máximo de un elemento.
min-width / min-height
    Valores: Igual que max-width
    Función: Define el tamaño mínimo de un elemento.

---

5. Propiedades de Posicionamiento
position
    Valores: static, relative, absolute, fixed, sticky
    Función: Controla la posición de un elemento en la página.
top, right, bottom, left
    Valores: auto, 10px, 50%
    Función: Define la distancia de un elemento con respecto a su contenedor.
z-index
    Valores: auto, 1, 10, -1
    Función: Controla la superposición de elementos.

---

6. Propiedades de Visualización
display
    Valores: block, inline, inline-block, none, grid, table
    Función: Define cómo se muestra un elemento en la página.
visibility
    Valores: visible, hidden
    Función: Muestra u oculta un elemento sin afectar su espacio.
opacity
    Valores: 0 (transparente) a 1 (opaco)
    Función: Controla la transparencia del elemento.
overflow
    Valores: visible, hidden, scroll, auto
    Función: Controla el comportamiento del contenido cuando se desborda.

---

7. Propiedades de Cursor e Interacción
cursor
    Valores: default, pointer, move, text, wait
    Función: Cambia la apariencia del cursor.
pointer-events
    Valores: auto, none
    Función: Controla si el elemento puede recibir eventos del cursor.

---

8. Propiedades de Imágenes

- Dimensiones y Espaciado
    width → Ancho de la imagen.
    height → Alto de la imagen.
    max-width → Ancho máximo permitido.
    max-height → Alto máximo permitido.
    min-width → Ancho mínimo permitido.
    min-height → Alto mínimo permitido.
    aspect-ratio → Relación de aspecto de la imagen.
    object-fit → Controla cómo se ajusta la imagen dentro de su contenedor (fill, cover, contain, etc.).
    object-position → Posición de la imagen dentro del contenedor.
    padding → Espaciado interno.
    margin → Espaciado externo.

- Apariencia y Estilo
    border → Borde de la imagen.
    border-radius → Redondeo de esquinas.
    box-shadow → Sombra de la imagen.
    opacity → Transparencia.
    filter → Efectos visuales (blur, grayscale, brightness, etc.).
    mix-blend-mode → Mezcla de la imagen con el fondo.
    background → Fondo de la imagen.
    clip-path → Recorta la imagen en una forma específica.
    mask-image → Máscara para ocultar partes de la imagen.

- Posicionamiento y Alineación
    display → Cómo se comporta la imagen en el flujo del documento (block, inline-block, flex, etc.).
    position → Posicionamiento (relative, absolute, fixed, etc.).
    top, right, bottom, left → Desplazamientos si la imagen tiene position diferente de static.
    z-index → Orden de apilamiento.
    float → Flotado de la imagen a la izquierda o derecha.
    clear → Evita que elementos floten junto a la imagen.

- Transformaciones y Animaciones
    transform → Escalar, rotar, trasladar o inclinar la imagen.
    transition → Transiciones suaves entre estilos.
    animation → Animaciones de la imagen.

---

9. Propiedades de contenedores
    aspect-ratio → Relación de aspecto.

    background → Fondo del div (color, imagen, gradiente).

    background-color → Color de fondo.

    background-image → Imagen de fondo.

    background-size → Tamaño del fondo (cover, contain, etc.).

    background-position → Posición de la imagen de fondo.

    border → Borde del div.

    border-radius → Redondeo de esquinas.

    box-shadow → Sombra del div.

    opacity → Transparencia.

    filter → Efectos visuales (blur, grayscale, etc.).

    mix-blend-mode → Cómo se mezcla con el fondo.

    display → Cómo se comporta el div en el flujo del documento (block, inline-block, flex, grid, etc.).

    position → Posicionamiento (static, relative, absolute, fixed, sticky).

    top, right, bottom, left → Desplazamientos con position.

    z-index → Orden de apilamiento.

    float → Flotar el div a la izquierda o derecha.

    clear → Controla si otros elementos flotantes pueden situarse junto al div.

    overflow → Manejo del contenido que se sale del div (hidden, scroll, auto).

    visibility → Visibilidad (visible, hidden).
    
    white-space → controla cómo se manejan los espacios en blanco dentro de un elemento.

        Valor	Saltos de línea (\n)	Espacios adicionales	Ajuste de texto (wrapping)
        normal	✅ Se respetan	❌ Se eliminan extra	✅ Se ajusta
        nowrap	✅ Se respetan	❌ Se eliminan extra	❌ No se ajusta (scroll horizontal si es necesario)
        pre	✅ Se respetan	✅ Se mantienen todos	❌ No se ajusta
        pre-wrap	✅ Se respetan	✅ Se mantienen todos	✅ Se ajusta
        pre-line	✅ Se respetan	❌ Se eliminan extra	✅ Se ajusta

    - display: flex
        flex-direction → Dirección de los elementos (row, column, etc.).
        justify-content → Alineación horizontal.
        align-items → Alineación vertical.
        flex-wrap → Controla si los elementos se ajustan en varias líneas.

    - display: grid
        grid-template-columns → Columnas de la cuadrícula.
        grid-template-rows → Filas de la cuadrícula.
        gap → Espaciado entre elementos.

    - Diferencia entre block, inline e inline-block
    ¿Ocupa todo el ancho disponible?	¿Se puede poner junto a otros elementos en línea?	¿Se pueden definir width y height?
    block	✅ Sí	❌ No	✅ Sí
    inline	❌ No	✅ Sí	❌ No (solo respeta padding y margin horizontal)
    inline-block	❌ No	✅ Sí	✅ Sí

    ---

    🔹 ¿Cuándo usar cada uno?
    🔸 1. block (por defecto en div, p, section, etc.)
    Se usa cuando quieres que el elemento ocupe todo el ancho disponible y esté en su propia línea.
    Permite definir width y height.

    🔸 2. inline (por defecto en span, a, strong, etc.)
    Se usa cuando el elemento debe estar en línea con otros elementos.
    ❌ No permite definir width ni height, solo padding y margin en horizontal.


    🔸 3. inline-block (Mezcla de ambos)
    Funciona como inline, pero permite definir width y height.
    Útil cuando necesitas que los elementos estén en la misma línea pero con tamaño controlado.

    ---

    - Diferencia entre elementos en bloque e inline

    📌 Elementos en bloque (block)

    Ocupan todo el ancho disponible de su contenedor.
    Siempre comienzan en una nueva línea.
    Se usa cuando queremos que un elemento sea un contenedor estructural.
    Ejemplo: <div>, <p>, <h1>-<h6>, <section>, <article>, <ul>, <li>

    📌 Elementos en línea (inline)
    Solo ocupan el ancho necesario según su contenido.
    No generan un salto de línea.
    Se usa en elementos que forman parte del flujo del texto.
    Ejemplo: <span>, <a>, <strong>, <em>

    📌 inline-block;
    Similar a inline, pero permite definir width, height, padding, y margin.
    Se usa para elementos que deben estar en línea, pero con dimensiones personalizadas.

    ---

    Cuándo usar <div> y <span>
    📌 Usa <div> cuando necesitas un contenedor en bloque.
    Se usa para agrupar contenido estructuralmente.

    📌 Usa <span> cuando necesitas un contenedor en línea.
    Se usa cuando quieres aplicar estilos a una parte específica del texto sin afectar el flujo.

    > Tambien existe el display table, table-cell y float

    > Añadir vertical-align: middle;



    # otros

    white-space: nowrap; /* Evita el salto de línea */
    overflow: hidden; /* Oculta el texto sobrante */
    text-overflow: ellipsis; /* Muestra los "..." */

    .padre {
    display: table; /* Asegúrate de que el contenedor sea tipo tabla */
    border-spacing: 10px; /* Establece el espacio entre los elementos (filas y celdas) */
    }

    .hijo {
        display: table-cell; /* Hace que los divs se comporten como celdas de una tabla */
        padding: 10px; /* Opcional: espacio interno dentro de cada celda */
    }





---
---
---

# Propiedades decorativas

ul {
  list-style-type: none; /* Elimina los puntos de la lista */
}


a {
  color: inherit; /* Cambia el color a heredar el color del texto normal */
  text-decoration: none; /* Elimina el subrayado */
}

button {
  border: none; /* Elimina el borde */
  outline: none; /* Elimina el borde de enfoque */
}

text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);

---
---
---

Magnitudes: 
1. auto
Función: Permite que el navegador calcule automáticamente el tamaño del elemento en función de su contenido o contexto.
Si un div tiene width: auto;, su ancho se ajustará automáticamente al contenido o al espacio disponible dentro de su contenedor padre.
En margin: auto;, se usa para centrar un elemento dentro de su contenedor.

2. px (Píxeles)
Unidad absoluta que representa un número fijo de píxeles en pantalla.
El elemento tendrá exactamente 100 píxeles de ancho sin importar el tamaño de la pantalla o el contenedor.

3. % (Porcentaje)
Es una unidad relativa que se basa en el tamaño del contenedor padre.
Si el contenedor padre mide 800px, el elemento tendrá 800px de 100% de ancho.

4. em (Relativo al tamaño de la fuente)
Se basa en el tamaño de la fuente del elemento padre.
1em = tamaño de la fuente del padre
2em = el doble del tamaño del padre

5. rem (Relativo al tamaño de la raíz)
Similar a em, pero basado en la fuente del html en lugar del padre inmediato.

6. vh y vw (Relativo al tamaño de la ventana)
vh (Viewport Height): 1vh es el 1% de la altura de la ventana del navegador.
vw (Viewport Width): 1vw es el 1% del ancho de la ventana del navegador.

7. min-content, max-content, fit-content
min-content: El tamaño mínimo que puede tener un elemento sin que el contenido se corte.
max-content: El tamaño máximo basado en el contenido.
fit-content: Se ajusta automáticamente entre min-content y max-content.

