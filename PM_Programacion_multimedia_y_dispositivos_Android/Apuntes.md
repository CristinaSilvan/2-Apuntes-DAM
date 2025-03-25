# Índice

<br>

- [Análisis de tecnologías para aplicaciones en dispositivos móviles]()
- [Instalación de Android Studio]()
- [Componentes Android Studio]()
- [Elementos tipo texto]()
- [Casillas en Android Studio]()
- [Switch]()
- [Utilizar imágenes](#utilizar-imágenes)
- [Listas de elementos](#lista-de-elementos)

<br>

- [Autoevaluación 1](#autoevaluación-1)
- [Autoevaluación 2](#autoevaluación-2)

<br>

# Utilizar imágenes

1. ¿Cuál es el propósito principal de un ImageView en Android?


        a. Mostrar texto


        b. Mostrar imágenes


        c. Mostrar botones

La respuesta correcta es:
Mostrar imágenes

---

2. ¿Cuál es el propósito principal de un ImageButton en Android?


        a. Mostrar texto


        b. Mostrar un botón de imagen que puede ser pulsado


        c. Mostrar un campo de entrada de texto

La respuesta correcta es:
Mostrar un botón de imagen que puede ser pulsado

---

3. ¿Qué atributo XML se utiliza para establecer la imagen de un ImageView?


        a. android:drawable


        b. android:image


        c. android:src

La respuesta correcta es:
android:src

- Explicación:
    - Este atributo permite especificar una imagen que será mostrada en el ImageView, ya sea desde los recursos del proyecto o desde una URL.

- Respuestas erróneas:
    - android:drawable se usa en otros contextos, por ejemplo, para establecer imágenes en un fondo o en un botón, pero no es válido para un ImageView.

    - android:image no existe en la documentación oficial de Android.

---

4. ¿Qué atributo XML se utiliza para establecer la imagen de un ImageButton?


        a. android:drawable


        b. android:image


        c. android:src

La respuesta correcta es:
android:src

- Explicación:
    - Al igual que en un ImageView, el atributo android:src se utiliza en un ImageButton para establecer la imagen que se mostrará.

---

5. ¿Qué método se utiliza para cambiar la imagen de un ImageView programáticamente?


        a. setDrawable()


        b. setImageResource()


        c. setImage()

La respuesta correcta es:
setImageResource()

- Explicación:
    - El método setImageResource(int resId) se utiliza para cambiar la imagen de un ImageView programáticamente en Android. Este método permite establecer una imagen utilizando el identificador del recurso (resource ID) de la imagen.

```
ImageView imageView = findViewById(R.id.miImageView);
imageView.setImageResource(R.drawable.mi_imagen);
```

- Respuestas erróneas:
    - setImageBitmap(Bitmap bitmap): Para usar un objeto de tipo Bitmap.

    - setImageURI(Uri uri): Para cargar una imagen desde una URI.

---

6. ¿Qué método se utiliza para cambiar la imagen de un ImageButton programáticamente?


        a. setImageResource()


        b. setImage()


        c. setDrawable()

La respuesta correcta:
setImageResource()

---

7. ¿Cuál es la diferencia principal entre ImageView e ImageButton?


        a. No hay diferencia, ambos se usan para mostrar imágenes


        b. ImageView se usa para mostrar imágenes estáticas, mientras que ImageButton es un botón con imagen que puede ser pulsado.


        c. ImageView se usa para mostrar botones, mientras que ImageButton se usa para mostrar texto.

La respuesta correcta:
ImageView se usa para mostrar imágenes estáticas, mientras que ImageButton es un botón con imagen que puede ser pulsado.

---

8. ¿Qué atributo XML se utiliza para ajustar el tamaño de la imagen dentro de un ImageView?


        a. android:adjustViewBounds


        b. android:scaleType


        c. android:resize

La respuesta correcta es:
android:scaleType

- Explicación:
    - El atributo android:scaleType se utiliza para especificar cómo se ajustará el tamaño de la imagen dentro de un ImageView. Define cómo la imagen debe escalarse o posicionarse para encajar en los límites del ImageView.

        ```
        Valores comunes de android:scaleType:
        
        1. fitCenter: Escala la imagen para que encaje completamente en el ImageView, manteniendo la proporción, y la centra.

        2. centerCrop: Escala la imagen para llenar completamente el espacio del ImageView, recortando las partes sobrantes si es necesario.

        3. centerInside: Escala la imagen para que encaje completamente dentro del ImageView, sin recortes.

        4. fitXY: Escala la imagen para que encaje exactamente en las dimensiones del ImageView, distorsionándola si es necesario.

        5. matrix: Permite aplicar transformaciones personalizadas a la imagen.
        ```

- Respuestas erróneas:
    - android:adjustViewBounds: se utiliza para ajustar los límites del ImageView de acuerdo con las dimensiones de la imagen, pero no ajusta directamente el tamaño de la imagen en sí. Cuando se establece en true, android:adjustViewBounds permite que el ImageView mantenga las proporciones de la imagen cuando se cambian los tamaños del ImageView (siendo especialmente útil cuando el ImageView tiene un ancho o alto fijo).

    - android:resize: Este atributo no existe en la API de Android. No hay un atributo llamado android:resize en el contexto de ImageView

---

9. ¿Qué valor del atributo android:scaleType se usa para escalar la imagen a lo largo del borde más grande y mantener la relación de aspecto?


        a. fitCenter


        b. centerCrop


        c. fitXY

La respuesta correcta es:
centerCrop

- Explicación: 
    - El valor centerCrop del atributo android:scaleType se utiliza para escalar la imagen de manera que llene completamente el espacio del ImageView a lo largo del borde más grande, manteniendo la relación de aspecto. La imagen se escala proporcionalmente hasta llenar el área del ImageView. Si las dimensiones de la imagen no coinciden con las del ImageView, algunas partes de la imagen pueden quedar fuera del área visible (recorte).

- Respuestas erróneas:
    - fitCenter: Escala la imagen para que encaje completamente dentro del ImageView, sin recortes, manteniendo la proporción.

    - fitXY: Escala la imagen para que se ajuste exactamente a las dimensiones del ImageView, lo que puede distorsionar la imagen.

---

10. ¿Cuál es la diferencia entre los atributos android:src y android:background en ImageView y ImageButton?


        a. android:src establece la imagen principal mientras que android:background establece el fondo detrás de la imagen


        b. No hay diferencia, ambos establecen la imagen principal.


        c. android:src establece el texto y android:background establece la imagen

La respuesta correcta es:
android:src establece la imagen principal mientras que android:background establece el fondo detrás de la imagen

# Lista de Elementos

1. ¿Qué clase se utiliza para crear una lista simple de elementos en Android?


a.
RecyclerView


b.
GridView


c.
ListView

---

2. ¿Cuál es el adaptador más comúnmente utilizado con ListView?


a.
ArrayAdapter


b.
SimpleAdapter


c.
BaseAdapter

---

3. ¿Qué clase es más eficiente para manejar listas grandes y complejas en Android?


a.
ExpandableListView


b.
ListView


c.
RecyclerView

---

4. ¿Qué clase se utiliza para crear listas expandibles en Android?


a.
RecyclerView


b.
ExpandableListView


c.
ListView

---

5. ¿Qué método del adaptador se utiliza para obtener la vista de cada elemento en un ListView?


a.
getCount()


b.
getView()


c.
getItem()

---

6. ¿Qué layout manager se puede usar con RecyclerView para una disposición en forma de lista vertical?


a.
LinearLayoutManager


b.
GridLayoutManager


c.
StaggeredGridLayoutManager

---

7. ¿Qué clase de adaptador se debe extender para personalizar un RecyclerView?


a.
BaseAdapter


b.
RecyclerView.Adapter

c.
ListAdapter

---

8. ¿Cuál es el propósito de un ViewHolder en RecyclerView?


a.
Contener datos del modelo para cada elemento


b.
Gestionar eventos de clic en la lista


c.
Mantener referencias a las vistas de cada elemento para mejorar el rendimiento

---

9. ¿Qué método se utiliza para enlazar datos a una vista en un RecyclerView.Adapter?


a.
onBindViewHolder()


b.
getItemViewType()


c.
onCreateViewHolder()

---

10. ¿Qué método se debe implementar para definir el número de elementos en un RecyclerView.Adapter?


a.
getItemViewType()


b.
getViewTypeCount()


c.
getItemCount()

[Volver al Índice](#índice)

---
---
---

# Autoevaluación 1

<br>

1. 

- La respuesta correcta es:

---

2. 

- La respuesta correcta es:

---

3. 

- La respuesta correcta es:

---

4. 

- La respuesta correcta es:

---

5. 

- La respuesta correcta es:

---

6. 

- La respuesta correcta es:

---

7. 

- La respuesta correcta es:

---

8. 

- La respuesta correcta es:

---

9. 

- La respuesta correcta es:

---

10. 

- La respuesta correcta es:

---

11. 

- La respuesta correcta es:

---

12. 

- La respuesta correcta es:

---

13. 

- La respuesta correcta es:

---

14. 

- La respuesta correcta es:

---

15. 

- La respuesta correcta es:

---


16. 

- La respuesta correcta es:

---

17. 

- La respuesta correcta es:

---

18. 

- La respuesta correcta es:

---

19. 

- La respuesta correcta es:

---

20. 

- La respuesta correcta es:


<br>

[Volver al Índice](#índice)

<br>

---
---
---

# Autoevaluación 2

<br>

1. ¿Cuál es el propósito principal de un ImageView en Android?


a.
Mostrar texto


b.
Mostrar opciones

c.
Mostrar botones


d.
Mostrar imágenes

- La respuesta correcta es:
Mostrar imágenes

---

2. ¿Qué clase se utiliza para crear una lista simple de elementos en Android?


a.
ImageView

b.
RecyclerView


c.
ListView


d.
GridView

- La respuesta correcta es:
ListView

---

3. ¿Qué es una Activity en Android?


a.
Un archivo de recursos que define la estructura de la interfaz de usuario.


b.
Representa una funcionalidad de la aplicación


c.
Un componente que representa una interfaz de usuario en una aplicación.


d.
Una biblioteca externa que se incluye en el proyecto

- La respuesta correcta es:
Un componente que representa una interfaz de usuario en una aplicación.

---

4. ¿Cuál es la diferencia principal entre CheckBox y RadioButton?


a.
CheckBox solo se usa para configuraciones, mientras que RadioButton solo se usa en formularios.


b.
RadioButton permite seleccionar múltiples opciones mientras que CheckBox permite seleccionar solo una.


c.
No hay diferencia significativa entre ellos.


d.
CheckBox permite seleccionar múltiples opciones mientras que RadioButton permite seleccionar solo una.

- La respuesta correcta es:
CheckBox permite seleccionar múltiples opciones mientras que RadioButton permite seleccionar solo una.

---

5. ¿Cómo se puede iniciar una nueva Activity desde la Activity actual?


a.
Intent intent = new Intent(this, NewActivity.class); startService(intent);


b.
Intent intent = new Intent(this, NewActivity.class); startActivity(intent);


c.
Intent intent = new Intent(this, NewActivity.class); sendBroadcast(intent);


d.
Intent intent = new Intent(this, NewActivity.class); sendActivity(intent);

- La respuesta correcta es:
Intent intent = new Intent(this, NewActivity.class); startActivity(intent);

---

6. ¿Cuál es el propósito de un FrameLayout?


a.
Disponer los elementos en forma de tabla


b.
Superponer los elementos unos sobre otros


c.
Disponer los elementos en relación con otros elementos y/o el contenedor.


d.
Disponer los elementos en una sola fila o columna

- La respuesta correcta es:
Superponer los elementos unos sobre otros

---

7. ¿Cuál es el método utilizado para obtener el RadioButton seleccionado de un RadioGroup?


a.
getSelectedRadioGroup()


b.
getRadioButtonId()


c.
getSelectedRadioButtonId()


d.
getCheckedRadioButtonId()

- La respuesta correcta es:
getCheckedRadioButtonId()

---

8. ¿Qué método se debe implementar para manejar el evento de cambio de estado de un Switch?


a.
onUpdate(CompoundButton buttonView, boolean isChecked)


b.
onSwitchToggled(View view, boolean isChecked)


c.
onCheckedChanged(CompoundButton buttonView, boolean isChecked)


d.
onStateChanged(View view, boolean isChecked)

- La respuesta correcta es:
onCheckedChanged(CompoundButton buttonView, boolean isChecked)

---

9. ¿Qué atributo XML se utiliza para ajustar el tamaño de la imagen dentro de un ImageView?


a.
android:adjustViewBounds


b.
android:scaleType


c.
android:resize


d.
android:reScale

- La respuesta correcta es:
android:scaleType

---

10. ¿Qué Layout se utiliza para disponer elementos en una tabla?


a.
GridLayout


b.
TableLayout


c.
ResponsiveLayout


d.
FrameLayout

- La respuesta correcta es:
TableLayout

---

11. ¿Cuál es la diferencia entre un estilo y un tema en Android?


a.
No hay diferencia; ambos términos son intercambiables.


b.
Un estilo se aplica a una vista individual, mientras que un tema se aplica a una actividad o aplicación completa.


c.
Un tema se aplica a una vista individual, mientras que un estilo se aplica a una actividad o aplicación completa.


d.
Un estilo define el comportamiento, mientras que un tema define la estructura.

- La respuesta correcta es:
Un estilo se aplica a una vista individual, mientras que un tema se aplica a una actividad o aplicación completa

---

12. ¿Cuál es el atributo utilizado para establecer un mensaje de sugerencia en un EditText?


a.
android:hint


b.
android:description


c.
android:text


d.
android:label

- La respuesta correcta es:
android:hint

---

13. ¿Qué atributo XML se utiliza para definir si un Switch está encendido por defecto?


a.
android:enabled


b.
android:selected


c.
android:activated


d.
android:checked

- La respuesta correcta es:
android:checked

---

14. ¿Qué método se utiliza para cambiar la imagen de un ImageButton utilizando código?


a.
setImage()


b.
setDrawable()


c.
setImageResource()


d.
setDrawableResource()

- La respuesta correcta es:
setImageResource()

---

15. ¿Cuál es la ventaja principal de usar ConstraintLayout sobre otros Layouts?


a.
Mejor rendimiento y flexibilidad para interfaces complejas


b.
Único responsive

c.
Mayor simplicidad en la disposición de elementos


d.
Menor consumo de memoria.

- La respuesta correcta es:
Mejor rendimiento y flexibilidad para interfaces complejas

---

16. ¿Qué atributo de TextView se utiliza para aplicar un color al texto?


a.
android:color


b.
android:textAlignment


c.
android:background


d.
android:textColor

- La respuesta correcta es:
android:textColor

---

17. La asociación de la parte física con la parte lógica se realiza con el método:



a.
findViewById(R.id.idelemento)


b.
ViewBy(R.id.idelemento)


c.
ViewById(R.id.idelemento)



d.
findViewBy(R.id.idelemento)

- La respuesta correcta es:
findViewById(R.id.idelemento)

---

18. ¿Cuál es la diferencia principal entre ImageView e ImageButton?


a.
ImageView se usa para mostrar botones, mientras que ImageButton se usa para mostrar texto.


b.
No hay diferencia, ambos se usan para mostrar imágenes


c.
ImageView se usa para mostrar imágenes estáticas, mientras que ImageButton es un botón con imagen que puede ser pulsado.


d.
ImageView se usa para mostrar texto estático, mientras que ImageButton es un botón con texto que puede ser pulsado.

- La respuesta correcta es:
ImageView se usa para mostrar imágenes estáticas, mientras que ImageButton es un botón con imagen que puede ser pulsado.

---

19. ¿Qué método se llama cuando una Activity se reanuda y se vuelve interactiva?


a.
onCreate()


b.
onStart()


c.
onResume()


d.
onStop()

- La respuesta correcta es:
onResume()

---

20. ¿Qué atributo se usa para asignar el peso de un elemento dentro de un LinearLayout?


a.
android:layout_gravit


b.
android:layout_order


c.
android:layout_margin


d.
android:layout_weight

- La respuesta correcta es:
android:layout_weight

<br>

[Volver al Índice](#índice)

<br>