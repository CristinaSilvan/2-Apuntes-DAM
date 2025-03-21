# Índice
- [Cuestionario 1 (Acceso a ficheros)](#cuestionario-1-acceso-a-ficheros)
- [Cuestionario 2 (Introducción a las bases de datos)](#cuestionario-2-introducción-a-las-bases-de-datos)
- [Cuestionario 3 (Conectores a SGBD)](#cuestionario-3-conectores-a-sgbd)
- [Cuestionario 4 (Herramientas de mapeo Objeto-Relacional. JPA)]( #cuestionario-4-herramientas-de-mapeo-objeto-relacional-jpa)
- [Cuestionario 5 (Bases de datos relacionales y orientadas a objeto)](#cuestionario-5-bases-de-datos-relacionales-y-orientadas-a-objeto)
- [Cuestionario 6 (Bases de datos XML)](#cuestionario-6-bases-de-datos-xml)
- [Cuestionario 7 (Programación de componentes de acceso a datos)](#cuestionario-7-programación-de-componentes-de-acceso-a-datos)

# Cuestionario 1 (Acceso a ficheros)

1. ¿Qué clase en Java se utiliza para leer archivos de texto?


        a. FileWriter


        b. FileOutputStream


        c. FileReader

La respuesta correcta es:
**FileReader**

- Explicación: 

    - **FileReader**: Se utiliza específicamente para leer archivos de texto. Es una subclase de InputStreamReader, que permite leer caracteres de un archivo de texto.

- Respuestas erróneas: 

    - **FileWriter**: Se utiliza para escribir datos en un archivo de texto.

    - **FileOutputStream**: Se utiliza para escribir bytes de datos en un archivo, pero no está diseñado para leer archivos de texto.

---

2. ¿Cuál es el propósito de la clase BufferedReader en Java?


        a. Escribir en un archivo con buffering


        b. Manejar archivos binarios


        c. Leer de un archivo con buffering

La respuesta correcta es:
**Leer de un archivo con buffering**

- Explicación:

    - **BufferedReader**: Se utiliza para leer caracteres de manera eficiente, especialmente cuando se trata de archivos de texto. Esta clase envuelve un Reader (como un FileReader) y almacena en memoria los datos leídos en un buffer. Esto reduce la cantidad de operaciones de lectura en disco, mejorando la eficiencia.

- Respuestas erróneas: 

    - **Manejar archivos binarios**: Los archivos binarios se manejan con clases como FileInputStream o FileOutputStream, no con BufferedReader

    - **Escribir en un archivo con buffering**: Para esto se usaría BufferedWriter, no BufferedReader

---

3. ¿Qué método de la clase File se utiliza para verificar si un archivo existe?


        a. exists()


        b. canRead()


        c. isFile()

La respuesta correcta es:
**exists()**

- Explicación:

    - El método **exists()** de la clase File en Java se utiliza para verificar si un archivo o directorio existe en el sistema de archivos. Devuelve true si el archivo o directorio existe y false si no.

- Respuestas erróneas: 

    - **canRead()**: Este método verifica si el archivo o directorio tiene permisos de lectura. Devuelve true si el archivo puede ser leído

    - **isFile()**: Este método verifica si el objeto File representa un archivo (no un directorio). Devuelve true si el archivo es un archivo regular y no un directorio.


---

4. ¿Cuál de las siguientes declaraciones es correcta para escribir en un archivo en Java?


        a. BufferedWriter writer = new BufferedWriter(new FileWriter("archivo.txt"));


        b. BufferedReader writer = new BufferedReader(new FileReader("archivo.txt"));


        c. FileOutputStream writer = new FileOutputStream(new BufferedReader("archivo.txt"));

La respuesta correcta es:
**BufferedWriter writer = new BufferedWriter(new FileWriter("archivo.txt"));**

- Explicación: 

    - **BufferedWriter** se utiliza para escribir texto en un archivo de manera eficiente, usando un buffer y **FileWriter** se utiliza para escribir caracteres en un archivo de texto. Combinando ambas clases, BufferedWriter mejora el rendimiento de la escritura al usar un buffer de memoria. Primero se crea un FileWriter que gestiona el archivo y luego se envuelve en un BufferedWriter para mejorar el rendimiento de las operaciones de escritura.

- Respuestas erróneas: 

    - **BufferedReader writer = new BufferedReader(new FileReader("archivo.txt"));** BufferedReader se utiliza para leer archivos, no para escribir. Por lo tanto, esta opción es incorrecta.

    - **FileOutputStream writer = new FileOutputStream(new BufferedReader("archivo.txt"));** FileOutputStream se usa para escribir bytes a un archivo (no texto) y no se debe usar con BufferedReader, que se usa para lectura.


---

5. ¿Qué método en Java se utiliza para manejar archivos binarios?


        a. terminate()


        b. stop()


        c. close()

La respuesta correcta es:
**close()**

- Explicación:

    - El método **close()** se utiliza en Java para cerrar flujos de entrada o salida, incluidos aquellos que manejan archivos binarios, como FileInputStream y FileOutputStream. Este método asegura que los recursos asociados con el flujo se liberen adecuadamente, evitando fugas de recursos.

- Respuestas erróneas: 

    - **terminate()**: No es un método estándar en Java relacionado con la gestión de archivos o flujos.

    - **stop()**: Tampoco es un método relacionado con la manipulación de archivos o flujos binarios. Fue utilizado en el pasado en la clase Thread, pero está obsoleto.

---

6. ¿Qué excepción es comúnmente lanzada cuando ocurre un error de I/O en Java?


        a. IOException


        b. ArithmeticException


        c. NullPointerException

La respuesta correcta es:
IOException

- Explicación:

    - **IOException** es una excepción en Java que se lanza cuando ocurre un error de entrada/salida (I/O):

        - Fallos al leer o escribir un archivo.
        
        - Intentar acceder a un archivo que no existe.
        
        - Problemas con streams o sockets de red.

- Respuestas erróneas: 

    - **ArithmeticException**: Se lanza cuando ocurre un error matemático, como una división entre cero.

    - **NullPointerException**: Se lanza cuando intentas acceder a un miembro o método de un objeto que es null.

---

7. ¿Cuál de las siguientes opciones es correcta para leer una línea de un archivo usando BufferedReader?


        a. String line = reader.readLine();


        b. String line = reader.nextLine();


        c. String line = reader.read();

La respuesta correcta es:
String line = reader.readLine();

- Explicación:

    - El método **readLine()** de la clase BufferedReader se utiliza para leer una línea completa de texto de un archivo o de un flujo de entrada. Devuelve un objeto de tipo String que contiene el contenido de la línea (sin el carácter de fin de línea). Si se alcanza el final del archivo, devuelve null.

- Respuestas erróneas: 

    - **String line = reader.nextLine();** Este método no existe en la clase BufferedReader, pero sí en Scanner, que se utiliza para leer entradas de consola o archivos.

    - **String line = reader.read();** El método read() de BufferedReader lee un solo carácter (como un entero) y no una línea completa, por lo que no es adecuado para este caso.

---

8. ¿Qué clase en Java se utiliza para escribir datos primitivos en un archivo?


        a. FileWriter


        b. PrintStream


        c. DataOutputStream

La respuesta correcta es:
DataOutputStream

- Explicación:

    - La clase **DataOutputStream** en Java se utiliza para escribir datos primitivos (como int, float, double, char, etc.) en un archivo u otro flujo de salida de una manera que pueda ser leída más tarde usando un DataInputStream. Esta clase es útil cuando se necesita escribir datos en un formato binario específico.

    >NOTA: 
    >
    > Las clases FileWriter y FileReader sirven para escribir/leer archivos de texto
    > Las clases BufferedWriter y BufferedReader mejoran la eficiencia de estas añadiendo un búfer intermedio
    > 
    > Las clases FileInputStream y FileOutputStream sirven para escribir/leer en archivos 
    > binarios
    > Las clases BufferedInputStream y BufferedOutputStream mejoran la eficiencia de estas
    > añadiendo un búfer intermedio
    >
    > Además, la clase DataInputStream y DataOutputStream también sirven para escribir/leer
    > en archivos binarios, específicamente tipos de datos primitivos

- Respuestas erróneas:

    - **FileWriter**: Se utiliza para escribir caracteres en un archivo de texto. No está diseñado para escribir datos primitivos de forma binaria.

    - **PrintStream**: Se utiliza para escribir representaciones de texto de datos (como cadenas, números y caracteres) en un flujo de salida, pero no es adecuado para escribir datos primitivos en formato binario.

---

9. ¿Cuál es el propósito de la clase FileInputStream en Java?


        a. Leer contenido de un archivo como caracteres.


        b. Leer contenido de un archivo como bytes.


        c. Escribir contenido en un archivo como bytes.

La respuesta correcta es:
**Leer contenido de un archivo como bytes.**

- Explicación:
    - La clase **FileInputStream** en Java se utiliza para leer datos de un archivo como una secuencia de bytes. Esto significa que puede leer cualquier tipo de archivo (por ejemplo, imágenes, documentos binarios, etc.) de forma byte a byte, sin interpretar los datos como caracteres o texto. 

- Respuestas erróneas:

    - **Leer contenido de un archivo como caracteres**: Se utiliza la clase FileReader

    - **Escribir contenido en un archivo como bytes**: Se utiliza la clase FileOutputStream

---

10. ¿Qué clase en Java se utiliza para escribir datos de tipo primitivo (como int, char, etc.) a un archivo?


        a. PrintWriter


        b. DataOutputStream


        c. FileOutputStream

La respuesta correcta es:
DataOutputStream

- Explicación:

    - La clase **DataOutputStream** en Java se utiliza para escribir datos primitivos (como int, float, double, char, etc.) en un archivo u otro flujo de salida de una manera que pueda ser leída más tarde usando un DataInputStream. Esta clase es útil cuando se necesita escribir datos en un formato binario específico.

- Respuestas erróneas:

    - **PrintWriter**: Aunque esta clase también puede escribir datos en un archivo, está más orientada a escribir datos como texto (de tipo String, char, etc.), no en formato binario como DataOutputStream.

    - **FileOutputStream**: Se utiliza para escribir datos en forma de bytes a un archivo, pero no proporciona métodos específicos para escribir tipos primitivos como int o char de manera eficiente (es más baja en nivel que DataOutputStream).

    >NOTA: 
    >
    > PrintWriter se diferencia de FileWriter en esencia funcionan igual:
    > 
    > - FileWriter: Se usa si necesitas escribir textos sencillos sin preocuparte del 
    > formato. Está diseñado para escribir Strings y Character, aunque puede escribir
    > datos numéricos pero convertidos a texto
    >
    > - PrintWriter: Se usa cuando necesitas escribir un texto sin perder la tipología de 
    > los datos almacenados, por lo que permite un manejo más complejo. Escribe datos
    > caracteres al igual que FileWriter, pero también tipos primitivos e incluso objetos
    >
    > Además, agrega salto de líneas automáticos, por lo que cuida más la presentación, en 
    > lugar de tener que añadir manualmente \n
    >
    > Tiene métodos convenientes como println(), printf() y format() que proporcionan
    > formato y facilidades adicionales que lo hacen más cómodo y funcional

[Volver al Índice](#índice)

---
---
---

# Cuestionario 2 (Introducción a las bases de datos)

[Volver al Índice](#índice)

1. ¿Qué es una base de datos?


        a. Un archivo de texto sin estructura


        b. Un programa de edición de imágenes


        c. Un sistema organizado para almacenar y gestionar datos

La respuesta correcta es:
**Un sistema organizado para almacenar y gestionar datos**

---

2. ¿Qué lenguaje se utiliza comúnmente para consultar bases de datos relacionales?


        a. CSS


        b. HTML


        c. SQL

La respuesta correcta es:
**SQL**

---

3. ¿Cuál es el propósito de un esquema en una base de datos?


        a. Ejecutar scripts de programación


        b. Definir la estructura y organización de la base de datos


        c. Realizar copias de seguridad

La respuesta correcta es:
Definir la estructura y organización de la base de datos

---

4. ¿Qué es una tabla en el contexto de bases de datos relacionales?


        a. Un archivo de imagen


        b. Un conjunto de instrucciones SQL


        c. Una colección de datos organizados en filas y columnas

La respuesta correcta es:
**Una colección de datos organizados en filas y columnas**

---

5. ¿Qué es una clave primaria en una base de datos?


        a. Un campo para almacenar contraseñas


        b. Un campo que permite la duplicación de registros


        c. Un campo que identifica de manera única cada registro en una tabla

La respuesta correcta es:
**Un campo que identifica de manera única cada registro en una tabla**

---

6. ¿Cuál es la principal función de un sistema de gestión de bases de datos (DBMS)?


        a. Editar documentos de texto


        b. Administrar y manipular datos almacenados en bases de datos


        c. Administrar el acceso a las redes


La respuesta correcta es:
**Administrar y manipular datos almacenados en bases de datos**

- Explicación: 

    - **Un Sistema de Gestión de Bases de Datos (DBMS)** es un software que se utiliza para crear, gestionar, manipular y mantener bases de datos. Sus principales funciones incluyen:

        - Almacenamiento de datos: Proporciona una estructura organizada para almacenar grandes volúmenes de datos.

        - Acceso a los datos: Permite a los usuarios y aplicaciones consultar, insertar, actualizar y eliminar datos de manera eficiente.

        - Seguridad y control de acceso: Controla quién tiene acceso a qué datos y protege la integridad de los datos.

        - Gestión de transacciones: Asegura que las operaciones en la base de datos se realicen de forma coherente y segura (con transacciones, ACID).

        - Respaldo y recuperación: Proporciona mecanismos para hacer copias de seguridad de los datos y recuperarlos en caso de fallos.

---

7. ¿Qué es una consulta en el contexto de bases de datos?


        a. Un procedimiento para eliminar la base de datos


        b. Una operación para modificar la estructura de la base de datos


        c. Una operación para obtener datos específicos de una base de datos

La respuesta correcta es:
**Una operación para obtener datos específicos de una base de datos**

---

8. ¿Qué tipo de relación existe entre las tablas en una base de datos relacional?


        a. Una relación sin restricciones


        b. Una relación uno a uno, uno a muchos, o muchos a muchos


        c. Una relación de tipo jerárquica

La respuesta correcta es:
**Una relación uno a uno, uno a muchos, o muchos a muchos**

---

9. ¿Cuál es la diferencia entre una base de datos estática y una dinámica?


        a. No hay ninguna diferencia


        b. La base de datos dinámica solo contiene texto, mientras que la estática contiene imágenes


        c. La base de datos estática no se actualiza, mientras que la dinámica sí

La respuesta correcta es:
**La base de datos estática no se actualiza, mientras que la dinámica sí**

---

10. ¿Qué es un índice en una base de datos?


        a. Un tipo de consulta compleja


        b. Una estructura que mejora la velocidad de recuperación de datos


        c. Un campo para almacenar datos de tipo texto

La respuesta correcta es:
**Una estructura que mejora la velocidad de recuperación de datos**

- Explicación:

    - Un **índice** en una base de datos es una estructura especial que se utiliza para mejorar la velocidad de las consultas. Actúa como un "índice" en un libro, permitiendo que el sistema de gestión de bases de datos (DBMS) localice rápidamente los datos sin tener que recorrer toda la tabla de forma secuencial. Un índice es una estructura que hace referencia a las ubicaciones de los datos.

[Volver al Índice](#índice)

---
---
---

# Cuestionario 3 (Conectores a SGBD)

No me permite realizarlo

[Volver al Índice](#índice)

---
---
---

# Cuestionario 4 (Herramientas de mapeo Objeto-Relacional. JPA)

1. ¿Cuál de los siguientes métodos se utiliza para crear una nueva entidad en JPA?


        a. create()


        b. persist()


        c. confirm()


        d. save()

La respuesta correcta es:
**persist()**

- Explicación:

    - En JPA (Java Persistence API), el método **persist()** se utiliza para crear una nueva entidad y persistirla (guardar) en la base de datos. Cuando se invoca el método persist() sobre un objeto de una entidad, este objeto se marca como entidad gestionada y se sincroniza con la base de datos en el contexto de persistencia.

- Respuestas erróneas:

    - **create()** no es un método estándar de JPA.

    -  **confirm()** no es un método en JPA. Las operaciones de confirmación de transacciones se manejan con commit() después de realizar operaciones como persist().

    -  **save()** no es un método estándar de JPA. Es más común en frameworks como Spring Data JPA, pero no es parte de la especificación oficial de JPA.

---

2. Para leer una entidad por su ID en JPA, ¿qué método se utiliza?


        a. write()


        b. find()


        c. read()


        d. get()


La respuesta correcta es:
**find()**

- Explicación:

   - En JPA (Java Persistence API), el método **find()** se utiliza para leer una entidad de la base de datos por su ID. Este método busca una entidad en el contexto de persistencia y, si se encuentra, la devuelve. Si la entidad no existe, find() devuelve null.

- Respuestas erróneas:

   - **write()** no es un método estándar en JPA para leer o consultar entidades. El método write() es más comúnmente utilizado en flujos de datos o escritura de archivos,

   - **read()** no es un método estándar de JPA. Aunque intuitivamente se podría pensar que podría ser el método para leer una entidad.

   - **get()** tampoco es un método estándar en JPA para leer entidades por su ID. Si bien algunos frameworks o bibliotecas pueden tener un método get(), en la especificación oficial de JPA se utiliza find() para esta tarea.

---

3. ¿Qué método se usa para actualizar una entidad en JPA?


        a. refresh()


        b. update()


        c. actualiza()


        d. merge()

La respuesta correcta es:
**merge()**

- Explicación:
 
 - El método **merge()** del EntityManager se utiliza para actualizar el estado de una entidad en el contexto de persistencia. Este método se usa cuando se tiene una entidad en estado "desacoplado" (detached), es decir, cuando una entidad ha sido modificada fuera del contexto de persistencia y luego se quiere sincronizar esos cambios con la base de datos. Si la entidad ya existe en la base de datos, merge() la actualiza; si no existe, la inserta.

 - El **EntityManager** es una de las clases principales en la Java Persistence API (JPA), que actúa como el intermediario entre las aplicaciones Java y la base de datos. Su función principal es gestionar las entidades (objetos de la clase Java que están mapeados a las tablas de la base de datos) durante su ciclo de vida en el contexto de persistencia.


- Respuestas erróneas: 
 
 - El método **refresh()** no actualiza una entidad en la base de datos. En cambio, refresh() se utiliza para recargar una entidad desde la base de datos, desechando cualquier cambio no guardado que pueda haber en la entidad en memoria, para que su estado refleje el último estado persistido en la base de datos.
 
 - **update()** no es un método estándar de JPA.
 
 - **actualiza()** no es un método en JPA.

---

4. ¿Cómo se elimina una entidad en JPA?


        a. drop()


        b. delete()


        c. remove()

La respuesta correcta es:
**remove()**

- Explicación:
 
 - En JPA (Java Persistence API), el método **remove()** se utiliza para eliminar una entidad de la base de datos. Este método marca la entidad como eliminada dentro del contexto de persistencia, y cuando la transacción se confirma (usando commit()), la entidad se elimina físicamente de la base de datos.

- Respuestas erróneas:
 
 - **drop()** no es un método en JPA para eliminar entidades. El comando DROP en SQL se utiliza para eliminar objetos de la base de datos, como tablas, pero no se utiliza en el contexto de JPA para eliminar entidades.
 
 - **delete()** no es un método estándar de JPA. Aunque muchos frameworks o bases de datos pueden usar delete(), en JPA, el método adecuado para eliminar entidades es remove().

---

5. ¿Qué anotación se utiliza para definir una entidad en JPA?


        a. @Persistence


        b. @Table


        c. @Entity


La respuesta correcta es:
**@Entity**

- Explicación:

 - En JPA (Java Persistence API), la anotación **@Entity** se utiliza para definir una clase como una entidad que está vinculada a una tabla en la base de datos. Las clases anotadas con @Entity serán gestionadas por el proveedor de persistencia (como Hibernate) y sus instancias se pueden almacenar en la base de datos.
 
 - **Hibernate** es uno de los proveedores de persistencia más populares, pero existen otros como EclipseLink o OpenJPA.

- Respuestas erróneas:
 
 - **@Persistence** no es una anotación de JPA para definir entidades. Existen otras anotaciones en JPA relacionadas con la persistencia, pero @Persistence no se utiliza para definir una entidad.

 - **@Table** se utiliza para especificar la tabla de la base de datos que corresponde a la entidad, pero no es la anotación principal para definir una entidad. Se usa en conjunto con @Entity para personalizar la tabla asociada a una entidad.

---

6. ¿Cuál es el propósito del método flush() en JPA?


        a. Limpiar el caché de entidades


        b. Sincronizar el estado del contexto de persistencia con la base de datos


        c. Cerrar el EntityManager


La respuesta correcta es:
**Sincronizar el estado del contexto de persistencia con la base de datos**

- Explicación:
 
 - El método **flush()** en JPA (Java Persistence API) se utiliza para sincronizar el estado del **persistence context** con la base de datos. Es decir, cuando se realiza una operación de persistencia (como persist(), merge(), o remove()), los cambios se mantienen en memoria en el contexto de persistencia. El método flush() fuerza a JPA a enviar esos cambios a la base de datos, pero sin comprometer la transacción (es decir, sin hacer un commit()).

- Respuestas erróneas:
 
 - **Limpiar el caché de entidades**: El método flush() no limpia el caché de entidades. Su función es asegurar que los cambios en el contexto de persistencia se reflejen en la base de datos, pero no tiene que ver con limpiar el caché. Para limpiar el caché, existen otros métodos como clear().

 - **Cerrar el EntityManager**: El método flush() no cierra el EntityManager. Para cerrar un EntityManager, se utiliza el método close(), que libera los recursos asociados con el EntityManager.

---

7. ¿Qué anotación se utiliza para generar automáticamente valores para la clave primaria?


        a. @AutoIncrement


        b. @GeneratedValue


        c. @AutoGenerate


La respuesta correcta es:
**@GeneratedValue**

- Explicación:
 
 - En JPA (Java Persistence API), la anotación **@GeneratedValue** se utiliza para generar automáticamente valores para la clave primaria de una entidad. Esto es común cuando se desea que el valor de la clave primaria (como un identificador único) sea asignado automáticamente por la base de datos (por ejemplo, mediante un contador incremental o un valor único generado). Esta anotación puede configurarse con diferentes estrategias de generación, como AUTO, IDENTITY, SEQUENCE o TABLE, dependiendo de la base de datos y de cómo se desee generar el valor.

- Respuestas erróneas:

 - **@AutoIncrement** no es una anotación válida en JPA. Aunque algunas bases de datos utilizan una propiedad AUTO_INCREMENT para generar valores automáticamente en la clave primaria.

 - **@AutoGenerate** tampoco es una anotación válida en JPA.

---

8. ¿Cómo se llama la consulta de JPA que se escribe en el propio lenguaje de consulta de JPA?


        a. HQL


        b. JPQL


        c. SQL

La respuesta correcta es:
**JPQL**

- Explicación:

 - **JPQL (Java Persistence Query Language)** es el lenguaje de consulta utilizado en JPA (Java Persistence API) para realizar consultas sobre las entidades gestionadas por el proveedor de persistencia. A diferencia de SQL, que se escribe directamente sobre la base de datos, JPQL opera sobre las entidades (no las tablas directamente) y se basa en la estructura del modelo de objetos de Java.

- Respuestas erróneas:

 - **HQL (Hibernate Query Language)** es un lenguaje de consulta similar a JPQL, pero es específico de Hibernate, que es una implementación de JPA. Sin embargo, HQL no es parte de la especificación oficial de JPA, aunque comparte muchas similitudes con JPQL.

 - **SQL (Structured Query Language)** es el lenguaje estándar utilizado para interactuar directamente con bases de datos. Aunque JPA permite escribir consultas SQL nativas, JPQL es el lenguaje específico de JPA para consultas de entidades.

---

9. ¿Qué método del EntityManager se usa para ejecutar una consulta JPQL?


        a. executeQuery()


        b. createQuery()


        c. runQuery()

La respuesta correcta es:
**createQuery()**

- Explicación:

 - El método **createQuery()** del EntityManager se utiliza para ejecutar una consulta JPQL en JPA. Este método toma como argumento una cadena de texto que contiene la consulta JPQL y devuelve un objeto Query que se puede usar para configurar parámetros y obtener los resultados.

```
En este ejemplo, createQuery() se usa para crear una consulta JPQL y luego se establece el valor del parámetro nombre mediante setParameter(). Los resultados de la consulta se obtienen con getResultList():

String jpql = "SELECT c FROM Cliente c WHERE c.nombre = :nombre";
Query query = entityManager.createQuery(jpql);
query.setParameter("nombre", "Carlos");

List<Cliente> clientes = query.getResultList();
```

- Respuestas erróneas:

 - **executeQuery()** no es un método del EntityManager en JPA. Este es un método de la interfaz Statement en JDBC, pero no se utiliza en JPA para ejecutar consultas.

 - **runQuery()** tampoco es un método del EntityManager en JPA.

---

10. ¿Qué método del EntityManager se utiliza para actualizar el estado de una entidad en el contexto de persistencia?


        a. refresh()


        b. merge()


        c. sync()


La respuesta correcta es:
**refresh()**

- Explicación:

 - **refresh()**: Este método se utiliza para sincronizar el estado de una entidad con la base de datos. Básicamente, carga la última versión de la entidad desde la base de datos, sobrescribiendo cualquier cambio que haya ocurrido en la entidad en el contexto de persistencia (si se ha modificado algo en el contexto de persistencia, se perderá).

- Respuestas erróneas:

 - El método **sync()** no es un método estándar de JPA ni de Hibernate en el contexto del manejo de entidades y persistencia.


[Volver al Índice](#índice)

---
---
---

# Cuestionario 5 (Bases de datos relacionales y orientadas a objeto)

1. ¿Qué es una base de datos orientada a objetos?


        a. Un sistema de gestión de bases de datos que usa tablas para almacenar datos.


        b. Un sistema de gestión de bases de datos utilizado solo para datos numéricos.


        c. Un sistema de gestión de bases de datos que representa la información en forma de objetos.

La respuesta correcta es:
**Un sistema de gestión de bases de datos que representa la información en forma de objetos.**

---

2. ¿Qué es un OID (Object Identifier) en una base de datos orientada a objetos?


        a. Un identificador único para cada objeto en la base de datos.


        b. Un identificador único para cada columna en una tabla.


        c. Un identificador único para cada fila en una tabla.

La respuesta correcta es:
**Un identificador único para cada objeto en la base de datos.**

- Explicación:

 - En las bases de datos orientadas a objetos, un OID (Object Identifier) es un identificador único asignado a cada objeto almacenado en la base de datos. Este identificador permite que los objetos sean referenciados y gestionados independientemente de su contenido o estado. Los OID son cruciales para garantizar la unicidad y facilitar el manejo de los objetos dentro de la base de datos.

---

3. ¿Cuál de las siguientes es una característica de las bases de datos orientadas a objetos?


        a. Uso exclusivo de lenguaje SQL.


        b. Uso de claves primarias y foráneas.


        c. Uso de clases y herencia.

La respuesta correcta es:
**Uso de clases y herencia.**

---

4. ¿Qué ventaja tienen las bases de datos orientadas a objetos sobre las relacionales?


        a. Concordancia con el modelo de programación orientado a objetos


        b. Mayor facilidad para manejar datos tabulares.


        c. Mayor estandarización.

La respuesta correcta es:
**Concordancia con el modelo de programación orientado a objetos.**

---

5. ¿Qué es el encapsulamiento en una base de datos orientada a objetos?


        a. La capacidad de dividir la base de datos en múltiples tablas.


        b. La capacidad de ocultar los datos de implementación interna y exponer solo una interfaz.


        c. La capacidad de realizar consultas SQL.

La respuesta correcta es:
**La capacidad de ocultar los datos de implementación interna y exponer solo una interfaz.**

---

6. ¿Qué es el polimorfismo en una base de datos orientada a objetos?


        a. La capacidad de una clase para tener múltiples subclases.


        b. La capacidad de un método para operar con diferentes tipos de datos.


        c. La capacidad de una base de datos para contener múltiples tipos de datos.

La respuesta correcta es:
**La capacidad de un método para operar con diferentes tipos de datos.**

---

7. ¿Qué desventaja tienen las bases de datos orientadas a objetos?


        a. Incompatibilidad con los lenguajes de programación orientados a objetos


        b. Menor flexibilidad y extensibilidad.


        c. Falta de estandarización.

La respuesta correcta es:
**Falta de estandarización.**

---

8. ¿Qué es XML?


        a. Un formato de marcado para describir datos estructurados en texto plano.


        b. Un lenguaje de programación orientado a objetos.


        c. Un sistema de gestión de bases de datos.

La respuesta correcta es:
**Un formato de marcado para describir datos estructurados en texto plano.**

---

9. ¿Cuál de las siguientes es una expresión XPath válida para seleccionar todos los elementos `<libro>` en un documento XML?


        a. xml/libro


        b. /libreria/libro


        c. //libro


        d. @libro

La respuesta correcta es:
**//libro**

---

10. ¿Cómo se seleccionan los elementos `<titulo>` de un documento XML utilizando XPath?


        a. titulo/


        b. /titulo


        c. //titulo

La respuesta correcta es:
**//titulo**

[Volver al Índice](#índice)

---
---
---

# Cuestionario 6 (Bases de datos XML)

# Cuestionario 1 (Acceso a ficheros)

1. ¿Qué es XQuery?

        a. Un lenguaje para consultar datos XML.


        b. Un lenguaje para consultar bases de datos relacionales.


        c. Un lenguaje de programación para desarrollo web


        d. Un lenguaje utilizado en algoritmos de inteligencia artificial

La respuesta correcta es:
**Un lenguaje para consultar datos XML**

---

2. ¿Cuál es la estructura básica de una consulta XQuery?

        a. IF ... ELSE ... END IF ...


        b. FOR ... LET ... WHERE ... RETURN ..


        c. SELECT ... FROM ... WHERE ...
 
La respuesta correcta es:
**FOR ... LET ... WHERE ... RETURN ..**

---

3. ¿Qué operador se utiliza en XQuery para concatenar cadenas?

        a. &


        b. ||


        c. +

La respuesta correcta es:
**||**

---

4. ¿Cuál de las siguientes es una expresión válida en XQuery para seleccionar todos los elementos `<libro>`?

        a. /libro


        b. //libro


        c. libro

La respuesta correcta es:
**libro o //libro**, dependiendo del contexto...

- Explicación de cada opción:

 - /libro → Selecciona el elemento `<libro>` solo si está en la raíz del documento. Esto rara vez es útil porque en la mayoría de los XML `<libro>` es un nodo secundario.

  - //libro → Esta es la forma más común y correcta de seleccionar todos los elementos `<libro>` en cualquier parte del XML.

  - libro → es posible que esté considerando un contexto específico dentro de XQuery, pero en términos de XPath, que es la base para seleccionar nodos en XQuery, esta opción por sí sola no es una expresión XPath válida.

---

5. ¿Cuál es la función en XQuery para convertir una cadena a minúsculas?

        a. toLowerCase()


        b. to-lower()


        c. lower-case()

La respuesta correcta es:
**lower-case()**

---

6. ¿Cuál de las siguientes opciones describe correctamente la función doc() en XQuery?

        a. Se utiliza para contar el número de nodos en un documento XML.


        b. Se utiliza para crear un nuevo documento XML.


        c. Se utiliza para importar un documento XML en la consulta.

La respuesta correcta es:
**Se utiliza para importar un documento XML en la consulta**

- Explicación: 

        La función doc() en XQuery se usa para acceder o importar un documento XML y trabajar con su contenido.

        Si tienes un archivo llamado "biblioteca.xml", puedes cargarlo en XQuery así:

        ```
        let $xml := doc("biblioteca.xml")
        return $xml
        ```

---

7. ¿Qué expresión XQuery selecciona todos los elementos `<titulo>` dentro de elementos `<libro>`?

        a. //libro//titulo


        b. /libro/titulo


        c. libro/titulo

La respuesta correcta es:
**//libro//titulo**

- Explicación de cada opción:

        a. //libro//titulo: Selecciona todos los elementos `<titulo>` dentro de `<libro>`, sin importar cuán anidados estén dentro de `<libro>`.

                - Funciona sin importar la estructura del XML.

                - Es la opción más flexible y común en XPath dentro de XQuery.

        b. /libro/titulo: 
        
                - Solo funciona si `<libro>` es el elemento raíz del documento XML.
                
                - Si `<libro>` está dentro de otro nodo, no funcionará.

        c. libro/titulo: No es una expresión XPath válida en XQuery. Podría funcionar solo si ya estás iterando sobre nodos `<libro>` dentro de una consulta FLWOR, pero no por sí sola.


---

8. ¿Cómo se comenta una línea en XQuery?

        a. `(: comentario :)`


        b. `<!-- comentario -->`


        c. `*/ Comentario */`


        d. `// comentario`

La respuesta correcta es:
`(: comentario :)`


---

9. ¿Qué palabra clave en XQuery se usa para ordenar los resultados?

        a. SORT BY


        b. GROUP BY


        c. ORDER BY

La respuesta correcta es:
**ORDER BY**

- Explicación:
 
 - ORDER BY se usa para ordenar los resultados de una consulta en función de un criterio específico.

- Respuestas erróneas:

 - SORT BY no es una palabra clave válida en XQuery. Algunos lenguajes como SQL o Python usan "sort", pero XQuery usa ORDER BY.

 - GROUP BY en otros lenguajes (como SQL) se usa para agrupar registros con valores similares, pero en XQuery la agrupación se hace con group by en una cláusula "for" dentro de FLWOR (For, Let, Where, Order by, Return).

[Volver al Índice](#índice)

---
---
---

# Cuestionario 7 (Programación de componentes de acceso a datos)

1. ¿Qué significa JSON?

        a. JavaScript Object Notation


        b. JavaScript Online Notation


        c. JavaScript Over None


        d. JavaScript Over Network

La respuesta correcta es:
**a. JavaScript Object Notation**

- Explicación:
 
 - JSON (JavaScript Object Notation) es un formato ligero de intercambio de datos que es fácil de leer y escribir para los humanos, y fácil de interpretar y generar para las máquinas. Se basa en la sintaxis de objetos de JavaScript, pero es independiente del lenguaje, lo que lo hace ampliamente utilizado para el intercambio de datos entre servidores y aplicaciones web.


---

2. ¿Cuál de los siguientes es un formato de datos utilizado por MongoDB para almacenar documentos?

        a. BSON


        b. JSON


        c. XML

La respuesta correcta es:
**BSON**

- Explicación:
 
 - MongoDB utiliza BSON (Binary JSON) para almacenar documentos. BSON es una representación binaria de JSON que permite almacenar datos de manera más eficiente, admitiendo tipos de datos adicionales como fechas y enteros de 64 bits, lo que mejora el rendimiento y la flexibilidad en comparación con JSON estándar.


---

3. ¿Qué método se usa en MongoDB para insertar un solo documento en una colección?

        a. createOne()


        b. insertOne()


        c. addOne()

La respuesta correcta es:
**insertOne()**

- Explicación:
 
 - El método insertOne() se utiliza en MongoDB para insertar un único documento en una colección. Es parte de la API de MongoDB y permite agregar datos de forma sencilla y eficiente.

- Respuestas erróneas:

 - createOne() y addOne() no existen en la API de MongoDB.


---

4. ¿Cómo se representa un array en JSON?

        a. { "array": (1, 2, 3) }


        b. { "array": {1, 2, 3} }


        c. { "array": [1, 2, 3] }

La respuesta correcta es:
**{ "array": [1, 2, 3] }**

- Explicación:
 
 - En JSON, los arrays se representan utilizando corchetes [ ], lo que permite listar elementos de manera ordenada. Los otros ejemplos usan paréntesis o llaves, que no son la sintaxis correcta para un array en JSON.


--- 

5. ¿Cuál es el método en MongoDB para actualizar un solo documento que cumple con un criterio específico?

        a. changeOne()


        b. updateOne()


        c. modifyOne()

La respuesta correcta es:
**updateOne()**

- Explicación:
 
 - Este método se utiliza para actualizar únicamente el primer documento que cumple con el criterio especificado. Si se quisiera actualizar todos los documentos que cumplan con la condición, se utilizaría el método updateMany().

- Respuestas erróneas:

 - changeOne() y modifyOne() no existen en la API de MongoDB.


---

6. En MongoDB, ¿qué método se usa para encontrar todos los documentos que cumplen con un criterio?

        a. find()


        b. search()


        c. get()

La respuesta correcta es:
**find()**

- Explicación:
 
 - En MongoDB, el método find() se utiliza para buscar y recuperar todos los documentos que cumplen con un criterio específico. Este método devuelve un cursor que permite iterar sobre los documentos encontrados.

- Respuestas erróneas:

 - search() no existe en la API de MongoDB. MongoDB tiene text indexes que usan find() con $text para búsquedas avanzadas, pero no un método llamado search().

 - En algunas bases de datos relacionales, get() se usa para recuperar registros, pero MongoDB no lo utiliza.


---

7. ¿Cuál de las siguientes es una característica clave de JSON?

        a. Es un formato de texto ligero.


        b. Es específico de JavaScript y no puede ser usado por otros lenguajes.


        c. Es un formato binario.

La respuesta correcta es:
**Es un formato de texto ligero**

- Explicación:
 
 - JSON es un formato de texto diseñado para el intercambio de datos, lo que lo hace fácil de leer y escribir tanto para humanos como para máquinas. Además, aunque se basa en la sintaxis de JavaScript, es independiente del lenguaje, por lo que puede ser utilizado por diferentes plataformas y lenguajes de programación.


---

8. ¿Qué método se usa en MongoDB para eliminar un solo documento que cumple con un criterio específico?

        a. removeOne()


        b. deleteOne()


        c. eraseOne()

La respuesta correcta es:
**deleteOne()**

- Explicación:
 
 - El método deleteOne() se utiliza en MongoDB para eliminar un único documento que cumple con el criterio especificado. Este método elimina el primer documento que coincida con la consulta proporcionada.

- Respuestas erróneas:

 - removeOne() y eraseOne() no existen en la API de MongoDB


---

9. ¿Qué tipo de dato no se puede representar directamente en JSON?

        a. Boolean


        b. String


        c. Date

La respuesta correcta es:
**Date**

- Explicación:
 
 - En JSON, no existe un tipo de dato nativo para representar fechas. Aunque se pueden representar fechas como cadenas de texto (strings) siguiendo un formato específico, JSON no define un tipo de dato "Date" de forma directa.


---

10. En MongoDB, ¿qué método se usa para insertar múltiples documentos a la vez?

        a. insertMany()


        b. insertMultiple()


        c. addMany()


        d. addMultiple()

La respuesta correcta es:
**insertMany()**

- Explicación:
 
 - El método insertMany() se utiliza en MongoDB para insertar múltiples documentos en una colección en una sola operación. Este método es eficiente y permite agregar un array de documentos de forma simultánea.

- Respuestas erróneas:

 - insertMultiple() y addMany() no existen en la API de MongoDB


[Volver al Índice](#índice)