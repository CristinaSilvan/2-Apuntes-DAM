# Índice
- [Acceso a Ficheros (Unidad 1)](#acceso-a-ficheros-unidad-1)
  - [Introducción](#introducción)
  - [Excepciones](#excepciones)
  - [Ficheros de datos](#ficheros-de-datos)
  - [Clase File](#clase-file)
  - [Clases de Manejo de archivos](#clases-de-manejo-de-archivos)
  - [FileWriter](#filewriter)
  - [PrintWriter](#printwriter)
  - [InputStreamReader](#inputstreamreader)
  - [FileReader](#filereader)
  - [BufferedWriter y BufferedReader](#bufferedwriter-y-bufferedreader)
  - [FileInputStream](#fileinputstream)
  - [FileOutputStream](#fileoutputstream)
  - [BufferedInputStream y BuffereOutputStream](#bufferedinputstream-y-buffereoutputstream)
  - [Uso de try/catch](#uso-de-trycatch)

- [Introducción a las Bases de Datos (Unidad 2)](#introducción-a-las-bases-de-datos-unidad-2)
- [Conectores a SGBD (Unidad 3)](#conectores-a-sgbd-unidad-3)
- [Herramientas de mapeo Objeto-Relacional JPA (Unidad 4)](#herramientas-de-mapeo-objeto-relacional-jpa-unidad-4)
- [Bases de datos relacionales y orientadas a objeto (Unidad 5)](#bases-de-datos-relacionales-y-orientadas-a-objeto-unidad-5)
- [Bases de Datos XML (Unidad 6)](#bases-de-datos-xml-unidad-6)

<br>

- [Cuestionario 1 (Acceso a ficheros)](#cuestionario-1-acceso-a-ficheros)
- [Cuestionario 2 (Introducción a las bases de datos)](#cuestionario-2-introducción-a-las-bases-de-datos)
- [Cuestionario 3 (Conectores a SGBD)](#cuestionario-3-conectores-a-sgbd)
- [Cuestionario 4 (Herramientas de mapeo Objeto-Relacional. JPA)]( #cuestionario-4-herramientas-de-mapeo-objeto-relacional-jpa)
- [Cuestionario 5 (Bases de datos relacionales y orientadas a objeto)](#cuestionario-5-bases-de-datos-relacionales-y-orientadas-a-objeto)
- [Cuestionario 6 (Bases de datos XML)](#cuestionario-6-bases-de-datos-xml)
- [Cuestionario 7 (Programación de componentes de acceso a datos)](#cuestionario-7-programación-de-componentes-de-acceso-a-datos)

<br>

- [Autoevaluación 1](#autoevaluación-1)
- [Autoevaluación 2](#autoevaluación-2)

---
---
---

# Acceso a Ficheros (Unidad 1)

## Introducción

La persistencia en el contexto de bases de datos es la capacidad de un sistema de almacenar datos de manera duradera, de modo que permanezcan disponibles incluso después de que el sistema haya sido apagado o reiniciado.

Es crucial para las aplicaciones donde la integridad de los datos debe mantenerse entre ejecuciones.

[Volver al Índice](#índice)

## Excepciones

Las excepciones son fundamentales en el acceso a datos porque permiten gestionar los errores y situaciones inesperadas que pueden ocurrir durante la interacción con una base de datos y poner en peligro la persistencia e integridad de la información.

Cuando las excepciones son fatales, provocan la finalización de la ejecución de un programa. Es conveniente terminar ordenadamente dando un mensaje explicativo sobre el error que se ha producido.

[Volver al Índice](#índice)

## Ficheros de datos

Un fichero permite almacenar datos, funcionando como una base de datos primitiva y sencilla.

Los ficheros pueden ser de entrada (input) o de salida (output) dependiendo de si están siendo utilizados para leer o escribir datos.

En Java existen dos tipos de ficheros: binarios y de texto. Para esto, Java contiene una gran cantidad de clases en combinación unas con otras.
El package de java.io contiene cerca de 50 clases, 10 interfaces y 15 excepciones con propósitos específicos desarrolladas con una alta cohesión, para manejar una gran cantidad de situaciones que se nos pueden poner por delante.

[Volver al Índice](#índice)

## Clase File

Proporciona una abstracción para trabajar con archivos y directorios en el sistema de archivos. A través de esta clase, puedes realizar diversas operaciones sobre archivos y ficheros, como crear, eliminar, renombrar o consultar propiedades.

Las instancias de la clase File, no manejan el contenido de los archivos, sino que se usa para representar el camino o ruta de un archivo o directiorio.
Es por esto que se necesitan otras clases como FileInputStream, FileOutputStream, BufferedReader, BufferedWriter, etc.

- Constructores:
```
public File(String pathname);
    public File f1 = new File("/carpeta/archivo.pdf"); 

public File(String parent, String child);
    public File f2 = new File("/carpeta", "archivo");

public File(File parent, String child);
    public File f3 = new File(new File("/carpeta"), "archivo");
    public File f4 = new File(f2, "archivo");

public File (URI uri);
    public URI uri = new URI("file:///C:/Users/Usuario/Documents/file.txt");
    public File f5 = new File(uri);
```

- Crear el archivo o directorio si no existe:
```
File archivo = new File("miArchivo.txt");
archivo.createNewFile();

File directorio = new File("miDirectorio");
directorio.mkdir();
```

- Eliminar archivo o directorio:
```
File archivo = new File("miArchivo.txt");
archivo.delete();

File directorio = new File("miDirectorio");
directorio.delete();
```

- Renombrar:
```
File archivo = new File("miArchivo.txt");
File nuevoArchivo = new File("nuevoArchivo.txt");
archivo.renameTo(nuevoArchivo);
```

- Verificar existencia:
```
File archivo = new File("miArchivo.txt");
if (archivo.exists()) {
    System.out.println("El archivo existe.");
}
```

- Comprobar si una instancia representa un archivo o directorio:
```
File archivo = new File("miArchivo.txt");
if (archivo.isFile()) {
    System.out.println("Es un archivo.");
}
if (archivo.isDirectory()) {
    System.out.println("Es un directorio.");
}
```

- Obtener información sobre la instancia:
```
File archivo = new File("miArchivo.txt");
System.out.println("Nombre: " + archivo.getName());
System.out.println("Ruta absoluta: " + archivo.getAbsolutePath());
System.out.println("Tamaño en bytes: " + archivo.length());
```

- Modificar permisos:
```
File archivo = new File("miArchivo.txt");
archivo.setReadable(true); // Establece que el archivo sea legible.
archivo.setWritable(true); // Establece que el archivo sea escribible.
archivo.setExecutable(true); // Establece que el archivo sea ejecutable.
```

- Resumen de métodos:
    - Información básica del fichero:
        - String getName(): Devuelve el nombre del fichero o directorio.
        - String getPath(): Devuelve la ruta relativa o absoluta usada al crear el objeto File.
        - String getAbsolutePath(): Devuelve la ruta absoluta del fichero o directorio.
        - String getParent(): Devuelve el nombre del directorio padre, o null si no tiene.
        - boolean renameTo(File NuevoNombre): Renombra el fichero o directorio al especificado.

    - Comprobaciones:
        - boolean exists(): Indica si el fichero o directorio existe.
        - boolean canWrite(): Indica si se tiene permiso de escritura.
        - boolean canRead(): Indica si se tiene permiso de lectura.
        - boolean isFile(): Indica si es un fichero (no un directorio).
        - boolean isDirectory(): Indica si es un directorio.
        - boolean isAbsolute(): Indica si la ruta es absoluta.

    - Información específica:
        - long lastModified(): Devuelve la fecha de la última modificación en milisegundos desde la época Unix.
        - long length(): Devuelve el tamaño del fichero en bytes.

[Volver al Índice](#índice)

## Clases de Manejo de archivos

- Acceso secuencial:
    - Texto:
        - Escritura: FileWriter y PrintWriter
        - Lectura: FileReader

    - Binario:
        - Escritura: FileOutputStream
        - Lectura: FileInputStream

- Acceso aleatorio:
    - RandomAccessFile

Estas clases engloban una instancia de la clase File, permitiendo acceder al archivo en modo escritura o lectura.

[Volver al Índice](#índice)

## FileWriter

La clase FileWriter en Java es una de las clases más utilizadas para escribir caracteres en un archivo. A diferencia de las clases basadas en bytes como FileOutputStream, FileWriter está diseñada para manejar caracteres y trabaja a nivel de flujo de caracteres.

- Constructores:
```
FileWriter writer = new FileWriter("archivo.txt");
    - FileWriter writer = new FileWriter("archivo.txt", true); -> No se sobreescribe
    - FileWriter writer = new FileWriter("archivo.txt", false); -> Sobreescribe

File file = new File("archivo.txt");
FileWriter writer = new FileWriter(file);

File file = new File("archivo.txt");
    - FileWriter writer = new FileWriter(file, true); -> No se sobreescribe
    - FileWriter writer = new FileWriter(file, false); -> Sobreescribe

```

- Métodos principales:
    - write():
    Escribe en el archivo.
        ```
        fichero.write(65); -> Escribe el carácter 'A' (código Unicode 65)

        char[] chars = {'H', 'o', 'l', 'a'};
        fichero.write(chars); -> Escribe "Hola" en el archivo

        String cadena = "Hola Mundo";
        fichero.write(cadena);

        fichero.write("Hola Mundo"); -> Escribe "Hola Mundo" en el archivo

        writer.write("Hola Mundo", 0, 4); -> Escribe "Hola" en el archivo, desde la posición 0 a la 4


        ```

    - flush():
    Fuerza que todos los datos que están en el buffer del FileWriter se escriban en el archivo.
    Si estás usando buffering, el flush asegura que no quede nada pendiente de escribir.
        ```
        writer.flush();
        ```

    - close():
    Cierra el FileWriter y libera los recursos asociados a él.
    Es importante llamar a close() cuando hayas terminado de escribir en el archivo para asegurar que los datos se guarden correctamente y se liberen los recursos.
    ```
    writer.close();
    ```

[Volver al Índice](#índice)

## PrintWriter

La clase PrintWriter en Java es una clase que permite escribir datos en un archivo o en la consola de manera más conveniente y eficiente, con una variedad de métodos de impresión de texto que manejan tanto texto como caracteres de forma sencilla. Esta clase se encuentra en el paquete java.io y proporciona una forma más fácil de escribir datos que otros flujos de caracteres como FileWriter.
A partir de Java 5 se puede crear un objeto PrintWriter directamente a partir de un objeto File o de una ruta.

A diferencia de otras clases como FileWriter o BufferedWriter, PrintWriter está diseñada para imprimir de manera más conveniente y con más funcionalidades, como la posibilidad de formatear la salida y manejar automáticamente el cierre del flujo.
No lanza excepciones de I/O. Si ocurre un error durante la escritura, PrintWriter simplemente establece un flag de error interno, que se puede verificar posteriormente mediante el método checkError().
El flujo de salida de PrintWriter puede configurarse para que realice un "flush" automático cada vez que se escribe una línea. Esto asegura que los datos se escriben en el destino (archivo, consola, etc.) de manera inmediata.

- Constructores: 
```
PrintWriter writer = new PrintWriter("archivo.txt");

File file = new File("archivo.txt");
PrintWriter writer = new PrintWriter(file);

PrintWriter writer = new PrintWriter(new FileOutputStream("archivo.txt"));

PrintWriter writer = new PrintWriter(new FileOutputStream("archivo.txt"), true); -> Autoflush habilitado
```

- Métodos:
    - void print(): imprime texto sin salto de línea.
    - void println(): imprime texto seguido de un salto de línea.
    - PrintStream printf(): imprime texto formateado y devuelve el mismo flujo.
    - PrintStream format(): igual que printf, imprime con formato y devuelve el flujo.
    - void close(): cierra el flujo de salida.
    - boolean checkError(): indica si ha ocurrido un error en el flujo.

[Volver al Índice](#índice)

## InputStreamReader

InputStreamReader es una clase en Java que actúa como un puente entre un flujo de bytes (InputStream) y un flujo de caracteres (Reader). Convierte los bytes en caracteres según un conjunto de caracteres específico (codificación).

Se utiliza para leer datos de una fuente de entrada basada en bytes, como archivos, sockets o la entrada estándar (System.in).

Convierte los bytes en caracteres usando una codificación específica (por defecto, la del sistema).

Se usa junto con BufferedReader para mejorar la eficiencia en la lectura de datos.

```
public InputStreamReader(InputStream in);
    - Usa la codificación predeterminada del sistema.
```

```
try (InputStreamReader isr = new InputStreamReader(System.in);
    BufferedReader br = new BufferedReader(isr)) {

    System.out.println("Escribe algo y presiona Enter:");
    String input = br.readLine();
    System.out.println("Leíste: " + input);

} catch (IOException e) {
    e.printStackTrace();
}
        
```
La diferencia clave entre InputStreamReader y FileInputStream es que FileInputStream trabaja con bytes, mientras que InputStreamReader convierte bytes en caracteres.

FileInputStream → Si trabajas con archivos binarios (imágenes, videos, archivos comprimidos).

InputStreamReader → Si lees archivos de texto y quieres manejar correctamente la codificación.

Se usa para: 
- Leer archivos de texto desde un FileInputStream.

- Leer datos desde una red usando Socket.getInputStream().

- Leer datos de la entrada estándar (System.in).

Si necesitas una lectura más eficiente, se recomienda usar BufferedReader junto con InputStreamReader para mejorar el rendimiento al leer líneas completas.

[Volver al Índice](#índice)

## FileReader

FileReader es una clase en Java que se utiliza para leer archivos de texto. Es una subclase de InputStreamReader y facilita la lectura de archivos de texto sin necesidad de especificar una codificación (usa la predeterminada del sistema). Permite leer caracteres de un archivo sin necesidad de convertir bytes manualmente.

- Constructores:
```
FileReader fr = new FileReader("archivo.txt");


File file = new File("archivo.txt");
FileReader fr = new FileReader(file);

```

- Métodos principales:
    - read(): Lee un solo carácter del archivo y retorna un entero que representa el valor Unicode del carácter leído, o -1 si se ha alcanzado el final del archivo.
    - close(): Cierra el archivo y libera los recursos asociados. Siempre se debe cerrar el archivo para evitar fugas de memoria o bloqueo del archivo.
    - ready(): : Indica si el FileReader está listo para ser leído sin bloquear. Retorna true si se puede leer sin bloquear, false si no.

[Volver al Índice](#índice)

## BufferedWriter y BufferedReader

Trabajan con caracteres: Estas clases están diseñadas para leer y escribir texto. Usan el sistema de codificación de caracteres (por ejemplo, UTF-8) para manejar la conversión entre bytes y caracteres.

BufferedWriter se usa para escribir texto en un archivo de manera eficiente. En lugar de escribir carácter por carácter, almacena los datos en un buffer interno intermedio primero y los escribe en bloques en el archivo, reduciendo las operaciones de escritura en el disco. 

- Constructores:
```
BufferedWriter bw = new BufferedWriter(new FileWriter("archivo.txt"));
```

- Métodos Principales:
    - write()
    - newLine()
    - flush()
    - close()

BufferedReader se usa para leer texto de una fuente de entrada (como un archivo) de manera eficiente. . En lugar de leer carácter por carácter, almacena los datos en un buffer interno, lo que reduce el número de accesos al disco y mejora el rendimiento.

- Constructores:
```
BufferedReader br = new BufferedReader(new FileReader("archivo.txt"));
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
```

- Métodos Principales:
    - read()
    - readLine()
    - ready()
    - close()

> NOTA: La clase BufferedReader no necesita llamar al método flush() de forma explícita, ya que su propósito es leer datos, no escribir. 

>NOTA: flush() se utiliza para forzar la escritura de datos almacenados en el buffer hacia un destino de salida.

Normalmente, estas dos clases engloban objetos de la clase FileWriter y FileReader respectivamente, pero también pueden englobar cualquier Reader o Writer, no solo de archivos. Como InputStreamReader o StringWriter.

[Volver al Índice](#índice)

## FileInputStream

La clase FileInputStream es parte del paquete java.io y se utiliza para leer datos de archivos en formato de bytes. A diferencia de clases como FileReader, que se usan para leer caracteres, FileInputStream está diseñada para manejar datos binarios o archivos que no necesariamente están en formato de texto.

- Constructores:
```
FileInputStream fis = new FileInputStream("archivo.txt");

File file = new File("archivo.txt");
FileInputStream fis = new FileInputStream(file);

FileDescriptor fd = ...;
FileInputStream fis = new FileInputStream(fd);
```

- Métodos principales:
    - read()
    - skip()
    - available()
    - close()
    - mark()
    - reset()

[Volver al Índice](#índice)

## FileOutputStream

La clase FileOutputStream se encuentra en el paquete java.io y se utiliza para escribir datos en archivos en formato binario. Al igual que FileInputStream, se maneja a nivel de bytes, lo que la hace adecuada para escribir cualquier tipo de archivo, incluyendo archivos binarios (como imágenes o archivos de audio).

- Constructores:
```
FileOutputStream fos = new FileOutputStream("archivo.txt");

File file = new File("archivo.txt");
FileOutputStream fos = new FileOutputStream(file);

FileOutputStream fos = new FileOutputStream("archivo.txt", true); -> true añade y false sobreescribe

```

- Métodos principales:
    - write()
    - flush()
    - close()

>> NOTA: FileOutputStream no tiene un buffer interno que maneje la escritura de datos como lo hace un BufferedWriter o BufferedOutputStream.
Pero en Java, muchas clases de entrada y salida están optimizadas a un nivel inferior (a nivel del sistema operativo) y pueden utilizar buffers a un nivel más bajo de forma implícita para mejorar la eficiencia del proceso de escritura.

[Volver al Índice](#índice)

## BufferedInputStream y BuffereOutputStream


La diferencia principal entre BufferedInputStream/BufferedOutputStream y BufferedReader/BufferedWriter es que los primeros trabajan con bytes y los segundos con caracteres.

Trabajan con bytes: Estas clases son utilizadas para leer y escribir datos binarios (es decir, cualquier tipo de dato que no esté limitado a texto, como imágenes, archivos comprimidos, etc.).

La clase BufferedInputStream es una subclase de InputStream que proporciona un buffer de lectura para optimizar el proceso de leer datos desde un flujo de entrada (como un archivo).

- Constructores:
```
FileInputStream fis = new FileInputStream("archivo.txt");
BufferedInputStream bis = new BufferedInputStream(fis);

BufferedInputStream bis = new BufferedInputStream(fis, 8192); -> Tamaño del buffer de 8KB
```

- Métodos principales:
    - read()
    - available()
    - skip()
    - close()

La clase BufferedOutputStream es una subclase de OutputStream que proporciona un buffer de escritura para optimizar el proceso de escribir datos en un flujo de salida (como un archivo).

- Constructures: 
```
FileOutputStream fos = new FileOutputStream("archivo.txt");
BufferedOutputStream bos = new BufferedOutputStream(fos);

BufferedOutputStream bos = new BufferedOutputStream(fos, 8192); -> Buffer de 8KB
```

- Métodos principales:
    - write()
    - flush()
    - close()

[Volver al Índice](#índice)

## Uso de try/catch

El uso de try-catch en los métodos que manejan archivos es necesario cuando se trabajan con clases de entrada y salida (I/O) en Java, ya que muchas de estas operaciones pueden generar excepciones.

1. Abrir un archivo: Al intentar abrir un archivo (por ejemplo, usando FileInputStream, FileOutputStream, BufferedReader, BufferedWriter, etc.), es posible que el archivo no exista, no tenga los permisos necesarios, o haya otro error relacionado con el acceso al archivo. Por lo tanto, siempre debes usar try-catch al abrir archivos.

2. Leer y escribir en archivos: Las operaciones de lectura o escritura en archivos pueden lanzar excepciones si ocurren errores durante el proceso (por ejemplo, si el archivo se cierra inesperadamente o si no se tiene acceso al archivo).

3. Cerrar los flujos: Aunque generalmente se usa un bloque finally o un try-with-resources para cerrar los flujos, si no se hace correctamente, también pueden generarse excepciones relacionadas con el cierre del flujo.

- La sintaxis básica de un try-with-resources:
```
try (Recurso recurso = new Recurso()) {
    // Usa el recurso aquí (lectura, escritura, etc.)
} catch (Excepción e) {
    // Maneja las excepciones si las hay
} 
// El recurso se cierra automáticamente al salir del bloque try

```

- Lectura de archivo usando BufferedReader:
```
import java.io.*;

public class FileReaderExample {
    public static void main(String[] args) {
        BufferedReader reader = null;

        try {
            // Crear un BufferedReader para leer un archivo
            reader = new BufferedReader(new FileReader("archivo.txt"));
            
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line); // Imprime cada línea del archivo
            }
        } catch (IOException e) {
            // Captura cualquier IOException (por ejemplo, archivo no encontrado)
            System.out.println("Error al leer el archivo: " + e.getMessage());
        } finally {
            try {
                // Cerrar el flujo, asegurándose de que siempre se cierre
                if (reader != null) {
                    reader.close();
                }
            } catch (IOException e) {
                System.out.println("Error al cerrar el archivo: " + e.getMessage());
            }
        }
    }
}
```

- Escribir en un archivo usando BufferedWriter:
```
import java.io.*;

public class FileWriterExample {
    public static void main(String[] args) {
        BufferedWriter writer = null;

        try {
            // Crear un BufferedWriter para escribir en un archivo
            writer = new BufferedWriter(new FileWriter("archivo.txt"));
            writer.write("Hola, Mundo!");
        } catch (IOException e) {
            // Captura cualquier IOException (por ejemplo, problema al escribir)
            System.out.println("Error al escribir en el archivo: " + e.getMessage());
        } finally {
            try {
                // Cerrar el flujo, asegurándose de que siempre se cierre
                if (writer != null) {
                    writer.close();
                }
            } catch (IOException e) {
                System.out.println("Error al cerrar el archivo: " + e.getMessage());
            }
        }
    }
}
```
[Volver al Índice](#índice)

## Excepciones en el manejo de Archivos

Las excepciones más comunes que pueden ocurrir durante el manejo de archivos son:

- IOException: Es la excepción más general relacionada con problemas de entrada/salida. Puede ocurrir por problemas con los archivos o los flujos de datos (por ejemplo, archivo no encontrado, no hay permisos, etc.).

- FileNotFoundException: Es una subclase de IOException y se lanza cuando el archivo que se intenta abrir no existe.

[Volver al Índice](#índice)

---
---
---

# Introducción a las bases de datos (Unidad 2)

Una base de datos (BBDD) es un sistema estructurado para almacenar, organizar, gestionar y acceder a grandes cantidades de datos de manera eficiente. Su principal objetivo es permitir el almacenamiento y la recuperación de información de forma rápida, precisa y coherente, a medida que se actualizan, insertan o eliminan datos.

Las bases de datos son cruciales en una amplia variedad de aplicaciones, desde sistemas simples como una agenda personal, hasta sistemas empresariales más complejos que manejan grandes volúmenes de datos en sectores como comercio electrónico, banca, telecomunicaciones, salud y más.

Una base de datos se compone de varios elementos clave que trabajan en conjunto para proporcionar un sistema organizado y eficiente para la gestión de datos:

- Datos: Son los elementos fundamentales que se almacenan y gestionan en la base de datos. Estos datos pueden ser de diferentes tipos (texto, números, imágenes, etc.) y se organizan de manera estructurada en tablas, documentos o colecciones.

- Sistema de Gestión de Bases de Datos (DBMS): Es el software que permite la creación, administración, manipulación y mantenimiento de la base de datos. Actúa como intermediario entre el usuario y los datos. Algunos ejemplos de DBMS incluyen:
    - Relacionales: MySQL, PostgreSQL, Oracle, SQL Server.
    - No relacionales: MongoDB, Cassandra, Redis.

- Esquema: Es la estructura lógica que define cómo se organizan los datos y las relaciones entre ellos. El esquema puede incluir tablas (en bases de datos relacionales), colecciones (en bases de datos no relacionales), campos (columnas), relaciones, índices, restricciones (como claves primarias y foráneas), vistas, procedimientos almacenados, entre otros.

- Consultas: Son las instrucciones utilizadas para interactuar con los datos almacenados. Permiten recuperar, insertar, actualizar o eliminar datos. Estas consultas se escriben en un lenguaje especializado, como el Lenguaje de Consulta Estructurado (SQL) para bases de datos relacionales. Por ejemplo:

[Volver al Índice](#índice)

## Sistemas de Gestión (DBMS)

Un Sistema de Gestión de Bases de Datos (DBMS) es un software diseñado para manejar la creación, el acceso y la administración de bases de datos. Un DBMS facilita las operaciones de almacenamiento y recuperación de datos de manera eficiente y controlada.

Existen dos tipos principales de DBMS:

- DBMS Relacional: Estos sistemas organizan los datos en tablas (también llamadas relaciones) que están relacionadas entre sí mediante claves. El modelo relacional es el más común y usa el lenguaje SQL para interactuar con la base de datos.

    - Ejemplos: MySQL, PostgreSQL, Oracle Database.

- DBMS No Relacional: Estos sistemas almacenan los datos en formatos más flexibles, como documentos, pares clave-valor, o grafos. Están diseñados para manejar grandes volúmenes de datos no estructurados o semi-estructurados.

    - Ejemplos: MongoDB (documentos), Cassandra (columnares), Redis (clave-valor), Neo4j (grafos).

Características principales de un DBMS:
- Independencia de los datos: Un DBMS permite que los usuarios accedan a los datos sin preocuparse por cómo están almacenados físicamente.

- Seguridad: Los DBMS gestionan los permisos de acceso, asegurando que solo los usuarios autorizados puedan modificar o ver los datos.

- Redundancia mínima: A través de técnicas como la normalización, los DBMS reducen la duplicación de datos y mejoran la eficiencia del almacenamiento.

- Recuperación ante fallos: Un buen DBMS garantiza que los datos se puedan recuperar en caso de fallos del sistema, utilizando mecanismos como transacciones y backups.

- Rendimiento optimizado: Los DBMS implementan técnicas como índices, caché y optimización de consultas para asegurar un acceso rápido a los datos.

[Volver al Índice](#índice)

## Modelo de datos

Un modelo de datos es una representación abstracta de cómo los datos se organizan y se manipulan dentro de una base de datos. Es la forma en que se describe la estructura, las relaciones y las restricciones de los datos, y sirve como la base para la implementación del sistema de base de datos.

Los modelos de datos no son implementaciones físicas, sino representaciones conceptuales que guían el diseño y la implementación de la base de datos. Los modelos de datos permiten un acceso eficiente a la información y garantizan la integridad y coherencia de los datos.

Tipos de Modelos de Datos:

- Modelo Relacional: Los datos se organizan en tablas (también llamadas relaciones). Cada tabla consta de filas (registros) y columnas (atributos). Las relaciones entre tablas se establecen mediante claves primarias (para identificar de manera única cada fila) y claves foráneas (para referenciar filas en otras tablas).
Ventaja: Alta flexibilidad para consultas complejas.

    - Los datos se organizan en tablas con filas y columnas. Se utilizan claves primarias y foráneas para vincular las tablas.
        - Ejemplo: MySQL, PostgreSQL.

- Modelo No Relacional: Los datos no se organizan en tablas fijas como en los modelos relacionales, sino que se almacenan de manera más flexible. Los sistemas NoSQL pueden emplear diversos enfoques de almacenamiento, como documentos, claves-valor, columnas o grafos. Este modelo es particularmente útil para gestionar grandes volúmenes de datos no estructurados o semi-estructurados, proporcionando escalabilidad horizontal y flexibilidad en la estructura de los datos. Aunque muchos sistemas NoSQL no ofrecen transacciones con las propiedades ACID de manera predeterminada, algunos modelos transaccionales han incorporado estas garantías, como en MongoDB, que ofrece transacciones en varias colecciones, o en Cassandra, que implementa consistencia eventual.

    - Los datos no se organizan en tablas fijas, sino de manera más flexible, como documentos, claves-valor o grafos. Ideal para grandes volúmenes de datos no estructurados.
        - Ejemplo: MondoDB, Cassandra.

- Modelo de Red: Los datos se organizan en nodos y enlaces. Cada nodo puede tener múltiples enlaces a otros nodos, formando una estructura de red. Este modelo permite representar relaciones más complejas entre los datos, pero es más difícil de manejar y menos flexible que el modelo relacional.

    - Los datos se organizan en nodos conectados por enlaces. Es útil para representar relaciones complejas, pero más difícil de manejar que el modelo relacional.
        - Ejemplo: IDMS.

- Modelo Jerárquico: Los datos se organizan en una estructura jerárquica tipo árbol, donde cada elemento tiene un único "padre" y puede tener múltiples "hijos". Es adecuado para datos con una estructura jerárquica clara, pero no es flexible para representar relaciones más complejas.

    - Los datos se estructuran en una jerarquía de tipo árbol, con un único "padre" para cada "hijo". Bueno para datos con una estructura clara y fija.
        - Ejemplo: IMS DB.

- Modelo de Documento: Los datos se almacenan en documentos, que son representaciones semiestructuradas de los datos, típicamente en formatos como JSON o BSON. Es ideal para bases de datos NoSQL, donde los datos pueden no tener una estructura fija.

    - Los datos se almacenan en documentos, como JSON o BSON, que permiten representaciones más flexibles.
        - Ejemplo: MongoDB.

- Modelo de Grafos: Los datos se organizan como grafos, con nodos que representan entidades y aristas que representan relaciones entre ellas. Este modelo es particularmente útil para representar relaciones complejas, como las redes sociales, la web o las redes de tráfico.

    - Los datos se organizan en nodos (entidades) y aristas (relaciones), útiles para representar redes sociales o tráfico.
        - Ejemplo: Neo4j.

- Modelo Transaccional: Este modelo se enfoca en garantizar la correcta ejecución de operaciones sobre los datos mediante el cumplimiento de las propiedades ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad). Los datos se organizan en estructuras como tablas (en modelos relacionales) o documentos (en modelos NoSQL), pero lo que lo caracteriza es la gestión de las transacciones. Cada transacción se ejecuta de manera atómica, lo que significa que se ejecuta completamente o no se ejecuta en absoluto, asegurando la integridad de los datos. Este modelo es particularmente útil en sistemas que requieren fiabilidad en operaciones concurrentes, como los sistemas bancarios, aplicaciones de comercio electrónico y bases de datos empresariales, donde se realizan múltiples operaciones de lectura y escritura en un corto período de tiempo.

    - Se enfoca en garantizar que las operaciones de los datos se realicen correctamente, asegurando integridad mediante las propiedades ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad).
        - Ejemplo: MySQL, MongoDB.

[Volver al Índice](#índice)

## Tipos de Bases de Datos 

- Bases de datos estáticas: Son aquellas en las que los datos almacenados no sufren cambios frecuentes, o sólo experimentan modificaciones de forma esporádica. Estas bases de datos se emplean principalmente para almacenar información histórica, de referencia o cualquier tipo de dato que no necesite ser actualizado regularmente.

- Bases de datos dinámicas: En estas bases de datos, los datos están sujetos a cambios constantes, como inserciones, actualizaciones y eliminaciones de registros. Se utilizan principalmente en aplicaciones donde es crucial contar con datos actualizados en tiempo real.

- Bases de datos bibliográficas: Son colecciones estructuradas de información sobre publicaciones científicas, académicas, literarias y otras formas de obras escritas. Contienen referencias a artículos de revistas, libros, tesis, actas de conferencias, informes técnicos y otros tipos de documentos. No suelen contener los textos completos de los documentos, sino sus referencias, resúmenes, palabras clave y a veces enlaces al texto completo.

- Bases de datos de texto completo: Son colecciones estructuradas que almacenan no solo referencias y resúmenes de documentos, sino también el contenido completo de los textos. Permiten a los usuarios acceder, leer y buscar dentro de los documentos completos, proporcionando una fuente rica y detallada de la información.

[Volver al Índice](#índice)

## Bases de Datos MySQL y modelo Entidad-Relación (E/R)

Las bases de datos MySQL son relacionales y se basan en el modelo Entidad-Relación (E/R). En este modelo, los datos se organizan en entidades y las relaciones entre ellas. Este enfoque es ideal para representar sistemas que requieren almacenamiento estructurado y la capacidad de hacer consultas complejas sobre los datos.

El modelo Entidad-Relación (E/R) es un modelo conceptual o intermedio utilizado durante el proceso de diseño de una base de datos. Es una representación gráfica que describe las entidades relevantes en un sistema y las relaciones que existen entre ellas. Su propósito es representar de manera abstracta cómo se organizan y se relacionan los datos antes de que se conviertan en una base de datos real, ya sea en un modelo relacional o en otro tipo.

- Entidades y Relaciones
    - Entidades: Son los objetos o conceptos relevantes del sistema que se quieren representar en la base de datos. Cada entidad tiene atributos (también llamados propiedades) que describen las características de los elementos dentro de esa entidad. Por ejemplo, en una base de datos de una tienda, una entidad podría ser "Producto", y sus atributos podrían ser "nombre", "precio" y "stock".

    - Relaciones: Definen cómo las entidades interactúan entre sí. Las relaciones pueden ser de varios tipos, como "uno a muchos" o "muchos a muchos". Por ejemplo, una relación entre las entidades "Empleado" y "Departamento" podría ser de tipo "uno a muchos", ya que un departamento puede tener varios empleados, pero cada empleado solo pertenece a un departamento.

    - Cardinalidad de las relaciones: Describe cuántas instancias de una entidad pueden estar relacionadas con una instancia de otra entidad. Algunas relaciones comunes son:

        - Uno a uno (1:1): Una instancia de una entidad está relacionada con una sola instancia de otra entidad.

        - Uno a muchos (1:N): Una instancia de una entidad está relacionada con muchas instancias de otra entidad.

        - Muchos a muchos (N:M): Muchas instancias de una entidad están relacionadas con muchas instancias de otra entidad.

- Identificación de Entidades
    - Es crucial poder identificar de manera única cada registro dentro de una entidad. Esto se logra mediante claves primarias, que son identificadores únicos asignados a cada registro en una tabla. Por ejemplo, en una tabla de clientes, el "ID_cliente" podría ser la clave primaria.


- Conversión del Modelo E/R a Bases de Datos
    - El modelo Entidad-Relación tiene la ventaja de ser fácilmente convertible a una base de datos relacional. Las entidades se convierten en tablas, los atributos en columnas, y los registros de las entidades en filas de las tablas. Las claves primarias aseguran que cada registro sea único, y las relaciones entre las entidades se reflejan en las claves foráneas y en la estructura de las tablas.

- Ventajas del Modelo Relacional
    - Las bases de datos basadas en el modelo relacional, como MySQL, permiten consultas poderosas mediante SQL (Structured Query Language). Esto permite acceder, modificar y gestionar los datos de manera eficiente y flexible. Además, el modelo relacional garantiza la integridad y consistencia de los datos, ya que las relaciones entre tablas están claramente definidas.

[Volver al Índice](#índice)

## Modelo Lógico

El siguiente paso en la evolución del modelo Entidad-Relación (E/R) se llama el modelo lógico. En este paso, se toma el modelo E/R conceptual y se traduce a una forma más cercana a la implementación real en una base de datos, como el modelo relacional. Este proceso implica transformar las entidades, relaciones y cardinalidades del modelo E/R en tablas, claves, y restricciones en una base de datos.

Conversión de las relaciones en un modelo lógico según su cardinalidad:

    - Relación "Uno a Uno (1:1)": En este caso, las dos entidades involucradas en la relación pueden ser representadas por una sola tabla o, si es necesario, se pueden crear dos tablas con una clave foránea en cualquiera de ellas. La clave foránea será la que apunte hacia la otra tabla, ya que las instancias en ambas entidades pueden estar directamente relacionadas.
        - Ejemplo: Si tienes las entidades "Empleado" y "Pasaporte", donde cada empleado tiene un pasaporte y cada pasaporte pertenece a un solo empleado, puedes optar por crear una sola tabla "Empleado" con una columna "PasaporteID" que sea una clave foránea a la tabla "Pasaporte".

    - Relación "Uno a Muchos (1:N)": En este tipo de relación, se crea una tabla para cada entidad, y luego se agrega una clave foránea en la entidad del lado "muchos" que apunta a la entidad del lado "uno".
        - Ejemplo: Si tienes las entidades "Departamento" (uno) y "Empleado" (muchos), en el modelo lógico se crearán dos tablas. La tabla "Empleado" tendrá una clave foránea que apunta a la tabla "Departamento", indicando qué departamento pertenece cada empleado.
    
    - Relación "Muchos a Muchos (N:M)": Este tipo de relación requiere la creación de una tabla intermedia (o de unión) que contiene las claves primarias de ambas tablas que participan en la relación. La tabla intermedia actúa como un punto de conexión entre las dos entidades.
        - Ejemplo: Si tienes las entidades "Estudiantes" y "Cursos", y un estudiante puede estar inscrito en varios cursos y un curso puede tener varios estudiantes, se crea una tabla intermedia llamada "Inscripciones". Esta tabla tendría claves foráneas que apuntan a "Estudiantes" y "Cursos", como por ejemplo "EstudianteID" y "CursoID".

Resumen de cómo se convierten las relaciones según su cardinalidad:
    - Uno a Uno (1:1): Puede convertirse en una sola tabla o dos tablas con una clave foránea en una de ellas.

    - Uno a Muchos (1:N): Se crea una tabla para cada entidad, y la tabla del "muchos" tiene una clave foránea que apunta a la tabla del "uno".

    - Muchos a Muchos (N:M): Se crea una tabla intermedia que contiene claves foráneas de ambas tablas que están relacionadas.

Otros Elementos en la Conversión al Modelo Lógico
- Atributos: Los atributos de las entidades del modelo E/R se convierten en columnas dentro de las tablas en el modelo lógico.

- Claves Primarias: Cada tabla debe tener una clave primaria, que es un identificador único de cada registro. Las claves primarias de las entidades en el modelo E/R se convierten en claves primarias en las tablas.

- Claves Foráneas: Las claves foráneas se agregan a las tablas del modelo lógico para representar las relaciones entre las entidades (como se explicó en los puntos anteriores).

[Volver al Índice](#índice)

## SQL (Structured Query Language)

MySQL utiliza el lenguaje SQL para interactuar con la base de datos. SQL es un lenguaje estándar que permite realizar varias operaciones sobre los datos. Estas operaciones se dividen en diferentes categorías:

1. DDL (Data Definition Language): Se utiliza para definir y modificar la estructura de las bases de datos y sus objetos (tablas, índices, etc.). Las principales sentencias DDL son:

    - CREATE: Crear una nueva base de datos o tabla.
    - ALTER: Modificar la estructura de una tabla existente.
    - DROP: Eliminar una tabla o base de datos.
    - TRUNCATE: Eliminar todos los registros de una tabla.
    - RENAME: Cambiar el nombre de una tabla o base de datos.

2. DML (Data Manipulation Language): Se utiliza para manipular los datos dentro de las tablas. Las principales sentencias DML son:

    - SELECT: Recuperar datos de una o más tablas.
    - INSERT: Insertar nuevos registros en una tabla.
    - UPDATE: Modificar registros existentes en una tabla.
    - DELETE: Eliminar registros de una tabla.

3. DCL (Data Control Language): Se utiliza para controlar el acceso a los datos. Las principales sentencias DCL son:

    - GRANT: Otorgar permisos a los usuarios.
    - REVOKE: Revocar permisos previamente otorgados.

4. TCL (Transaction Control Language): Se utiliza para gestionar transacciones en la base de datos, asegurando que las operaciones se realicen de manera atómica y consistente. Las principales sentencias TCL son:

    - COMMIT: Confirmar los cambios realizados en la base de datos.
    - ROLLBACK: Revertir los cambios realizados en la base de datos en una transacción.

El CRUD cubre las operaciones esenciales para trabajar con datos en una base de datos, mientras que el SQL proporciona el lenguaje y las sentencias específicas para realizar esas operaciones.

- C (Create).
- R (Read).
- U (Update).
- D (Delete).

[Volver al Índice](#índice)

---
---
---

# Conectores a SGBD (Unidad 3)

Los conectores a SGBD (Sistemas de Gestión de Bases de Datos) o  DBMS (Database Management System) son herramientas o bibliotecas de software que permiten que una aplicación o sistema interactúe con un SGBD para acceder y manipular los datos almacenados en la base de datos. Estos conectores actúan como intermediarios entre la aplicación y el SGBD, facilitando la comunicación mediante protocolos específicos.

En términos más simples, un conector a un SGBD es un conjunto de funciones o métodos que permiten a los desarrolladores de aplicaciones conectarse a bases de datos para realizar operaciones de lectura, escritura, actualización y eliminación (operaciones CRUD) de datos.

Funciones principales de los conectores a SGBD:

1. Conexión a la base de datos: El conector establece la conexión entre la aplicación y la base de datos. Esto incluye la autenticación del usuario, la validación de las credenciales y la conexión a la base de datos.

2. Ejecución de consultas: Los conectores permiten enviar consultas SQL a la base de datos para recuperar, modificar o eliminar datos. Las consultas pueden ser de tipo SELECT, INSERT, UPDATE y DELETE.

3. Manejo de errores: Los conectores gestionan los errores que puedan ocurrir durante las interacciones con la base de datos, como problemas de conexión, errores de sintaxis en las consultas o violaciones de restricciones.

4. Manejo de transacciones: Los conectores también permiten el manejo de transacciones. Esto incluye operaciones como el commit (confirmar cambios) o rollback (revertir cambios), lo que asegura la consistencia de los datos.

5. Cierre de la conexión: Después de que se haya completado la interacción con la base de datos, el conector cierra la conexión para liberar recursos y evitar problemas de rendimiento.

[Volver al Índice](#índice)

## JDBC (Java Database Connectivity)

Es una API de Java que permite a las aplicaciones Java interactuar con bases de datos. JDBC define un conjunto de interfaces y clases que permiten realizar operaciones estándar sobre bases de datos, como conectar, consultar, actualizar y gestionar los resultados de las consultas.

JDBC no se encarga de la implementación específica de la conexión a la base de datos. Esta tarea es realizada por los drivers JDBC, que son conectores específicos para cada base de datos. Los drivers JDBC implementan la API de JDBC y permiten que la API interactúe correctamente con un SGBD en particular, gestionando la comunicación y las operaciones en la base de datos.

>> NOTA: Una API (Interfaz de Programación de Aplicaciones, Application Programming Interface) es un conjunto de reglas, protocolos y herramientas que permite que diferentes aplicaciones o componentes de software se comuniquen entre sí. Básicamente, una API define cómo los programas interactúan con otros sistemas o servicios, especificando cómo se deben realizar las solicitudes y cómo se van a devolver las respuestas. Las APIs permiten que un software acceda a las funcionalidades de otro software o servicio sin necesidad de conocer su implementación interna. Es como un "puente" que conecta diferentes sistemas.

- Ejemplo conexión con un SGBD desde Java con la API JDBC:
```
Connection con = DriverManager.getConnection("jdbc::mysql://localhost:3306/miBase", "usuario", "contraseña");

Statement stmt = con.createStatement();

ResultSet rs = stmt.executeQuery("SELECT * FROM personas");

while(rs.next()){
    System.out.println(rs.getString("nombre"));
}
```

1. Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/miBase", "usuario", "contraseña");
    - DriverManager.getConnection(): Este método se utiliza para establecer una conexión con la base de datos. Recibe como parámetros una URL de conexión, junto con el nombre de usuario y la contraseña.

    - "jdbc:mysql://localhost:3306/miBase": La URL de conexión especifica el tipo de base de datos (jdbc:mysql) y proporciona información sobre la ubicación del servidor de base de datos. En este caso, está indicando que la base de datos se encuentra en localhost (el mismo equipo donde se está ejecutando la aplicación Java), en el puerto 3306 (que es el puerto predeterminado para MySQL), y que se conectará a la base de datos llamada miBase.

    - "usuario" y "contraseña": Estos son los datos de autenticación para conectar con la base de datos. Son los credenciales que MySQL requiere para acceder a la base de datos.

    - La variable con almacena la conexión que se ha establecido con la base de datos.

2. Statement stmt = con.createStatement();
    - con.createStatement(): Este método se utiliza para crear un objeto Statement, que es utilizado para ejecutar consultas SQL. El Statement representa una declaración SQL que se enviará al SGBD.

    - El objeto stmt se utiliza luego para ejecutar las consultas sobre la base de datos. En este caso, el Statement es el encargado de ejecutar la consulta que se encuentra en la siguiente línea.

3. ResultSet rs = stmt.executeQuery("SELECT * FROM personas");
    - stmt.executeQuery(): Este método ejecuta una consulta SQL de tipo SELECT, que recupera datos de la base de datos. La consulta "SELECT * FROM personas" recupera todos los registros de la tabla personas.

    - ResultSet rs: El método executeQuery devuelve un objeto ResultSet que contiene los resultados de la consulta. El ResultSet es básicamente una tabla de datos que puedes recorrer y procesar.

    - En este caso, rs contiene las filas de la tabla personas devueltas por la consulta SELECT.

4. while(rs.next())
    - rs.next(): Este método avanza el cursor del ResultSet a la siguiente fila. Devuelve true si hay una fila más para leer y false si ya no quedan filas.

5. System.out.println(rs.getString("nombre"));
    - rs.getString("nombre"): Este método obtiene el valor de la columna nombre de la fila actual del ResultSet. El nombre de la columna se pasa como parámetro al método.

- Ejemplo conexión con ODBC (Open Database Connectivity):
```
string connectionString = "DSN=myDataSource;UID=usuario;PWD=contraseña";

using(OdbcConnection con = new OdbcConnection(connectionString)){
    con.Open();
    OdbcCommand cmd = new OdbcCommand("SELECT * FROM personas", con);
    OdbcDataReader reader = cmd.ExecuteReader();

    while(reader.Read()){
        Console.WriteLine(reader["nombre"].ToString());
    }
}
```

- Ejemplo conexión con ORM (Object-Relational Mapping):
```
Session session = sessionFactory.openSession();

Transaction tx = session.beginTransaction();

List<Personas> personas = session.createquery("FROM Personas").list();

for(Personas p: personas){
    System.out.println(p.getNombre());
}

tx.commit();
session.close();
```

- Ejemplo conexión con Entity Framework (C#):
```
using(var context = new MiBaseContext()){
    var personas = context.Personas.ToList();
    foreach(var personas in personas){
        Console.WriteLine(personas.Nombre);
    }
}
```

[Volver al Índice](#índice)

## Tipos de Conectores JDBC

Puesto que JDBC es una especificación JavaSoft estándar, un programa Java que utilice esta API puede conectar con cualquier sistema de gestión de bases de datos (SGBD) siempre y cuando haya un controlador para dicho SGBD.

Un controlador JDBC es un componente que actúa como intermediario entre tu aplicación Java y la base de datos. El controlador implementa las clases y las interfaces de JDBC, que son las que permiten que tu programa Java se comunique con la base de datos.

    - El programa Java hace una solicitud usando la API JDBC.

    - El DriverManager de JDBC carga el controlador adecuado para ese SGBD.

    - Luego, el controlador convierte esas solicitudes Java (en formato JDBC) en algo que el SGBD pueda entender.

Existen cuatro tipos de controladores JDBC que se utilizan dependiendo de la arquitectura y el tipo de conexión que necesites. Cada tipo de controlador tiene sus propias características y ventajas:

1. Tipo 1 - Puente JDBC-ODBC más controlador ODBC: Este tipo de controlador convierte las llamadas de la API JDBC en llamadas de ODBC (Open Database Connectivity), que es otro estándar de conexión con bases de datos.

El controlador JDBC-ODBC es un "puente" que traduce las solicitudes de JDBC a ODBC, y luego ODBC pasa esas solicitudes al controlador ODBC.

Problemas: Necesita que se instale y se configure un controlador ODBC en el cliente, lo que puede ser problemático en algunos sistemas y puede ser más lento.

2. Tipo 2 - API nativa, parcialmente controlador Java: Este controlador convierte las llamadas JDBC a llamadas específicas del cliente (API) de un SGBD determinado.

Por ejemplo, si estás utilizando un controlador JDBC para Oracle, este controlador usa las API nativas de Oracle para comunicarse con la base de datos de Oracle.

Problemas: Necesita código nativo específico para cada sistema, lo que significa que debes tener un controlador específico para cada plataforma y cada base de datos. Esto puede ser más complejo y no es tan flexible.

3. Tipo 3 - JDBC-Net, controlador Java puro: Este controlador convierte las solicitudes JDBC en llamadas que se envían a un servidor intermedio (un servidor de nivel medio).

Este servidor intermedio luego convierte las llamadas en un protocolo de red que el SGBD entiende, y pasa esas llamadas a la base de datos.

Ventajas: No necesita un controlador nativo para cada base de datos. Permite que un cliente Java se conecte a múltiples SGBD usando el mismo servidor intermedio.

Problemas: Aún necesita un servidor adicional que actúe como intermediario.

4. Tipo 4 - Protocolo nativo, controlador Java puro: Este es el controlador más eficiente. Convierte directamente las llamadas JDBC a un protocolo de red específico para el SGBD sin necesidad de un servidor intermedio ni un controlador nativo.

Por ejemplo, si estás utilizando MySQL, este controlador convierte directamente las solicitudes JDBC a un protocolo que MySQL entiende, y se comunica directamente con el servidor de la base de datos.

Ventajas: Es el más rápido y eficiente porque se conecta directamente al SGBD sin pasos intermedios. Además, es un controlador 100% en Java, por lo que es plataforma independiente.

Problemas: Puede no ser compatible con todas las bases de datos, ya que está diseñado específicamente para un SGBD.

| Tipo de controlador | Descripción | Ventajas | Desventajas |
|---------------------|-------------|----------|-------------|
| Tipo 1              | JDBC-ODBC (puente) | Compatible con muchos SGBD | Depende de ODBC, lento, necesita configuración adicional |
| Tipo 2              | API nativa (parcialmente en Java) | Más rápido que el Tipo 1 | Necesita controladores específicos para cada base de datos y sistema |
| Tipo 3              | JDBC-Net (servidor intermedio) | No necesita código nativo | Necesita un servidor intermedio |
| Tipo 4              | Protocolo nativo (Java puro) | Más rápido y eficiente | Solo funciona con el SGBD que soporta ese protocolo |

Diferencia entre Controlador JDBC y Conector JDBC:
    - Un controlador JDBC es un componente específico que implementa la especificación JDBC (Java Database Connectivity). Su tarea principal es traducir las solicitudes que hace un programa Java utilizando la API JDBC a un formato que el SGBD pueda entender.
    Existen diferentes tipos de controladores JDBC, como te mencioné anteriormente, y estos controladores están diseñados para que un programa Java pueda interactuar con cualquier base de datos, siempre y cuando haya un controlador adecuado para esa base de datos.

    - El término conector de SGBD suele usarse de manera más general. Un conector es cualquier tipo de software o interfaz que permite la conexión entre una aplicación (en este caso Java) y un SGBD. Puede referirse a varios tipos de implementaciones, y el controlador JDBC es un tipo de conector.

Controlador JDBC es un tipo específico de conector utilizado en el contexto de Java para conectar con bases de datos.

Conector de SGBD es un término más amplio y puede incluir diferentes tipos de software que permiten conectar aplicaciones con bases de datos, como drivers nativos o APIs específicas para otros lenguajes de programación.

En la práctica, un controlador JDBC es, por tanto, un conector en el ecosistema de Java, pero no todos los conectores son controladores JDBC. Un conector puede ser cualquier tipo de interfaz entre una base de datos y una aplicación, no necesariamente relacionada con JDBC.

>> NOTA: Las llamadas de la API son solicitudes que un programa o aplicación hace para utilizar las funcionalidades o servicios proporcionados por otra aplicación, sistema o biblioteca. Por ejemplo, si estás trabajando con una API que permite acceder a una base de datos a través de JDBC (Java Database Connectivity), tu programa Java hace llamadas de API JDBC para realizar tareas como conectar a la base de datos, realizar una consulta SQL o actualizar o eliminar datos.

[Volver al Índice](#índice)

## Proceso Consulta con JDBC

El proceso está compuesto de los siguientes pasos:

    1. Establecer conexión con la BBDD

    2. Crear un objeto Statement

    3. Ejecutar una sentencia SQL

    4. Leer el resultSet

1. Se establece conexión con la base de datos:
    ```
    jdbc::mysql://localhost:9999/gestionPedidos -> Con el SGBD de MySQL

    jdbc:odbc:DSN_gestionPedidos -> Con el SGBD mediante ODBC

    jdbc:oracle:juan@servidor:9999:gestionPedidos
    ```

2. Crear un objeto Statement a partir del objeto Connection

3. Lanzar una sentencia SQL con executeQuery y guardarla en un objeto ResultSet

4. Leer el ResultSet

Ejemplo:

- Se crea la base de datos

- Descargamos el controlador JDBC

- Dentro de nuestro archivo java, creamos la cadena de conexión:

```
import java.sql.DriveManager;
import com.mysql.jdbc.*;
import java.sql.*;

public static void main (String[]args){
try{
Connection miCon = driverManager.getConnection("jdbc:mysql://localhost:3306/gestionpedidos", "root", "");
```

- Creamos el statement
```
Statement miSt= miCon.createStatement();
```

- Ejecutar sentencia SQL
```
ResultSet miRs = miSt.executeQuery("SELECT * FROM PRODUCTOS");
```

- Leer el resultset
```
while(miRs.next()){
    System.out.println(miRs.getString(1) + " " + miRs.getString(3));
    miCon.close();
}
catch(Exception e){
    System.out.println("No se ha conectado");
    e.printStackTrace();
}
}
```

> NOTA: es importante cerrar la conexión al finalizar

[Volver al Índice](#índice)

## Ejemplos de consultas básicas

- Borrar un registro (DELETE)
```
Statement miSt = miCon.createStatement();

String inSQL = "DELETE FROM PRODUCTOS WHERE CODIGOARTICULO='AR45'";
miSt.executeUpdate(inSQL);

miCon.close();
```

> NOTA: el método executeQuery() se utiliza para consultas que devuelven un conjunto de resultados, mientras que executeUpdate() se usa para operaciones que modifican la base de datos, devolviendo un número entero referenciando el éxito de la operación.

- Modificar un registro (UPDATE)
```
String inSQL = "UPDATE PRODUCTOS SET PRECIO=70 WHERE CODIGOARTICULO='AR45'";
miSt.executeUpdate(inSQL);

miCon.close();
```

- Insertar un registro (INSERT)
```
String inSQL = "INSERT INTO PRODUCTOS (CODIGOARTICULO, NOMBREARTICULO, PRECIO) VALUES ('AR45', "LIMPIA CRISTALES", 90);
miSt.eecuteUpdate(inSQL);

miCon.close();
```

[Volver al Índice](#índice)

---
--- 
---

# Herramientas de mapeo Objeto-Relacional JPA (Unidad 4)

## JavaBeans

Un JavaBean es una clase en Java que sigue ciertas reglas y convenciones para encapsular datos y hacerlos fácilmente reutilizables en aplicaciones Java, especialmente en entornos empresariales y frameworks como Java EE, Spring y JSP.

Básicamente, un JavaBean es una estructura de clase diseñada para representar objetos con atributos privados y métodos públicos que permiten acceder y modificar esos atributos de forma controlada.

[Volver al Índice](#índice)

## Definición y Características

Para que una clase sea considerada un JavaBean, debe cumplir con estas reglas:

- Encapsulación de Datos:
Los atributos de la clase JavaBean deben ser privados y solo accesibles mediante métodos públicos llamados getters y setters. Esto sigue el principio de encapsulación, protegiendo los datos y permitiendo su manipulación de forma controlada.

- Constructor sin Argumentos:
Un JavaBean debe tener un constructor público sin argumentos. Esto permite que herramientas de desarrollo visual y frameworks creen instancias de la clase sin necesidad de parámetros.

- Implementación de Serializable:
Los JavaBeans deben implementar la interfaz Serializable, lo que permite que sus objetos sean convertidos en un flujo de bytes y almacenados en archivos o transmitidos a través de una red.

- Cumplimiento de Convenciones:
Los JavaBeans deben seguir nombres estándar para garantizar su compatibilidad con herramientas y frameworks:
    - Los getters deben empezar con get + NombreAtributo
    - Los setters deben empezar con set + NombreAtributo
    - Si el atributo es booleano, el getter puede empezar con is en lugar de get

>NOTA: Serializable es una interfaz de marcado en Java (no tiene métodos) que indica que un objeto puede convertirse en un flujo de bytes. Esto permite guardar el estado del objeto en archivos, bases de datos o enviarlo a través de una red.

>NOTA: el atributo serialVersionUID es un número de versión único que se utiliza en la serialización de objetos en Java para garantizar la compatibilidad entre diferentes versiones de una clase. Cuando un objeto es serializado (convertido en bytes) y deserializado (reconstruido desde bytes), Java usa serialVersionUID para verificar si la clase que intenta leer el objeto es compatible con la versión de la clase que se usó para guardarlo.

Ejemplo:
```
import java.io.Serializable;
import java.time.LocalDateTime;

public class Llamada implements Serializable{
    private static final long serialVersionUID = 2736782367823L;

    private LocalDateTime fechaHora;
    private String emisor;
    private String motivo;

    public Llamada(){
        this.fechaHora = LocalDateTime.now();
    }

    public LocalDateTime getFechaHora(){
        return fechaHora;
    }

    public void setFechaHora(LocalDateTime fechaHora){
        this.fechaHora = fechaHora;
    }

    public String getEmisor(){
        return emisor;
    }

    public void setEmisor(String emisor){
        this.emisor = emisor;
    }

    public String getMotivo(){
        return motivo;
    }

    public setMotivo(){
        this.motivo = motivo;
    }

    public String toString(){
        return this.emisor + " llamo el " + this.fechaHora + " para " + this.motivo;
    }
}
```
[Volver al Índice](#índice)

## Ventajas

- Reutilización y Modularidad:
Permite la creación de componentes reutilizables y modulares que pueden ser ensamblados en aplicaciónes más complejas, lo que significa que una clase JavaBean puede usarse en diferentes aplicaciones sin necesidad de modificar su código.

- Integración con Herramientas:
Son compatibles con herramientas de desarrollo visual y frameworks (como NetBeans o Eclipse), lo que facilita la configuración y manipulación de componentes gráficos dentro de un entorno de desarrollo.

- Facilidad de Mantenimiento: 
La separación de  los datos de la lógica de negocio mediante el uso de métodos getter y setter, lo que hace que el código sea más claro y fácil de modificar o extender en el futuro.

- Compatibilidad con Tecnologías Java:
Se integran perfectamente con otras tecnologías del ecosistema Java, como JSPs, Servlets y frameworks de persistencia como JPA.

[Volver al Índice](#índice)

## Mapeo Objeto-Relacional (ORM)

Los sistemas de bases de datos relacionales (RDBMS) organizan la información en tablas relacionadas entre sí, donde cada fila representa un registro, y cada tabla tiene una clave primaria que la identifica de forma única.

Por otro lado, en Java y la Programación Orientada a Objetos (POO), la información se modela a través de objetos, los cuales contienen atributos (datos) y métodos (acciones). En lugar de tablas, tenemos clases que representan entidades del mundo real, y los objetos de estas clases interactúan entre sí.

Dado que las bases de datos relacionales y los programas Java manejan los datos de manera diferente, se necesita un mecanismo para hacerlos compatibles.  El Mapeo Objeto-Relacional (ORM, Object-Relational Mapping) es un proceso que convierte los datos almacenados en una base de datos relacional en objetos de Java y viceversa.

El objetivo es hacer que la interacción con bases de datos sea más natural en Java, evitando la escritura manual de consultas SQL. El Mapeo Objeto-Relacional (ORM) permite a los desarrolladores Java trabajar con bases de datos de manera más natural, transformando tablas en objetos y registros en instancias de clases.

1. Se parte del Modelo Entidad-Relación de la base de datos.

2. Se crean clases Java que representan esas entidades.

3. Se usa un framework ORM (como Hibernate o JPA) para convertir automáticamente los registros de la BD en objetos Java.

Cuando usamos ORM, se crea una base de datos orientada a objetos virtual en memoria. Esto significa que podemos trabajar con objetos Java sin necesidad de manipular directamente las tablas de la BD.

Ejemplo:
```
import java.io.Serializable;
import javax.persistence..*;
import java.util.List;

@Entity
@NameQuery(name="Cliente.findAll", query="SELECT c FROM Cliente c")
public class Cliente implements Serializable{
    private static final long serialVersionUID = 1L;

    @Id
    private String nif;
    private String ciudad;
    private String domicilio;
    private String nombre;
    private String tlf;

    //bi-directional many-to-one association to Factura
    @OneToMany(mappedBy="cliente")
    private List<Factura> facturas;

    public Cliente(){

    }
    public String getNif(){
        return this.nif;
    }

    //... Getters y Setters

    public List<Factura> getFacturas(){
        return this.facturas;
    }

    public void setFacturas(List<Factura> facturas){
        this.facturas = facturas;
    }

    public Factura addFactura(Factura factura){
        getFacturas().add(factura);
        factura.setCliente(this);
        return factura;
    }

    public Factura removeFactura(Factura factura){
        getFacturas().remove(factura);
        factura.setCliente(null);
        return factura;
    }
}
```

## Ventajas de usar ORM

- Programación más intuitiva:
    - Se puede trabajar con objetos en lugar de escribir SQL manualmente.
    - Se mantiene la filosofía de POO, lo que hace el código más limpio y modular.

- Independencia del motor de base de datos
    - Un mismo código ORM puede funcionar con MySQL, PostgreSQL, Oracle, etc., sin modificaciones.

- Seguridad y reducción de errores
    - Al evitar SQL manual, se minimizan riesgos como inyección SQL.
    - El ORM maneja automáticamente la validación de datos.

- Facilidad en el mantenimiento y escalabilidad
    - Si cambia la estructura de la BD, solo se ajustan las clases Java sin modificar todo el código.

[Volver al Índice](#índice)

## Anotaciones

Las anotaciones en Java son una forma de añadir metadatos a tu código. Estos metadatos no cambian la lógica del código, pero pueden ser utilizados por el compilador, herramientas de desarrollo y frameworks en tiempo de compilación o en tiempo de ejecución para realizar diversas tareas, como validación, generación de código, configuración, etc.

Las anotaciones son precedidas por el símbolo @ y se pueden aplicar a declaraciones de clases, métodos, campos, parámetros, variables locales, etc.
    - @Override @Deprecated @SuppressWarnings

Las meta-anotaciones se utilizan para definir el comportamiento de otras anotaciones.
    - @Retention @Target @Documented @Inherit

[Volver al Índice](#índice)

## Tipos de Anotaciones

- Anotaciones Incorporadas: vienen con el JDK.
- Anotaciones Personalizadas: definidas por los usuarios para propósitos específicos. Se pueden crear según las necesidades del flujo del código.

Ejemplo:
```
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;
import java.lang.annotation.ElementType;

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface MyAnnotation{
    String value();
}

// Uso de la anotación personalizada
public class MyClass{
    @MyAnnotation(value = "Hello")
    public void myMethod(){
        // ...
    }
}
```

[Volver al Índice](#índice)

## Los Frameworks ORM

Un Framework ORM (Object-Relational Mapping) es una herramienta de software que facilita la interacción entre aplicaciones y bases de datos relacionales. Su función principal es mapear las estructuras de una base de datos a objetos en el lenguaje de programación utilizado, permitiendo que los desarrolladores trabajen con bases de datos de forma más intuitiva y eficiente.

1. Mapeo de estructuras: Convierte tablas y registros en clases y objetos.

2.  Gestión de operaciones CRUD: Inserción, consulta, actualización y eliminación de datos mediante métodos de Java en lugar de SQL.

3. Sincronización: Cuando se actualizan los objetos en la aplicación, el ORM se encarga de reflejar los cambios en la base de datos.

Los frameworks ORM (Object-Relational Mapping) funcionan como una capa intermedia entre la base de datos relacional y la aplicación. Su principal tarea es convertir las tablas físicas de la base de datos en objetos Java, permitiendo que los desarrolladores trabajen con los datos de manera más intuitiva y orientada a objetos.

Cuando utilizamos un ORM, la base de datos relacional sigue existiendo en el sistema de almacenamiento, pero dentro de la aplicación trabajamos con una representación orientada a objetos conocida como Base de Datos virtual.

Una vez que los datos han sido mapeados a objetos, la aplicación puede modificar, agregar o eliminar información simplemente manipulando estos objetos. Sin embargo, estos cambios no se reflejan automáticamente en la base de datos; es el Framework ORM el que se encarga de sincronizar la información cuando se le indica hacerlo.

[Volver al Índice](#índice)

## Java Persistence API (JPA)

Java Persistence API (JPA) es una especificación de Java diseñada para gestionar la persistencia de datos en aplicaciones basadas en este lenguaje. Está definida en el paquete javax.persistence y proporciona un conjunto de reglas y anotaciones para trabajar con bases de datos relacionales utilizando una arquitectura orientada a objetos.

Es importante destacar que JPA no es una implementación en sí misma, sino una especificación que establece las reglas y el comportamiento esperado para la gestión de la persistencia de datos. Para poder utilizar JPA en una aplicación, se necesita una implementación concreta que proporcione la funcionalidad definida en la especificación.

Existen diversas implementaciones que cumplen con la especificación JPA y permiten su uso en aplicaciones Java. Algunas de las más populares son:

- EclipseLink

- Hibernate

- MyBatis

Java Persistence API (JPA) permite gestionar los datos relacionales en aplicaciones Java mediante el uso de objetos persistentes. Proporciona una forma estándar de mapear las entidades de una base de datos a objetos Java, permitiendo trabajar con datos de manera más natural y orientada a objetos.

- Mapeo de Entidades: conversión de las tablas de la base de datos física en clases Java (Entidades), cuyas columnas se traducen en atributos de la clase. Se encuentran dentro de la carpeta src del proyecto, dentro del paquete model.

- Consultas: JPA proporciona un lenguaje de consulta llamado JPQL (Java Persistence Query Language) que permite realizar consultas de manera similar a SQL, utilizando clases (Entidades) en lugar de tablas.

- Gestión de Relaciones: JPA soporta relaciones entre entidades uno a uno, uno a muchos, muchos a uno y muchos a muchos.

- Gestión del Ciclo de Vida: gestiona el ciclo de vida de las entidades con operaciones como persistencia, actualización, eliminación y consulta de entidades.

[Volver al Índice](#índice)

## Diferencia entre una especificación y una API

Una especificación es un conjunto de reglas, directrices y estándares que definen cómo se debe hacer algo, sin dar los detalles de la implementación concreta. En otras palabras, una especificación establece qué debe hacer algo, pero no necesariamente cómo debe hacerlo.

En el caso de JPA, la especificación define cómo deberían ser las operaciones de persistencia de datos en Java, como almacenar objetos en una base de datos y recuperarlos, pero no prescribe cómo exactamente debe implementarse. Deja esa parte en manos de los proveedores de persistencia (como Hibernate, EclipseLink, etc.).


Una API (Interfaz de Programación de Aplicaciones) es un conjunto de interfaces o funciones que puedes usar para interactuar con una aplicación o una biblioteca. En el caso de JPA, la API es el conjunto de interfaces que proporcionan los métodos que permiten interactuar con la base de datos de manera orientada a objetos (como EntityManager, EntityManagerFactory, etc.).

Así que, mientras que la especificación establece los principios y comportamientos que se deben seguir, la API es la colección de interfaces que proporcionan las funcionalidades necesarias para implementar esos principios en el código.

- Resumen: 

    - Especificación: El conjunto de reglas, directrices y estándares que describen cómo debe ser un producto o servicio.

    - API: El conjunto de interfaces o herramientas concretas que los desarrolladores pueden utilizar para interactuar con esa especificación.

¿Por qué JPA es una especificación y no solo una API?
La especificación de JPA se define por la Java Community Process (JCP), una comunidad de desarrollo que establece estándares para la plataforma Java. Esto asegura que JPA sea un estándar abierto que pueda ser implementado de diversas maneras por diferentes proveedores de persistencia.

- JPA es una especificación porque define cómo debe funcionar la persistencia de objetos en Java, pero no implementa realmente ese funcionamiento.

- JPA es una API porque ofrece las interfaces que se deben utilizar para interactuar con la persistencia en Java. Estas interfaces te permiten trabajar con datos, pero los detalles de cómo se almacenan esos datos son dejados a la implementación concreta.

[Volver al Índice](#índice)

## Ventajas del JPA

- Productividad: Simplifica el desarrollo.

- Portabilidad: Al ser una especificación estándar, permite cambiar de proveedor JPA (como Hibernate, Eclipse Link) sin cambios significativos en el código.

- Integración: Se integra fácilmente con otros frameworks y tecnologías Java, como Java EE y Java SE.

- Mantenimiento: Facilita el mantenimiento del código al centralizar la lógica de acceso a datos.

[Volver al Índice](#índice)

## Componentes del JPA

- Entidad: Clase de Java que representa una tabla. Cada instancia de la clase, representa una fila o registro de dicha tabla.

- Entity Manager: Es la principal interfaz de la API utilizada para interactuar con la persistencia. Se utiliza para operaciones CRUD.

- Persistencia Unit: Configuración dentro del archivo persistence.xml dentro de la carpeta META-INF, que define define varios detalles sobre el proyecto y cómo se relaciona la base de datos virtual con la física.

- JPQL: Lenguaje de consulta orientado a objetos que se aplica sobre la base de datos virtual.

> NOTA: Un API es un conjunto de interfaces y herramientas que permite que diferentes programas o sistemas interactúen entre sí.

[Volver al Índice](#índice)

## Persistence.xml

Es un archivo crucial en la especificación JPA, que define la unidad de persistencia (persistence unit) y sus propiedades, tales como la conexión con la base de datos, el proveedor de JPA, las clases de entidad y otras configuraciones relacionadas con la persistencia.

La unidad de persistencia va encerrada entre las etiquetas:

```
<persistence-unit name="nombreUnidadPersistencia">

...

</persistence-unit>
```

Ejemplo:
```
<persistence xmlns="http://java.sun.com/xml/ns/persistence"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://java.sun.com/xml/ns/persistence
                                 http://java.sun.com/xml/ns/persistence/persistence_2_0.xsd">
    <persistence-unit name="miUnidadDePersistencia">
        <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>
        <class>com.ejemplo.Cliente</class>
        <class>com.ejemplo.Pedido</class>
        <properties>
            <property name="hibernate.dialect" value="org.hibernate.dialect.MySQLDialect"/>
            <property name="hibernate.hbm2ddl.auto" value="update"/>
            <property name="hibernate.show_sql" value="true"/>
            <property name="hibernate.format_sql" value="true"/>
        </properties>
    </persistence-unit>
</persistence>

```

- persistence-unit: Define una unidad de persistencia llamada "miUnidadDePersistencia". Es como un contenedor que contiene toda la configuración relacionada con JPA.

- provider: Indica el proveedor de persistencia que JPA va a usar. En este caso, estamos usando Hibernate, que es uno de los proveedores más comunes.

- class: Aquí indicamos las clases que son entidades JPA, como Cliente y Pedido. Estas clases serán gestionadas por JPA.

- properties: Contiene configuraciones adicionales. En este caso, estamos configurando Hibernate para:
    - Usar el dialecto de MySQL.

    - Configurar el comportamiento de la base de datos (como la actualización de esquemas).
    
    - Mostrar las consultas SQL que se están ejecutando.

[Volver al Índice](#índice)

## Operaciones CRUD con JPA

1. Create

    Para crear y almacenar una nueva entidad en la base de datos, se utiliza el método persist() del EntityManager.

    ```
    import javax.persistence.EntityManager;
    import javax.persistence.EntityManagerFactory;
    import javax.persistence.Persistence;

    public class CrudOperations {
        private EntityManagerFactory emf = Persistence.createEntityManagerFactory("miUnidadPersistencia");

        public void createUsuario(Usuario usuario){
            EntityManager em = emf.createEntityManager();
            em.getTransaction().begin();
            em.persist(usuario);
            em.getTransaction().commit();
            em.close();
        }
    }
    ```

2. Read

    Para leer entidades de la base de datos, se puede utilizar el método find() del EntityManager, consultas JPQL o Criteria API.

    - Leer una entidad por su id:

    ```
    public Usuario readUsuario(Long id){
        EntityManager em = emf.createEntityManager();
        Usuario usuario = em.find(Usuario.class, id);
        em.close();
        return usuario;
    }
    ```

    - Leer todas las entidades:

    ```
    import java.util.List;
    public List<Usuario> readAllUsuarios(){
        EntityManager em = emf.createEntityManager();
        List<Usuario> usuarios = em.createQuery("SELECT u FROM Usuarios u", Usuario.class).getResultList();
        em.close();
        return usuarios;
    }
    ```

3. Update

    Para actualizar una entidad existente, se utiliza el método merge() del EntityManager.

    ```
    public void updateUsuario (Usuario usuario){
        EntityManager em = emf.createEntityManager();
        em.getTransaction().begin();
        em.merge(usuario);
        em.getTransaction().commit();
        em.close();
    }
    ```

4. Delete

    Para eliminar una entidad, se utiliza el método remove() del EntityManager.

    ```
    public void deleteUsuario(Long id){
        EntityManager em = emf.createEntityManager();
        em.getTransaction().begin();
        Usuario usuario = em.find(Usuario.class, id);
        if(usuario != null){
            em.remove(usuario);
        }
        em.getTransaction().commit();
        em.close();
    }
    ```

[Volver al Índice](#índice)

---
--- 
---

# Bases de datos relacionales y orientadas a objeto (Unidad 5)

## Introducción a XML

XML es un lenguaje de etiquetado o marcado de información de propósito general. Podemos etiquetar cualquier tipo de información mediante sus elementos, atributos y relaciones.

Es diferente a otros lenguajes como HTML donde los elementos y el uso que se les debe dar viene fijado por la propia especificación del lenguaje.

Es un lenguaje que facilita el intercambio de datos. Define un estándar que permite el intercambio de información entre sistemas, independientemente de la tecnología que estos tengan por detrás, ya que XML da un ámbito único de definición para compartir la información.

Tiene la capacidad de separar la información de su representación. Por un lado tenemos la definición de cómo debe de ser la estructura de la información en lo que respecta a sus elementos y relaciones entre ellos además de la información que albergan. Por otro lado, tenemos la información que puede ser representada de múltiples formas.

El lenguaje XML se estructura en forma que al ver un fichero XML puede ser comprendido por máquinas que intercambian la información, pero también fácilmente por humano debido a la estructura del mismo.

Es extensible porque permite crear estructuras de datos que pueden ser extendidas y añadir nuevos elementos, atributos o relaciones sobre los documentos base.

## Estructura de un documento XML

Es la unidad XML de información constituido por elementos y markup. Sirven para identificar en qué consiste la información del documento y proporciona una jerarquía semántica.

Tiene dos partes:

- Document Prolog (prólogo): es una sección especial que aparece al principio de un documento XML, antes del elemento raíz. Este prólogo tiene varios propósitos importantes, como proporcionar información sobre el documento XML y su formato. Es una parte opcional, pero en la mayoría de los casos se utiliza para definir la versión de XML y la codificación de caracteres que se va a usar.

    - Declaración XML:
    Esta es una línea opcional que va al principio de un documento XML y proporciona información acerca de la versión de XML y la codificación de caracteres que se utiliza.
    ```
    <?xml version="1.0" encoding="UTF-8"? standalone="no">
    ```
    version = Versión xml que se utiliza.

    encoding = sistema de codificación de los caracteres y la cantidad de bits que se usarán en la codificación.

    standalone = determina si el documento depende o no de información del exterior de este.

    - La declaración de tipo de documento (DTD, opcional):
    Especifica cómo deben estar organizados los elementos dentro de un documento XML de tipo "libro".

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE libro [
    <!ELEMENT libro (titulo, autor, ano)>
    <!ELEMENT titulo (#PCDATA)>
    <!ELEMENT autor (#PCDATA)>
    <!ELEMENT ano (#PCDATA)>
    ]>
    ```

- Document elements (elementos): dividen el documento en una jerarquía, con diferentes secciones, creando una estructura de árbol que surgen de una raíz. Cada sección se crea con elementos que a su vez, pueden tener otros elementos y textos. Estos se conocen como nodos.

    Tipos de elementos: 

    - Texto

    - Atributos

    - Otros elementos
    
    Los elementos tienen un ámbito, delimitado por la etiqueta de apertura y por la etiqueta de cierre. Es decir, el contenido que está entre el `<tag>` de apertura y el `</tag>` de cierre pertenece a ese elemento en particular. El ámbito de un elemento es el contexto o espacio dentro del documento XML en el cual el contenido del elemento tiene sentido y es válido. Si hay elementos o nodos hijos, su ámbito también está dentro del ámbito del elemento padre.

[Volver al Índice](#índice)

## Atributos

Los atributos brindan información extra al elemento. El nombre del atributo es único.
Definen propiedades del elemento, siempre van en el `<tag>` de apertura del elemento al que pertenecen y su  contenido va entre comillas.

```
<elemento atributo="valor">

    ...

</elemento>

```

Hay diferentes tipos de atributos:

- Cadena (String): Es el tipo más común. El valor del atributo es simplemente un texto común.

```<empleado nombre="Juan" edad="30" />```

- Tokenized: Son atributos que tienen restricciones especiales sobre su valor. En lugar de ser solo una cadena de texto, los valores de estos atributos siguen ciertas reglas para asegurar que el valor tiene un formato específico.
    
    - ID: Es un tipo de atributo que identifica un elemento de manera única dentro del documento XML. Un atributo ID debe ser único en todo el documento.
    ```<empleado id="empleado001" />```

    - IDREF: Este atributo hace referencia a un ID de otro elemento en el mismo documento.
    
    ```
    <empleado id="empleado001" nombre="Juan" />
    <empleado id="empleado002" nombre="María" jefe="empleado001" />

    ```
    - IDREFS: Es similar a IDREF, pero en lugar de hacer referencia a un solo ID, puede hacer referencia a varios IDs.

    ```
    <empleado id="empleado001" nombre="Juan" />
    <empleado id="empleado002" nombre="María" jefe="empleado001 empleado003" />

    ```

    - ENTITY: Se usa para hacer referencia a una entidad externa (como un archivo o un dato definido en otro lugar). El valor del atributo debe ser el nombre de una entidad que está definida en algún lugar del documento o en una declaración de entidad externa.

    ```
    <!DOCTYPE ejemplo [
        <!ENTITY empresa "AcmeCorp">
    ]>

    <empleado nombre="Juan" empresa="&empresa;" />

    ```
    Aquí, el atributo `empresa="&empresa;"` hace referencia a una entidad externa que está definida en el DTD (Documento de Tipo de Definición).

    - ENTITIES: Similar a ENTITY, pero este atributo puede hacer referencia a varias entidades externas.

    ```
    <!DOCTYPE ejemplo [
        <!ENTITY empresa "AcmeCorp">
        <!ENTITY cliente "JohnDoe">
    ]>

    <empleado nombre="Juan" empresa="&empresa;" cliente="&cliente;" />
    ```

    - NMTOKEN: Este tipo de atributo tiene restricciones sobre qué datos pueden ser parte del valor del atributo. Son básicamente strings (cadenas de texto), pero con restricciones adicionales sobre qué caracteres pueden usarse. El valor solo puede contener caracteres que sean válidos según las reglas de un token (por ejemplo, no puede tener espacios, ni caracteres especiales como !, @, etc.). Es útil cuando queremos que el valor del atributo sea algo similar a un nombre (por ejemplo, un nombre de usuario, una clase, etc.).

    ```
    <empleado nombre="Juan" cargo="gerente123" />
    ```

    - NMTOKENS: Similar a NMTOKEN, pero permite varios tokens en el mismo atributo.

    ```
    <empleado nombre="Juan" roles="gerente123 supervisor456" />
    ```
- Enumerados: Son aquellos que tienen un conjunto de valores predefinidos. Esto significa que el valor del atributo no puede ser cualquier texto libre; debe ser uno de los valores especificados en la definición del atributo. Restringe el valor del atributo a un conjunto específico de opciones predefinidas.

    - NotationType: Este tipo de atributo es usado para hacer referencia a una notación que ha sido previamente declarada dentro del documento XML. Una notación en XML es una forma de indicar cómo los datos de un documento se deben interpretar. Generalmente, se refiere a algún tipo de archivo o dato que no se puede expresar directamente en XML. La notación podría hacer referencia, por ejemplo, a un tipo de archivo externo (como imágenes o archivos de audio) o a un tipo de codificación especial.

    ```
    <!DOCTYPE documento [
        <!NOTATION imagen SYSTEM "image/jpg">
        <!NOTATION audio SYSTEM "audio/mp3">
    ]>

    <documento archivo="foto.jpg" tipo="imagen" />
    <documento archivo="musica.mp3" tipo="audio" />

    ```

    En este ejemplo, el atributo tipo está restringido a referenciar una notación previamente definida en el DTD, por ejemplo imagen o audio. En este caso, tipo="imagen" o tipo="audio" son valores enumerados porque solo puede ser uno de esos dos valores definidos por las notaciones declaradas.

    - Enumeración: Un atributo de enumeración es un atributo cuyo valor tiene que estar dentro de una lista predefinida de valores posibles. Es decir, solo se aceptan los valores especificados en la definición del atributo.

    ```
    <!DOCTYPE empleados [
        <!ATTLIST empleado estado (activo|inactivo|suspendido) #REQUIRED>
    ]>

    <empleados>
        <empleado nombre="Juan" estado="activo" />
        <empleado nombre="Ana" estado="inactivo" />
        <empleado nombre="Pedro" estado="suspendido" />

        <empleado nombre="Carlos" estado="despedido" /> <!-- Esto no sería válido -->
    </empleados>

    ```

[Volver al Índice](#índice)

## Sección DATA (CDATA)

Una sección de datos o CDATA (Character Data) es una forma especial de incluir texto en un documento XML sin que se interprete como parte del lenguaje XML. Es útil cuando necesitas insertar texto que podría contener caracteres que normalmente tienen un significado especial en XML, como los signos de mayor (>) o menor (<), sin que el parser XML los interprete como elementos de apertura o cierre de etiquetas.

```
<![CDATA[
  Aquí va el texto que no será interpretado como XML.
  Por ejemplo, <p> y </p> serán tratados como texto, no como etiquetas XML.
]]>
```

[Volver al Índice](#índice)

## Instrucciones de procesamiento (Processing Instructions o PI)

Las instrucciones de procesamiento son una manera de incluir información adicional en un documento XML, que no forma parte de los datos del documento en sí, sino que son dirigidas a una aplicación o procesador que manipula o interpreta el XML. Estas instrucciones son procesadas por programas que leen el XML y pueden usarlas para realizar ciertas acciones.

```
<?target instruction?>
```

- Target: Es el nombre del procesador o aplicación que debe interpretar la instrucción. Por ejemplo, podría ser un nombre de software o sistema que se encargará de procesar esa instrucción. No es una etiqueta de XML, sino un nombre que actúa como un identificador para la aplicación que va a procesar esa instrucción.

- Instruction: Es el conjunto de instrucciones que la aplicación o procesador deberá realizar. Este texto es manejado directamente por la aplicación que recibe la instrucción, y puede variar dependiendo del software que está procesando el XML.

```
<?xml version="1.0" encoding="UTF-8"?>
<?orderProcessor validateOrder?>
<order>
    <customer>Juan Perez</customer>
    <items>
        <item>
            <name>Smartphone</name>
            <quantity>2</quantity>
            <price>300</price>
        </item>
    </items>
</order>
```

`<?orderProcessor validateOrder?>` le indica al procesador de pedidos que valide la orden. La aplicación que recibe y procesa el XML podría ejecutar alguna lógica interna de validación, como asegurarse de que el precio sea correcto o que el cliente esté registrado en el sistema. Si el procesador de XML no reconoce el target o la instrucción, simplemente puede ignorarlas sin causar errores.

[Volver al Índice](#índice)

## Validación

Un documento XML es válido si los contenidos están de acuerdo con los elementos y atributos definidos en el Document Type Declaration (DTD).

Existen dos criterios que documento XML debe cumplir para ser considerado válido:

### 1. Well-formed XML document

Un documento XML bien formado es aquel que cumple con las reglas básicas de la sintaxis XML, es decir, tiene la estructura adecuada para ser considerado un archivo XML. Estas reglas de sintaxis son necesarias para que el procesador XML pueda leer el archivo sin errores.

    Reglas de un documento XML bien formado:
    
    - Etiqueta de apertura y cierre: Cada elemento debe tener una etiqueta de apertura y una etiqueta de cierre (con la excepción de los elementos vacíos, como `<elemento />`).

    - Etiquetas anidadas correctamente: Las etiquetas deben cerrarse en el orden en que fueron abiertas. Por ejemplo, si abres `<a>`, debes cerrarla con `</a>` antes de cerrar cualquier otro elemento dentro de ella.

    - Uso de comillas en atributos: Los atributos dentro de las etiquetas deben estar entre comillas. Ejemplo: `<persona nombre="Juan"></persona>`.

    - No deben haber etiquetas sin cerrar: Cada etiqueta debe tener su correspondiente cierre. Un error común sería olvidar cerrar una etiqueta.

    - La raíz debe ser única: Un documento XML debe tener un solo elemento raíz que contenga todo el contenido. Por ejemplo, un documento válido debe comenzar con `<documento>` y terminar con `</documento>`.

### 2. Valid XML document

Un documento XML válido no solo debe ser bien formado, sino que también debe cumplir con un conjunto de reglas adicionales especificadas en el DTD (Document Type Declaration) o el XML Schema. Estas reglas definen los elementos y atributos permitidos, su orden y estructura, asegurando que el contenido XML siga un formato específico que sea compatible con la estructura de datos esperada.

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE persona [
        <!ELEMENT persona (nombre, edad)>
        <!ELEMENT nombre (#PCDATA)>
        <!ELEMENT edad (#PCDATA)>
    ]>
    <persona>
        <nombre>Juan</nombre>
        <edad>30</edad>
    </persona>

    ```

    En este caso, el DTD define que el elemento `<persona>` debe contener los elementos `<nombre>` y `<edad>`, y que ambos deben tener contenido de tipo texto.

    ```
    <persona>
        <nombre>Juan</nombre>
        <!-- Falta el elemento edad, por lo que el XML no es válido si usamos un DTD que lo exija -->
    </persona>
    ```


[Volver al Índice](#índice)

## XPath

XPath (XML Path Language) es un lenguaje utilizado para navegar y buscar a través de documentos XML. Es una herramienta para localizar datos dentro de un documento XML utilizando una sintaxis de ruta similar a un sistema de archivos o una URL.

Permite navegar por la estructura jerárquica de un documento XML, haciendo posible localizar nodos o elementos específicos de un documento. Es un estándar aprobado por el W3C.

Inicialmente se creó para utilizarlo con XLST, pero en la actualidad se utiliza también con XML Schema, Xquery, Xlink, Xpointer, Xforms, etc.

> NOTA: XSchema o XML Schema (también conocido como XSD, por sus siglas en inglés: XML Schema Definition) es un lenguaje de descripción de esquemas que se usa para definir la estructura y las restricciones de los documentos XML. Es un estándar que permite validar documentos XML para asegurarse de que sigan una estructura definida (similar al uso de DTD, pero más poderoso y flexible).

## Expresiones o Predicados

XPath usa expresiones para referirse a los nodos dentro de la jerarquía árbol de un documento XML. Estas expresiones se escriben como rutas y devuelven todo lo que encaja con la ruta y el predicado.

- Sintaxis:
    - Ruta absoluta: Empieza desde el nodo raíz (/).
        Ejemplo: `/libro/titulo` selecciona el nodo `<titulo>` dentro de un nodo `<libro>`, comenzando desde el nodo raíz del documento XML.

    - Ruta relativa: Empieza desde el nodo actual (sin / al principio).
        Ejemplo: `titulo` selecciona todos los nodos `<titulo>` en el contexto actual.

    - Selección de todos los elementos de un tipo: Usando //.
        Ejemplo: `//titulo` selecciona todos los nodos `<titulo>`en cualquier parte del árbol.

    - Selección de un atributo: Se usa @ para acceder a los atributos de un nodo.
        Ejemplo: `/libro/@id` selecciona el atributo id del nodo `<libro>`.

    - Predicados: Los predicados se colocan entre corchetes [] y se usan para filtrar los nodos que cumplen una condición.
        Ejemplo: `/libro/titulo[1]` selecciona el primer nodo `<titulo>` dentro de un nodo `<libro>`.

    - Funciones comunes:
        - text(): Se usa para seleccionar el texto dentro de un nodo.
        
        - position(): Para seleccionar el nodo en una posición específica.

    ```
    /libros/libro: Selecciona todos los elementos <libro> dentro del nodo raíz <libros>.

    /libros/libro/titulo: Selecciona todos los nodos <titulo> dentro de los nodos <libro>.

    /libros/libro[@id="1"]: Selecciona el nodo <libro> cuyo atributo id es igual a 1.

    /libros/libro/titulo/text(): Selecciona el texto dentro del nodo <titulo>.

    //titulo: Selecciona todos los nodos <titulo> en cualquier parte del documento XML (ruta relativa en todo el documento).
    ```

[Volver al Índice](#índice)

## Tipos de Nodos

- Nodo raíz: es el nodo más alto en la jerarquía del árbol XML, es decir, el nodo de nivel más alto que contiene todo el contenido del documento XML. Este nodo no tiene un nombre ni una etiqueta propia. Es simplemente un punto de partida desde el cual se organiza toda la estructura del XML. Se representa como `/` en las expresiones XPath.

El nodo raíz no es un elemento en sí mismo (como `<libros>` o `<persona>`), sino el contenedor global que "envuelve" todos los elementos del documento. Es nodo raíz abstracto que no forma parte del documento XML visible.

No es lo mismo que el elemento raíz, que es el primer elemento dentro del documento XML, el cual contiene todos los demás elementos.
A diferencia del nodo raíz, el elemento raíz sí tiene un nombre (por ejemplo, `<libros>`, `<documento>`, etc.), y su contenido abarca todo el documento XML.

    ```
    <libros>
    <libro>
        <titulo>XML Básico</titulo>
    </libro>
    </libros>
    ```

    El nodo raíz sería el contenedor que contiene todo el documento.

    El elemento raíz sería `<libros>`, ya que es el primer elemento del XML.

    Si en una expresión XPath escribimos `/`, nos estamos refiriendo al nodo raíz, es decir, el punto de partida de todo el documento.
    Si escribimos `/libros`, nos estamos refiriendo al elemento raíz llamado `<libros>` dentro del documento.

- Nodo elemento: Son los elementos de un documento XML, es decir, los bloques principales de datos dentro de la estructura del XML. Cada nodo elemento tiene un padre, excepto el elemento raíz, que es el primer nodo real del documento y está contenido dentro del nodo raíz abstracto del XML. Un nodo elemento puede tener hijos (otros elementos, atributos o nodos de texto).

- Nodo texto: Son los fragmentos de texto dentro del XML que no están envueltos en etiquetas adicionales. Se encuentran dentro de los nodos elemento y no pueden tener hijos. Aunque visualmente el texto parece parte del elemento, en términos de la estructura de nodos, el texto es un nodo separado dentro del nodo elemento.

- Nodos atributo: Son atributos asociados a un nodo elemento. Técnicamente en el modelo de datos del DOM (Document Object Model), los atributos no son nodos hijos de los elementos a los que pertenecen, sino propiedades adicionales del nodo. A pesar de esto, algunas herramientas tratan atributos como nodos dentro de su propio modelo de implementación, pero esto no es parte del estándar DOM de XML. No pueden tener otros nodos dentro y su valor se asigna directamente en la etiqueta del elemento.

    Si en un esquema XML (XSD o DTD) un atributo tiene un valor predeterminado, el procesador XML lo tomará como si estuviera presente en el documento, aunque no se haya escrito explícitamente el atributo dentro del tag.

    Si un atributo se define con #IMPLIED en un DTD, significa que no es obligatorio y, si no se especifica, simplemente no existirá en la estructura del documento.

    >NOTA: todos los atributos deben estar definidos en el esquema XML para poder ser validado y reconocido por el XML. Todos los atributos deben tener un tipo de declaración (#IMPLIED, #REQUIRED o un valor por defecto). No puedes simplemente declarar un atributo sin más.

- Nodos espacio de nombre (name space): son una forma de evitar conflictos de nombres cuando se combinan documentos XML de diferentes fuentes. En XML, los espacios de nombre permiten usar los mismos nombres de elementos o atributos sin que se confundan, asegurando que cada uno pertenece a un contexto único.

- Nodos comentario/instrucciones de procesamiento: son elementos que contienen notas o comentarios, y no afectan la estructura del documento ni el procesamiento de los datos. Se utilizan principalmente para hacer anotaciones en el código que no son procesadas por el parser XML, pero que pueden ser útiles para los desarrolladores.

    Los espacios de nombre son un mecanismo que permite distinguir entre elementos o atributos que pueden tener el mismo nombre pero que pertenecen a diferentes contextos o vocabularios.

    En lugar de usar solo un nombre como `<persona>`, puedes agregar un prefijo a los nombres de los elementos para indicar a qué espacio de nombre pertenecen. Esto se logra mediante la declaración de un espacio de nombre.

    ```
    <persona xmlns="http://example.com/namespace">
    <nombre>Juan</nombre>
    </persona>
    ```

    Aquí, el espacio de nombre xmlns="http://example.com/namespace" se aplica a todos los elementos dentro de `<persona>`, de modo que cualquier otro `<persona>` de otro contexto no se mezcle.

- Nodo actual: es aquel al que nos referimos cuando se evalúa una expresión XPath.

    ```
    /personas/persona[1]/nombre
    ```

    Aquí, el nodo actual es el primer `<persona>`, y la expresión XPath obtiene su `<nombre>`.

- Nodo contexto: hace referencia al conjunto de nodos sobre los cuales se realiza la evaluación de una expresión XPath. Cuando evalúas una expresión XPath, la evaluación comienza en un nodo inicial (llamado nodo contexto inicial) y va cambiando a través de la jerarquía de nodos XML, explorando los nodos según sea necesario hasta resolver la expresión. Cada vez que XPath evalúa una subexpresión, se mueve al siguiente nodo en ese contexto. El nodo contexto es un único nodo en cada momento de la evaluación, pero este nodo depende de la parte de la expresión XPath que estés evaluando.

- Tamaño del contexto: El tamaño del contexto hace referencia al número de nodos que están siendo evaluados por una expresión XPath en un momento determinado.

    ```
    <personas>
        <persona>
            <nombre>Juan</nombre>
        </persona>
        <persona>
            <nombre>María</nombre>
        </persona>
    </personas>
    ```

    Si ejecutas una expresión XPath como /personas/persona, el tamaño del contexto es 2 (porque hay dos nodos `<persona>`).

- Node-set: En XPath, cuando se hace una evaluación de una expresión que devuelve múltiples nodos, esos nodos se agrupan en lo que se llama un conjunto de nodos (node-set). 

    - Conjunto no ordenado:

        Un conjunto de nodos no tiene un orden definido. Es decir, los nodos dentro de este conjunto no tienen una secuencia específica como los elementos en una lista o array.

        Los nodos se agrupan, pero no hay un principio o final claro en cuanto al orden en que fueron seleccionados.

    - Son hermanos:

        Aunque los nodos dentro de un conjunto pueden estar en diferentes niveles de la jerarquía del documento XML (pueden ser nodos hijos de nodos diferentes), se considera que todos los nodos dentro de un conjunto son "hermanos".

        Esto significa que, a pesar de que esos nodos podrían haber pertenecido a diferentes partes del árbol XML, en el contexto de XPath, se tratan como si fueran hermanos (es decir, de un mismo nivel).

    - Subárboles no incluidos:

        Los subárboles (o sea, los nodos descendientes de un nodo) no se consideran parte del conjunto del node-set.


[Volver al Índice](#índice)

## Tokens

Los tokens son unidades sintácticas dentro de un lenguaje, y en el contexto de XPath o lenguajes similares, se refieren a símbolos que tienen un significado específico dentro de las expresiones y las unidades lógicas que componen las expresiones XPath.

En XPath, los tokens son utilizados para formular consultas sobre documentos XML, para seleccionar nodos, definir condiciones y más. Cada tipo de token tiene un propósito particular dentro de la sintaxis de las expresiones XPath.

- "()" (Paréntesis): se utilizan para agrupar expresiones o para definir el orden de las operaciones dentro de una expresión XPath. También se usan para invocar funciones y aplicar filtros o condiciones.

- "{}" (Llaves): se usan en XPath para referirse a los espacios de nombres. En este caso, se utilizan para identificar el prefijo del espacio de nombre al que pertenece un elemento o atributo, especialmente cuando se manejan documentos XML con múltiples espacios de nombre.

- "[]" (Corchetes): se utilizan para aplicar filtros o condiciones en XPath, permitiendo seleccionar nodos que cumplen con un criterio específico dentro de una lista de nodos. También se pueden usar para acceder a un ítem específico dentro de una lista (por ejemplo, el primer elemento).

- Atributo "@": se usa para hacer referencia a los atributos de un elemento en XPath. 

- Comodín "*": selecciona todos los elementos en un contexto determinado, sin importar su nombre. Es útil cuando se desea hacer una selección sin importar el nombre específico de los elementos.

- Separador "::" : se utiliza en XPath para seleccionar un tipo específico de nodo. Se utiliza en combinaciones con un nombre de nodo o función para especificar qué tipo de nodos queremos seleccionar.

- Coma "," : se usa para separar varias expresiones dentro de una consulta XPath. Es útil cuando se quieren seleccionar múltiples nodos o aplicar varias condiciones.

- Elemento padre "..":  se refiere al nodo que contiene al nodo actual.

- Nombre de un elemento: el nombre que se le asigna al elemento en el documento XML. En XPath, puedes referirte a un elemento por su nombre para seleccionar nodos específicos dentro de la jerarquía.

- Elemento Actual: el nodo sobre el que se realiza la evaluación en un momento dado.

[Volver al Índice](#índice)

## Operadores

- And, or, mod, div, *, **, /, //, |, +, -, =, !=, <, >, <=, >= : Estos operadores permiten realizar comparaciones, operaciones matemáticas y selecciones de nodos dentro de una expresión XPath.

```
//persona[edad > 18 and genero = 'M']

//persona[ciudad = 'Madrid' or ciudad = 'Barcelona']

//empleado[edad > 30]

```

- Nombres de funciones: XPath proporciona una serie de funciones que se pueden utilizar para manipular y filtrar los resultados. boolean, not, true, false, count, name, local-name, namespace-uri, position, last, normalize-space, string, concat, string-length, sum, ...

```
count(//empleado) → Cuenta cuántos nodos empleado existen.

contains(nombre, 'Juan') → Devuelve true si el nodo nombre contiene "Juan".

string-length(nombre) → Devuelve la longitud del texto dentro del nodo nombre.

normalize-space(//direccion) → Elimina espacios extra al inicio y final de un nodo de texto.
```

- Denominación de ejes: Los ejes en XPath definen relaciones entre nodos en el árbol XML. Se utilizan para navegar desde el nodo actual hacia otros nodos. ancestor, ancestor-or-self-atribute, child, descendant, descendant-or-self, following, following-sibling, namespace, parent, preceding, preceding-sibling, self.

```
//empleado/ancestor::empresa → Selecciona todos los nodos ancestros del nodo actual (padre, abuelo, bisabuelo, etc.)

//libro/attribute::id o //libro/@id → Selecciona los atributos de un nodo.

//libro/namespace::* → Selecciona los nodos espacio de nombres (raramente usado).
```

- Literales: Los literales en XPath son valores de texto o números utilizados en expresiones.

```
'Madrid', 'Juan' → Literales de texto (se usan en comparaciones como [ciudad = 'Madrid']).
```

- Números.

- Referencias a variables: Las variables en XPath se representan con el símbolo $ y se usan en combinación con XSLT o consultas en algunos entornos. $nombreVariable.

```
<xsl:variable name="precioMaximo" select="100"/>

//producto[precio <= $precioMaximo]

```

[Volver al Índice](#índice)

## Rotas de localización

En XPath, una ruta de localización es la secuencia de pasos que se deben seguir dentro del árbol XML para encontrar uno o varios nodos específicos. Al evaluar una ruta de localización, siempre se obtiene un conjunto de nodos (que puede contener uno, varios o ninguno).

Pueden ser rutas relativas o absolutas. Son deterministas. Dada una estructura XML fija, la misma ruta XPath siempre devuelve el mismo resultado.

[Volver al Índice](#índice)

## Acceso a ficheros y datos externos

Además de acceder a los datos del fichero XML con el que se está trabajando directamente, también es posible a acceder a datos de otros ficheros. 

Para ello usamos la función document(), que no es propia del lenguaje XPtah, sino que pertenece a XSLT.

Esta función puede admitir dos argumentos diferentes:

- document(URI): En este caso la función devuelve el elemento raíz del documento XML que se localiza en el URI especificado.

- document(nodo): En esta ocasión devuelve el conjunto de nodos cuya raíz es el nodo dado.

[Volver al Índice](#índice)

## XSLT

Es un estándar aprobado por el W3C. Es uno de los lenguajes derivado de XML, por tanto las hojas o archivos XSLT, también son documentos XML.

Debido a esto, podemos realizar varios tipos de transformación sobre un documento XSLT:

- A otro documento XML.

- A un documento HTML.

- A un documento de texto.

Dentro de XSLT podemos definir tres tipos de elementos:

- Elementos XSLT: están precedidos por el prefijo `xsl:` y pertenecen al espacio de nombres xsl.

- Elementos LRE (Literal Result Elements): no pertenecen al namespace de XSLT, son elementos literales.

- Elementos de extensión: no pertenecen al namespace de XSLT, son manejados por implementaciones concretas del procesador. Estos normalmente no son usados.

[Volver al Índice](#índice)

## Asociar un XML con una hoja XSLT

El propósito de asociar un XML a un XSLT es transformar el contenido del XML en otro formato, como HTML, otro XML, JSON, texto plano, etc.
XML solo almacena datos de forma estructurada, pero no define cómo se deben presentar o visualizar. XSLT permite:

- Convertir XML en HTML o XHTML → Para mostrarlo en un navegador.

- Filtrar y reorganizar datos → Extraer solo la información relevante o cambiar el orden de los elementos.

- Transformar un XML en otro XML → Para adaptarlo a diferentes sistemas o estructuras de datos.

- Aplicar estilos y dar formato → Controlar cómo se visualizan los datos.

Para indicar que un XML está asociado a un XSLT, hay que añadir al prólogo:

```<?xml-strylesheet type="text/xsl" href="rute_del_fichero_xsl.xsl"?>```

[Volver al Índice](#índice)

## Elementos de nivel superior

Los elementos de nivel superior son aquellos que se declaran directamente como hijos de `<xsl:stylesheet>` o `<xsl:transform>`. Estos elementos no pueden estar anidados dentro de otros elementos, excepto en casos especiales como `<xsl:variable>` y `<xsl:param>`.
Estos elementos son fundamentales para definir la lógica de transformación del documento XML y estructurar la hoja de estilos XSLT.

Los elementos más destacados son:

- xsl:attribute añade un atributo a un elemento en el árbol de resultados.

- xsl:choose permite decidir qué parte de la hoja XSL se va a procesar en función de varios resultados.

- xsl:decimal-format define un patrón que permite convertir en cadenas de texto números en coma flotante-

- xsl:for-each aplican sentencias a cada uno de los nodos del árbol que recibe como argumento.

- xsl:if permite decidir si se va a procesar o no una parte del documento XSL.

- xsl:import importa una hoja de estilos XSLT localizada en una URI dada.

- xsl:key define una o varias claves que pueden ser referenciadas desde cualquier lugar del documento.

- xsl:output define el tipo de salida que se generará como resultado.

- xsl:preserve-space especifica cuales son los elementos del documento XML que no tienene espacio en blanco eliminados antes de la transformación.

- xsl:sort permite aplicar un template a una serie de nodos ordenándolos alfabéticamente o numéricamente.

- xsl:stripe-space especifica cuales son los elementos del documento XML que tienen espacios en blanco eliminados antes de la transformación.

- xsl:template es el bloque fundamental de una hoja XSLT, por lo que veremos su descripción en el apartado siguiente.

- xsl:value-of calcula el valor de una expresión XPtah dada y lo inserta en el árbol de resultados del documento de salida.

- xsl:variable asigna un valor a una etiqueta para usarlo cómodamente.

[Volver al Índice](#índice)

## Plantillas

Las plantillas en XSLT sirven para definir cómo se transformarán los datos del documento XML. Se usan con el elemento `<xsl:template>`, y su propósito es aplicar estilos o estructuras a nodos específicos del XML.
Cada plantilla tiene un atributo match, que selecciona los nodos del XML a los que se aplicará la transformación.

```
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="productos.xsl"?>
<tienda>
    <producto>
        <nombre>Portátil</nombre>
        <precio>1200</precio>
    </producto>
    <producto>
        <nombre>Teléfono</nombre>
        <precio>800</precio>
    </producto>
</tienda>

```

```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    
    <!-- Plantilla principal, se aplica a la raíz del documento / -->
    <xsl:template match="/">
        <html xmlns="http://www.w3.org/1999/xhtml">
            <html>
                <body>
                    <h2>Lista de Productos</h2>
                    <ul>
                        <!-- Se aplica la plantilla a cada producto -->
                        <xsl:apply-templates select="tienda/producto"/>
                    </ul>
                </body>
            </html>
    </xsl:template>

    <!-- Plantilla para cada producto -->
    <xsl:template match="producto">
        <li>
            <strong><xsl:value-of select="nombre"/></strong> - $<xsl:value-of select="precio"/>
        </li>
    </xsl:template>

</xsl:stylesheet>

```

Cuando transformamos un XML con XSLT, el resultado debe ser XHTML bien estructurado (o HTML en versiones modernas). 
XHTML es una versión de HTML más estricta que sigue las reglas de XML.
El contenido dentro de `<xsl:template>` debe cumplir con la estructura de XHTML válida, sino el procesador XSLT puede falla:

- Se usa el namespace de XHTML: `<html xmlns="http://www.w3.org/1999/xhtml">`.

- Las etiquetas deben cerrarse correctamente `<br/>, <img src="imagen.jpg" alt=""/>`.

- Los atributos deben tener comillas dobles `<input type="text" />`.

- Se deben usar etiquetas en minúsculas `<body>`, no `<BODY>`.

Una plantilla puede contener varias reglas, cada una asociada a diferentes elementos del XML. Estas reglas determinan cómo se transformarán los datos de entrada en la salida.
Por defecto, las reglas dentro de una plantilla se ejecutan de arriba a abajo, en el orden en que aparecen en el archivo XSLT.
Se pueden modificar usando `<xsl:apply-templates>`, lo que permite llamar a reglas en otro orden o aplicar diferentes transformaciones a distintos elementos del XML.

```
<xsl:template match="producto">
    <li>
        <xsl:value-of select="nombre"/> - <xsl:value-of select="precio"/>
    </li>
</xsl:template>

<xsl:template match="producto[@oferta='si']" priority="2">
    <li style="color:red;">
        <xsl:value-of select="nombre"/> - <xsl:value-of select="precio"/> (¡Oferta!)
    </li>
</xsl:template>

```

[Volver al Índice](#índice)

##  Procesadores

Un procesador XSLT, es un software que lee un documento XSLT y otro XML para crear un documento de salida aplicando las instrucciones de la hoja de estilos XSLT a la información del documento XML.
Pueden estar integrados dentro de un explorador Web (como MSXML en IE6, en un servidor web como Cocoon de Apache XML o puede ser un programa que se ejecuta desde la línea de comandos como Xalan de Apache o SAXON).

Existen diferentes modos de realizar la transformación XSLT:

- Mediante el procesador MSXML, un ejecutable que llama a la biblioteca de transformación de Internet Explorer.

- Usando un procesador XSLTPROC.

- Invocando a la biblioteca de transformación desde un programa.

- Realizando un enlace entre la hoja XSLT y el documento XML.

[Volver al Índice](#índice)

## Bases de Datos Orientadas a Objetos (OODBMS)

Son sistemas de gestión de bases de datos que representan la información en forma de objetos.

Características principales:

- Los datos se almacenan en objetos/instancias de clases. Pueden contener tanto atributos como métodos que operen sobre los datos.

- Se utilizan clases para definir la estructura y el comportamiento de los objetos. Pudiendo heredar atributos y métodos, permitiendo la reutilización de código y la creación de jerarquía de clases.

- Cada objeto tiene una identidad única, conocida como OID (Object Identifier), que lo distingue de otros objetos.

Este tipo de Base de Datos ventajas:

- Concordancia: son mucho más naturales para los lenguajes de programación orientados a objetos, lo que reduce la brecha de impedancia entre el modelo físico y el de programación.

- Flexibilidad y Extensibilidad: La herencia y el polimorfismo facilitan la evolución del sistema sin grandes reestructuraciones.

- Soporte para datos complejos: pueden manejar datos complejos como listas, conjuntos y otros objetos compuestos de manera más eficiente.

Tienen las siguientes desventajas:

- Falta de estándares: no están tan estandarizados en la actualidad, por lo que puede conllevar problemas de portabilidad y compatibilidad.

- Curva de Aprendizaje: se necesita tiempo adicional para aprender y adaptarse a los conceptos y tecnologías de las OODBMS.

- Rendimiento y Escalabilidad: para ciertas aplicaciones, pueden no ser tan eficientes o escalables, especialmente para entornos con grandes volúmenes de datos y alta concurrencia.

Aplicaciones que comunmente implementan este tipo de Bases de Datos:

- Aplicaciones CAD/CAM.

- Sistemas de Información Geográfica (GIS).

- Aplicaciones de Telecomunicaciones.

[Volver al Índice](#índice)

---
--- 
---

# Bases de Datos XML (Unidad 6)

## Características del lenguaje XML

1. Formato flexible y estructurado:

    - XML (eXtensible Markup Language) permite representar datos en un formato estructurado mediante etiquetas personalizables.

    - No define cómo deben presentarse los datos, sino que proporciona una manera estandarizada de describirlos, lo que facilita la interoperabilidad entre sistemas.

2. Ficheros de texto legibles:
        
    - Los documentos XML son simplemente archivos de texto plano, lo que significa que pueden ser abiertos y editados por cualquier programa
    - Esto los hace fáciles de inspeccionar y depurar, sin necesidad de herramientas especializadas.

3. Interoperabilidad:
        
    - XML es un estándar ampliamente aceptado para el intercambio de datos.
        
4. Extensible y personalizable:
        
    - Los desarrolladores pueden definir sus propias etiquetas y estructuras según las necesidades de la aplicación, lo que otorga gran flexibilidad.
    
5. Jerarquía y estructura clara:
    
    - Los datos están organizados de manera lógica y organizada en forma de árbol.

6. Autodescriptivo:
    
    - Las etiquetas son descriptivas, indicando su contenido, lo que hace que los datos sean fáciles de entender.

[Volver al Índice](#índice)

## Categorías de sistemas que utilizan XML

Se refiere a cómo se usa XML dentro de un sistema, es decir, si el XML es tratado como un documento completo o como una fuente estructurada de datos individuales.

Los sistemas que utilizan XML para el almacenamiento y manejo de datos se agrupan en dos categorías principales, según cómo se organicen y procesen los documentos y qué tan estructurados o flexibles sean los datos dentro de estos:


1. Sistemas centrados en los documentos:

    Estos sistemas están diseñados para trabajar con documentos completos en formato XML, donde tanto la estructura como el contenido son ambas relevantes.

    Este es el enfoque tradicional, donde XML se utiliza principalmente para representar documentos completos, y el esquema (si se usa uno) tiende a ser flexible.
    
    En estos sistemas, un documento XML puede ser tratado como una unidad completa, es decir, se almacena, recupera y procesa como un documento completo, sin necesidad de descomponerlo en partes más pequeñas:

    - Orden e importancia de la jerarquía: El orden de los elementos dentro del documento XML tiene importancia. Se conserva la jerarquía y las relaciones entre elementos. Se utilizan principalmente cuando el contenido estructurado del documento es tan importante como su semántica o presentación.

    - Ideal para documentos grandes y complejos: Si necesitas almacenar y recuperar documentos completos (como facturas, contratos, informes, etc.), el enfoque basado en documentos es adecuado. Se tratan como una unidad, a menudo se procesan en su totalidad.

    - Flexibilidad en la estructura: No es necesario que todos los documentos sigan un formato rígido. Por ejemplo, en un sistema de gestión de catálogos de productos, cada archivo XML podría tener un número diferente de campos (algunos productos podrían tener una categoría, otros no, algunos podrían tener una descripción más larga que otros, etc.) Tienden a ser más impredecibles en cuanto a tamaño y contenido, presentando reglas más flexibles como campos opcionales para el propio contenido.

    ``` Ejemplos: Publicaciones electrónicas, documentos legales, documentos académicos. ```


2. Sistemas centrados en los datos:

    El enfoque basado en datos es una forma más estructurada de manejar XML, donde no se trata a todo el documento XML como una unidad completa, sino que se extraen fragmentos de datos específicos. Los documentos XML se pueden consultar y analizar en fragmentos pequeños que contienen solo la información necesaria, sin preocuparse por el formato o la jerarquía del documento completo.

    Estos sistemas se centran en manejar los datos almacenados como elementos estructurados que pueden ser consultados y procesados de manera granular:

    - Optimizado para consultas: Este enfoque es más adecuado para escenarios donde se necesita hacer consultas rápidas y precisas, como en sistemas de inventarios o bases de datos que usan XML como formato de intercambio de datos entre diferentes sistemas. Están diseñados para manejar grandes volúmenes de datos estructurados que se procesan frecuentemente.

    - Estructura más rígida: Los datos son tratados de manera más estructurada. Aunque XML es flexible, en este enfoque los datos se almacenan de forma que se puedan consultar fácilmente de manera más fragmentada. Tienen una estructura definida fija.

    - Consultas específicas: Utilizan lenguajes de consulta como XPath o XQuery para extraer solo los datos que son relevantes en un momento dado. No es necesario tratar el documento completo si solo quieres acceder a una parte. El enfoque principal está en consultar, actualizar y manipular datos (CRUD).

    ``` Ejemplos: Inventarios, facturas, catálogos, intercambio de datos entre apps ```

[Volver al Índice](#índice)

## Bases de Datos XML

Una base de datos XML es una colección de documentos XML en la que cada documento representa un registro dentro de la base de datos o un archivo dentro de un sistema de archivos

Este enfoque permite que la información esté estructurada y legible tanto para máquinas como para humanos

Los documentos XML almacenados en estas bases de datos suelen seguir un mismo XML Schema o DTD (Document Type Definition):

Los esquemas XML definen las reglas sobre los tipos de datos que los documentos XML pueden contener y cómo deben organizarse.:

- Los elementos que deben aparecer ```Ejemplo: <nombreProducto> o <precio>```

- La jerarquía entre los elementos

- Tipos de datos permitidos (números, fechas, texto, etc.)

Esto asegura que los documentos sean consistentes y puedan ser procesados correctamente, en lugar de almacenar cualquier tipo de documento XML sin control, permitiendo garantizar que los documentos sigan un formato consistente, asegurando que la información cumpla ciertas reglas predefinidas.

Sin embargo, esta estructura también puede ser más flexible que las bases de datos relacionales, ya que no requiere un esquema rígido y fijo

[Volver al Índice](#índice)

## Ventajas

La principal ventaja de usar este tipo de bases de datos, es que proporcionan gran flexibilidad gracias a tener colecciones de documentos con un esquema independiente
Lo cual deriba en un compartimiento de información más cómodo, automático y eficiente

### 1. Flexibilidad

- A diferencia de las bases de datos relacionales, en las bases de datos XML los documentos no tienen que seguir exactamente el mismo esquema. Esto permite agregar nuevos tipos de información o campos sin afectar documentos anteriores

- Por ejemplo, si en un sistema de facturación se decide agregar un nuevo campo como "descuento", no será necesario modificar toda la base de datos, ya que los documentos XML antiguos aún serán válidos

### 2. Compatibilidad y compartición de datos

- Al estar estructurados como documentos XML, los datos pueden ser fácilmente compartidos entre aplicaciones y sistemas. Esto es especialmente útil en servicios web, donde XML es una de las principales formas de intercambio de datos

### 3. Procesamiento automático

- Los documentos XML pueden ser procesados automáticamente por herramientas y tecnologías como XPath, XQuery o XSLT, lo que facilita la búsqueda, transformación y consulta de datos

- Tienen lenguajes de consulta diseñados específicamente para trabajar con datos XML. Los lenguajes de consulta permiten extraer información específica de los documentos XML sin necesidad de leerlos completamente. Esto es crucial cuando tienes grandes volúmenes de datos y necesitas realizar búsquedas rápidas y eficientes.

### 4. Eficiencia en sistemas heterogéneos

- Las bases de datos XML permiten integrar información proveniente de diferentes sistemas o formatos sin necesidad de transformarla previamente a un esquema relacional único

Sin embargo, no son la mejor opción en escenarios donde se necesita alta eficiencia en consultas complejas o grandes volúmenes de datos estructurados, para lo cual las bases de datos relacionales suelen ser más apropiadas

### 5. APIs (SAX y DOM)

- Tienen interfaces de programación de aplicaciones (APIs) que se utilizan para leer y manipular documentos XML en aplicaciones de software. Son métodos de acceso y manipulación de XML que varían en cómo gestionan el procesamiento de los datos.

    - DOM (Document Object Model):
    DOM es una API que carga todo el documento XML en memoria y lo representa como un árbol de nodos. Cada parte del XML (elementos, atributos, texto) es un nodo que puede ser accedido y manipulado de forma programática.
        - Ventajas: 
        Permite manipular fácilmente los documentos XML (puedes modificar el contenido, agregar elementos, eliminar nodos, etc.).

        - Desventajas: 
        Puede ser ineficiente en documentos grandes, ya que consume bastante memoria para cargar todo el documento en la memoria RAM.

    - SAX (Simple API for XML):
    SAX es un procesador basado en eventos que lee el XML de manera secuencial, sin cargar todo el documento en memoria. Cada vez que se encuentra un elemento, genera un evento que puede ser procesado por el programa.
        - Ventajas: Es más eficiente en términos de memoria, especialmente para documentos grandes, ya que no necesita cargar todo el archivo en memoria.

        - Desventajas: No permite manipular el documento como el DOM, ya que solo puedes procesarlo de manera secuencial, sin guardar el árbol completo.

[Volver al Índice](#índice)

## Diferencias con Bases de Datos Tradicionales

Los sistemas basados en documentos: 

- Estructura irregular: Los documentos no siguen una estructura fija estricta. Pueden tener diferentes campos o atributos según el contexto, lo que otorga flexibilidad, pero también puede hacer que el acceso y procesamiento de la información sea menos eficiente si no se define bien el esquema.

- Tipos de datos simples: Los documentos suelen contener tipos de datos simples como texto, números o fechas, sin muchas relaciones complejas entre ellos.

- Importancia del orden: Los sistemas basados en documentos suelen dar más importancia al orden en que se presentan los datos. Por ejemplo, en un fichero XML, el orden de los elementos puede ser significativo para interpretar correctamente la información.

Los sistemas basados en bases de datos relacionales: 

- Estructura plana: Los datos se organizan en tablas con filas y columnas. Cada tabla tiene una estructura fija, lo que significa que los datos deben ajustarse a un esquema predefinido. Esta estructura es eficiente para realizar operaciones de consulta complejas, pero más rígida.

- Tipos de datos complejos: Las bases de datos relacionales pueden manejar tipos de datos más complejos como referencias entre tablas, índices, y relaciones más avanzadas entre diferentes entidades.

- Poca importancia al orden: En las bases de datos relacionales, el orden de los datos generalmente no importa para su almacenamiento o recuperación. Se puede acceder a los datos de cualquier manera utilizando claves o índices.

Conclusión: 
Las bases de datos XML permiten integrar ambos tipos de sistemas (basados en documentos y basados en bases de datos relacionales).

Los sistemas basados en XML pueden servir como un puente entre datos de ficheros y documentos con estructura irregular y los datos relacionales que requieren un formato estructurado. Esto se logra porque XML permite representar tanto información jerárquica como tabular.

Esta integración permite que los datos de diferentes orígenes (orígenes heterogéneos) puedan ser almacenados y procesados de manera más eficiente, sin necesidad de transformar todos los datos a un formato común rígido como en las bases de datos relacionales.

[Volver al Índice](#índice)

## Tipos de Bases de Datos XML

Se refiere a cómo se almacena físicamente la información XML en una base de datos. Es un enfoque técnico sobre almacenamiento y gestión.
Existen dos enfoques principales para almacenar y recuperar información XML:

### 1. Bases de Datos XML Basadas en Texto

- Almacenan el documento como texto completo, sin transformarlo en otra estructura. 
    
- Utilizan herramientas de indexación para mejorar la búsqueda y recuperación.

- Pueden ofrecer soporte para transacciones (operaciones seguras y consistentes sobre los datos).

    Se pueden implementar de dos formas:

    - Opción 1: Guardar el XML como un archivo de texto en un almacén adecuado, con índices y soporte para transacciones.

    - Opción 2: Almacenar el XML como un BLOB (Binary Large Object) dentro de una base de datos relacional, junto con índices que faciliten las consultas.

### 2. Bases de Datos XML Basadas en el Modelo
 
- En lugar de almacenar el XML como texto, convierten su contenido a una estructura binaria más eficiente.

- Suelen utilizar DOM (Document Object Model) para representar y almacenar los datos.

- Son más eficientes en consultas y procesamiento porque trabajan directamente con una estructura optimizada.

    Existen diferentes formas de implementarlas:

    - Opción 1: Convertir el DOM del XML en tablas relacionales, donde cada nodo del XML (elementos, atributos, etc.) se almacena en una tabla diferente.

    - Opción 2: Traducir el DOM en objetos dentro de una base de datos orientada a objetos.

    - Opción 3: Usar un almacén especializado para XML, diseñado específicamente para manejar este tipo de datos (ej. BaseX, eXist-DB).

| Tipo de BD XML    | Ventajas                               | Desventajas                                      |
|-------------------|----------------------------------------|--------------------------------------------------|
| Basadas en Texto  | Simples y fáciles de almacenar        | Consultas más lentas si no hay buenos índices   |
| Basadas en Modelo | Más eficientes en consultas y procesamiento | Requieren conversión del XML a otro formato     |

[Volver al Índice](#índice)

## Diferencia entre el DOM y el Nodo Raíz

Es  una representación estructurada en memoria de un documento XML (o HTML). Es una estructura jerárquica (en forma de árbol) que representa el contenido y la estructura del XML como objetos en memoria. Es como un "modelo" que crea el navegador o un procesador XML cuando lee el documento. Este modelo convierte el XML en una estructura que es más fácil de manejar para un programa, permitiendo que puedas manipular los elementos, atributos y texto del documento mediante código.

- Cómo funciona: Cada elemento, atributo, texto, etc., dentro de un documento XML se convierte en un nodo en este árbol. El DOM permite a los programas acceder, modificar y manipular ese documento de manera estructurada.

- Propósito: El DOM es una interfaz que permite interactuar con el contenido de un documento XML (y también HTML). Permite leer y modificar el contenido de un XML de manera estructurada.

- Relación con el nodo raíz: El DOM es un modelo completo que abarca toda la estructura del XML, mientras que el nodo raíz es simplemente el primer nodo dentro de esa estructura. Es el nodo más alto en la jerarquía del DOM y normalmente representa el elemento raíz del documento XML.

El Nodo Raíz por otra parte, es el primer elemento (el contenedor principal) del documento XML. Es el nodo que contiene todo el resto del documento. En un documento XML, solo puede haber un nodo raíz.

- Cómo funciona: En un documento XML, todos los elementos deben estar dentro de este nodo raíz. Este nodo es el punto de partida para recorrer el árbol del DOM.

- Propósito: Es simplemente el contenedor principal de todos los elementos del XML. No tiene funcionalidades adicionales como el DOM, pero es el punto de referencia para acceder al contenido completo del documento XML.

Resumen:

- DOM es la estructura completa en memoria que representa un documento XML como un conjunto de nodos jerárquicos.

- El nodo raíz es el primer nodo dentro de esa estructura (normalmente el contenedor principal) que da comienzo al árbol del DOM.

En términos sencillos, el DOM es el "modelo" o la representación estructurada del XML, y el nodo raíz es el primer nodo dentro de ese modelo que contiene todos los demás nodos del documento.

[Volver al Índice](#índice)

## XQUERY

XQuery es un lenguaje de consulta y transformación para XML. Se utiliza para extraer información de documentos XML y manipular esos datos de manera estructurada. La comparación más cercana sería con SQL, que es un lenguaje de consulta para bases de datos relacionales, pero XQuery está específicamente orientado al manejo de datos XML.

Tiene similitudes con SQL ya que ambos son lenguajes de consulta. Mientras SQL consulta bases de datos relacionales, XQuery está diseñado para consultar documentos XML o bases de datos XML.

- En SQL, puedes escribir una consulta como `SELECT * FROM empleados WHERE edad > 30`.

- En XQuery, harías algo similar, pero enfocado en los elementos y atributos de un documento XML.

```
for $e in doc("empleados.xml")/empleado
where $e/edad > 30
return $e
```

También comparte muchas características con XPath, ya que ha sido construido en base a este, siendo un lenguaje declarativo para la localización de nodos y fragmentos de información en árboles XML. XPath es un lenguaje para navegar dentro de un documento XML y seleccionar nodos, y XQuery utiliza XPath para seleccionar esos nodos en las consultas. XQuery extiende XPath con capacidades adicionales de procesamiento y programación.

A diferencia de XPath, que se limita principalmente a seleccionar nodos, XQuery permite programación adicional.

- Bucles: como el for o let, que permiten iterar sobre nodos.

- Condicionales (if):  lo que permite realizar operaciones basadas en condiciones.

- Funciones definidas por el usuario para hacer más flexibles las consultas.

| **Característica**      | **XML**                                      | **XQuery**                                      |
|-------------------------|---------------------------------------------|------------------------------------------------|
| **Tipo**               | Formato de datos                            | Lenguaje de consulta                          |
| **Función principal**  | Almacenar y estructurar información        | Consultar y manipular datos XML               |
| **Uso**               | Definir y organizar datos en una jerarquía  | Extraer, filtrar y transformar información de documentos XML |
| **Ejemplo**           | `<libro><titulo>El Hobbit</titulo></libro>` | `for $l in /libro return $l/titulo` (devuelve "El Hobbit") |


Principales usos de XQuery:

### 1. Recuperar información de documentos XML

Se usa principalmente para consultar y extraer datos de documentos XML de manera eficiente, lo que es muy útil cuando trabajas con grandes volúmenes de datos XML.

```
for $person in doc("personas.xml")/personas/persona
where $person/edad > 30
return $person/nombre
```

Este ejemplo busca y extrae los nombres de todas las personas mayores de 30 años de un archivo XML.

### 2. Transformar estructuras XML

No solo consulta datos, sino que también puede transformar esos datos. Por ejemplo, puedes usar XQuery para reorganizar un XML y convertirlo en otra estructura más útil para diferentes aplicaciones.

### 3. Alternativa a XSLT para transformaciones

También se utiliza para transformaciones de datos, similar a XSLT. Sin embargo, XQuery es más flexible y tiene una sintaxis más simple que XSLT en algunos casos. A diferencia de XSLT, que se enfoca en la transformación de un XML a otro XML o a otros formatos como HTML, XQuery también puede hacer consultas y transformaciones más complejas en un solo paso.

XSLT es muy útil cuando necesitas transformar documentos XML a un formato diferente (como HTML o PDF), pero XQuery ofrece una alternativa más completa y flexible para realizar esas transformaciones, ya que también permite hacer consultas dentro del proceso de transformación.

[Volver al Índice](#índice)

## Requerimientos técnicos XQUERY

Los requerimientos técnicos de XQuery son las características que este lenguaje de consultas debe cumplir para trabajar correctamente con datos en formato XML. Estos incluyen:

### 1. Respetar el modelo de datos XML

XQuery trabaja con datos en formato XML, por lo que debe respetar la estructura y jerarquía de los datos.

```
<libros>
    <libro>
        <titulo>El Principito</titulo>
        <autor>Antoine de Saint-Exupéry</autor>
    </libro>
</libros>

```

Una consulta XQuery válida debe respetar esta estructura:

```
for $l in /libros/libro
return $l/titulo

```

### 2. Soportar XML Schemas, XSD y DTDs, pero ser independiente de ellos

XQuery debe poder trabajar con documentos validando su estructura con un esquema (XSD, DTD) o sin él.


Un XML Schema (XSD) podría definir que `<titulo>` debe ser un texto, pero XQuery también debe funcionar sin esta validación.
```
<libros xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="libros.xsd">
    <libro>
        <titulo>El Hobbit</titulo>
        <autor>J.R.R. Tolkien</autor>
    </libro>
</libros>
```

XQuery aún puede consultar datos sin importar si el XSD está presente o no.

### 3. Soporte de tipos simples y tipos complejos

XQuery debe manejar tipos simples (como números o texto) y tipos complejos (como nodos XML).

```
let $nombre := "Juan"
let $edad := 25
return <persona><nombre>{$nombre}</nombre><edad>{$edad}</edad></persona>
```

Salida XML generada:

```
<persona>
    <nombre>Juan</nombre>
    <edad>25</edad>
</persona>
```

### 4. Soporte de cuantificadores universales y existenciales

- Cuantificadores universales ("for all"): Comprueban si todos los elementos cumplen una condición.

- Cuantificadores existenciales ("exists"): Comprueban si al menos un elemento cumple una condición.


¿Todos los libros tienen un título?

```
every $b in /libros/libro satisfies $b/titulo
```

¿Existe al menos un libro con el título "El Hobbit"?

```
some $b in /libros/libro satisfies $b/titulo = "El Hobbit"
```

### 5. Soportar operaciones sobre jerarquías de nodos y secuencias

XQuery permite filtrar datos de un nodo padre a sus hijos y manejar secuencias de nodos.

```
for $titulo in /biblioteca/seccion/libro/titulo
return $titulo
```

### 6. Combinar información de múltiples fuentes

XQuery puede unir información de varios documentos XML en una consulta.

Si tenemos dos XML separados, uno con libros y otro con autores:

```
libros.xml:

<libros>
    <libro id="1"><titulo>El Hobbit</titulo></libro>
</libros>
```

```
autores.xml:

<autores>
    <autor id="1"><nombre>J.R.R. Tolkien</nombre></autor>
</autores>
```

Consulta XQuery que une los datos:

```
for $l in doc("libros.xml")/libros/libro,
    $a in doc("autores.xml")/autores/autor
where $l/@id = $a/@id
return <info><titulo>{$l/titulo}</titulo><autor>{$a/nombre}</autor></info>
```

### 7. Manipular datos sin importar el origen

XQuery permite procesar datos sin importar si vienen de XML, bases de datos o APIs.

Se puede obtener datos de un XML local:

```
doc("misLibros.xml")/biblioteca/libro/titulo
```

O de un servicio web externo:

```
doc("http://ejemplo.com/libros.xml")/libros/libro
```

###  8. Independencia de sintaxis en el lenguaje de consulta

XQuery debe ser independiente de la sintaxis de los datos XML, lo que significa que puede manejar estructuras diferentes sin necesidad de un formato fijo.

Si tenemos dos XML con diferentes estructuras:

```
<biblioteca><libros><libro><titulo>El Hobbit</titulo></libro></libros></biblioteca>
```

y

```
<coleccion><ejemplares><item><nombre>El Hobbit</nombre></item></ejemplares></coleccion>
```

Una consulta independiente de la sintaxis podría ser:

```
for $t in (/biblioteca/libros/libro/titulo | /coleccion/ejemplares/item/nombre)
return $t
```

[Volver al Índice](#índice)

## Modelo de datos XQUERY

XQuery y SQL pueden parecer similares en casi la totalidad de sus aspectos, pero no lo son. Tienen modelos distintos.

XML tiene conceptos de jerarquía y orden que no existen en el modelo relacional. El orden en el que se encuentran los datos es importante y determinante.


[Volver al Índice](#índice)

## Consultas XQUERY

A diferencia de SQL, donde los valores en las consultas siempre son absolutos (una tabla con filas y columnas), en XQuery los resultados dependen del contexto.

Factores que afectan el contexto en XQuery:

- Namespaces (Espacios de nombres): Afectan cómo se interpretan los nodos.

- Ubicación de la etiqueta raíz: Dependiendo de dónde se ejecuta la consulta, puede devolver distintos resultados.

- Secuencia de nodos: XQuery devuelve datos como nodos en secuencia, no como filas en una tabla.

Estas consultas pueden estar compuestas por hasta cláusulas de cinco tipos distintos. Siguen la norma FLWOR (For, Let, Where, Order and Return).
Son una de las estructuras más poderosas de este lenguaje para iterar, filtrar y ordenar datos:

```
<biblioteca>
    <libro>
        <titulo>Dune</titulo>
        <autor>Frank Herbert</autor>
        <precio>15.99</precio>
    </libro>
    <libro>
        <titulo>1984</titulo>
        <autor>George Orwell</autor>
        <precio>12.50</precio>
    </libro>
</biblioteca>
```

Consulta FLWOR en XQuery:

```
for $l in /biblioteca/libro
let $precio := $l/precio
where $precio > 13
order by $precio descending
return <resultado><titulo>{$l/titulo}</titulo><precio>{$precio}</precio></resultado>
```

Salida:

```
<resultado>
    <titulo>Dune</titulo>
    <precio>15.99</precio>
</resultado>
```

- (FOR) $l in /biblioteca/libro → Itera sobre cada libro.
- (LET) $precio := $l/precio → Guarda el precio del libro en la variable $precio.
- (WHERE) $precio > 13 → Filtra solo libros con precio mayor a 13.
- (ORDER) by $precio descending → Ordena de mayor a menor.
- (RETURN) → Devuelve el título y precio en formato XML.

Esto se parece a un `SELECT ... FROM ... WHERE` en SQL, pero con estructura XML.

En una sentencia FLWOR debe existir al menos una cláusula `for` o `let`.
Las cláusulas son case sensitive al contrario que en SQL.

[Volver al Índice](#índice)

## Cláusula RETURN

Se utiliza para especificar qué información se debe devolver como resultado de una consulta.

Sintáxis básica:

```
for $variable in //elemento
return result
```

- `$variable` representa el elemento que se va a buscar.

- `return` es la información que se desea recuperar.

Puede contener cualquier tipo de información desde simples valores numéricos y cadenas, hasta estructuras XML complejas. Además es posible utilizar funciones y expresiones XQuery dentro de la cláusula return para realizar cálculos y manipulaciones de datos más avanzados.

[Volver al Índice](#índice)

## Cláusula FOR

Asocia una o más variables con cada nodo que encuentre en la colección de datos. Si en la consulta aparece más de una cláusula for o más de una variable en la cláusula for, el resultado es el producto cartesiano de dichas variables.

Es una de las cláusulas más importantes de XQuery ya que permite especificar las variables y los valores que se van a procesar en una consulta.

Se utiliza para establecer el contexto de la consulta y para definir las expresiones que se van a evaluar. Es la que permite establecer el ámbito y los datos a procesar en una consulta.

[Volver al Índice](#índice)

## Cláusula LET

Permite asignar un valor a una variable la cual se puede utilizar posteriormente. Su uso permite que las consultas sean más legibles y fáciles de mantener.

Sintáxis básica:

```
let $variable expression
```

- `$variable` es el nombre de la variable que se va a utilizar.

- `expression` es la expresión que se va a evaluar para asignarle un valor a la variable.

Una característica a tener en cuenta es que las variables en XQuery son inmutables. Una vez definidas no se pueden modificar. A pesar de denominarse variables, su comportamiento es el de constantes.

Junto a la expresión XPath adecuada permiten obtener un único valor utilizando las funciones de agregación, recuento, suma, media, etc.

- La cláusula let para asignar los nombres de los empleados de la secuencia de nodos empleados a la variable $nombres.

- La cláusula return junto con la función count para obtener la cantidad de nombres.

```
let $nombres := /empleados/empleado[edad>=18]/nombre
return count($nombres)
```

[Volver al Índice](#índice)

## Cláusula WHERE

Se utiliza para filtrar los resultados producidos por las cláusulas for y let, limitándolos a aquellos elementos que cumplen ciertas condiciones especificadas en la consulta.

Sintáxis básica:

```
for $variable in elemento // where condition return result
```

- `$variable` representa el elemento que se va a buscar.

- `condition` es la expresión booleana que se evalúa para determinar si se incluye o no un elemento en el resultado.

- `result` es la información que se desea recuperar.

Cuando utilizamos where con un for, el where está recibiendo una lista de elementos los cuales recorreremos de forma individual. De esta forma, se evaluará la condición definida en el where a cada uno de los elementos que se han obtenido de la expresión de la cláusula for.

```
for $libro in //libro
where $libro/precio > 50
return $libro/titulo
```

Cuando utilizamos where con un let, el where está recibiendo un único elemento. Teniendo esto en cuenta, se evaluará la condición definida en el where a toda la variable.

```
let $n := 2
where $n > 1
return $n
```
- `let`declara una variable $n que guarda el valor 2.

- `where` para filtrar si el valor de $n es mayor a 1.

- `return` para recuperar el valor de $n.

[Volver al Índice](#índice)

## Cláusula ORDER BY 

Se utiliza para ordenar los resultados de una consulta en función de ciertos criterios especificados en la consulta. Ordena el resultado generado por for y let después de que han sida filtradas por la cláusula where.

```
for $variable in //elemento
where condition
order by criteria1, criteria2, ... criteriaN descending
return result
```

```
for $libro in //libro
order by $libro/autor, $libro/titulo
return $libro/titulo
```

```
for $estudiante in //estudiantes
let $promedio := avg($estudiante/calificaciones/calificacion)
order by $promedio descending
return $estudiante/nombre
```

[Volver al Índice](#índice)

## Tuplas en XQUERY

En XQuery, una tupla es cada conjunto de valores que toma una variable en una iteración.

```
<personas>
    <persona>
        <nombre>Ana</nombre>
        <edad>30</edad>
    </persona>
    <persona>
        <nombre>Juan</nombre>
        <edad>25</edad>
    </persona>
</personas>
```

Consulta XQuery con tuplas:

```
for $p in /personas/persona
return <datos><nombre>{$p/nombre}</nombre><edad>{$p/edad}</edad></datos>
```

Salida:

```
<datos>
    <nombre>Ana</nombre>
    <edad>30</edad>
</datos>
<datos>
    <nombre>Juan</nombre>
    <edad>25</edad>
</datos>
```

- Cada "persona" es una tupla dentro del for.

- Se genera un nodo `<datos>` con nombre y edad para cada iteración.

- Resultado: Un XML con una lista de tuplas.

En SQL, cada fila de una tabla sería una tupla. En XQuery, cada nodo iterado es una tupla.

| **Característica**         | **SQL**                                    | **XQuery**                                      |
|---------------------------|------------------------------------------|------------------------------------------------|
| **Formato de datos**      | Tablas (filas y columnas)                | XML (nodos jerárquicos)                        |
| **Independencia del contexto** | Sí, los datos no cambian según la consulta | No, depende de namespaces, ubicación y estructura |
| **Estructura de consulta** | `SELECT ... FROM ... WHERE ...`         | `FOR ... LET ... WHERE ... ORDER BY ... RETURN` |
| **Salida**                | Filas                                    | XML                                            |

[Volver al Índice](#índice)

## Funciones

En XQuery, las funciones se utilizan para realizar operaciones específicas que devuelven un resultado.
Este lenguaje, incluye una amplia variedad de funciones integradas para procesar y manipular datos, pero también permite definir funciones propiar y funciones dependientes del entorno de ejecución del motor XQuery.

Las funciones soportadas son de tipo:

- Funciones matemáticas:

    - floor()

    - ceiling()

    - round()

    - count()

    - min()

    - max()

    - avg()

    - sum()

- Funciones de cadenas de texto:

    - concat()

    - string-length()

    - starts-with()

    - ends-with()

    - upper-case()

    - lower-case()

- Funciones para el tratamiento de expresiones regulares.

- Funciones para comparar fechas y horas.

- Funciones para la manioulación de nodos XML.

- Funciones para la manipulación de secuencias.

- Funciones para la comprobación y conversión de tipos.

- Funciones booleanas.

- Funciones de uso general:

    - empty()

    - exists()

    - distinct-values()

    - data()

- Cuantificadores:

    - some

    - every

[Volver al Índice](#índice)

## Crear funciones

Una función nos permite definir operaciones que no están incluidas de forma nativa en XQuery. Se utilizan para modularizar el código, ya que se pueden llamar desde diferentes partes del código.

Se definen con la palabra clave `declare function` seguido del nombre:

```
declare function nombre_funcion ($param1 as tipo_dato1, $param2 as tipo_dato2, ..., $paramN as tipo_datoN) as tipo_dato_devuelto {
    (: Cuerpo de la función :)
}
```

Ejemplo:

```
declare function minPrice($p as xs:decimal?, $d as xs:decimal?) as xs:decimal? {
    let $disc := ($p * $d) div 100
    return ($p - $disc)
}
```

[Volver al Índice](#índice)

## Operadores

Comparación de valores:

- `eq` (equal)

- `ne` (not equal)

- `lt` (less than)

- `le` (less or equal than)

- `gt` (greater than)

- `ge` (greater or equal than)

Comparación general:

- `=`

- `!=`

- `>`

- `>=`

- `<`

- `<=`

Comparación de nodos:

- `is`

- `is not`

- `and`

- `or`

Operadores aritméticos:

- `+`

- `-`

- `*`

- `div`

- `mod`

[Volver al Índice](#índice)

## Motores XQuery

Motores de código abierto (open source) más relevantes:

- BaseX: es una base de datos XMl nativa y una herramienta de procesamiento de documentos XML. Este software que es de código abierto y multiplataforma, proporciona un motor de consulta completo para XPath, XQuery y XSLT.

- SAXON: es una herramienta de procesamiento XSLT y XQuery desarrollada por Java, aunque también se encuentra disponible en otros lenguajes como C, NEt, PHP, Python o JavaScript. Implementa los estándares XSLT y XQuery. Contiene múltiples paquetes open source y otros bajo licencia comercial.

- Fonto 3.1: es una herramienta online que permite realizar consultas XQuery sobre un documento XML.

- Pattern matching XPath XQuery CSS Selector Online Tester: es una herramienta online que permite probar consultas XQuery. Para su funcionamiento, es necesario un documento XML.

[Volver al Índice](#índice)

## Resumen lenguajes que trabajan con XML

XML es muy flexible y estructurado, por lo que se utiliza en muchas áreas (bases de datos, documentos, configuración de sistemas, etc.). Sin embargo, XML por sí solo no es suficiente:

- XQuery se usa para consultar XML (Almacena datos).

- XPath permite navegar dentro de XML (Consulta datos XML).

- XSLT transforma XML en otros formatos (Transforma XML en otros formatos).

- XSD (XML Schema) define reglas y validaciones para XML (Valida la estructura de XML).

Cada uno de estos lenguajes cumple una función específica para trabajar con XML (Permite navegar dentro de XML).

| **Lenguaje**                                      | **Tipo**                     | **Función principal**                               | **Ejemplo** |
|---------------------------------------------------|------------------------------|----------------------------------------------------|-------------|
| **XML**             | Formato de datos             | Almacenar y estructurar información jerárquica    | `<persona><nombre>Ana</nombre></persona>` |
| **XQuery**                                       | Lenguaje de consulta         | Buscar, filtrar y manipular datos en XML         | `for $p in /persona return $p/nombre` |
| **XSLT** | Lenguaje de transformación  | Convertir XML a otros formatos (HTML, texto, JSON) | `<xsl:template match="nombre"><h1><xsl:value-of select="."/></h1></xsl:template>` |
| **XSD**                  | Lenguaje de validación       | Definir la estructura y reglas de un documento XML | `<xs:element name="nombre" type="xs:string"/>` |
| **XPath**                                        | Lenguaje de navegación       | Seleccionar partes específicas de un documento XML | `//persona/nombre` (selecciona todos los nombres dentro de "persona") |

[Volver al Índice](#índice)

---
---
---

# Programación de Componentes de Acceso a Datos (Unidad 7)

## JSON

JSON (JavaScript Object Notation) es un formato para estructurar datos en forma de texto y transmitirlos de un sistema a otro, como en aplicaciones cliente-servidor o en aplicaciones móviles.

Un archivo JSON  es un formato de texto ligero y legible para el intercambio de datos. Se utiliza ampliamente para transmitir datos entre un servidor y una aplicación web, aunque su uso se ha extendido a muchas otras áreas, como la configuración de aplicaciones y la comunicación entre servicios.
La ventaja de este formato es que permite obtener código legible para las personas con nombres y valores que funcionan como indicadores de la información que contienen.
JSON es un formato basado en texto que representa datos estructurados mediante pares clave-valor y listas ordenadas (arrays). Fue derivado de la sintaxis de objetos de JavaScript, pero es independiente del lenguaje, lo que lo hace muy popular.

Los archivos suelen tener la extensión `.json` y son especialmente provechosos para intercambiar o transferir información a lo largo de diferentes tipos de dispositivos digitales. El caso más común de uso de JSON está en el diseño de sitios web. Al crear páginas en línea queremos aseguramos de que el sitio lea correctamente la información contenida en el servidor y que la muestre de forma óptima.
También es utilizado para la creación de aplicaciones móviles y programas computacionales o incluso para la transferencia de documentos.

Es una herramienta tan versátil que podríamos asegurar que está prácticamente en todos lados. JSON es una sintáxis para almacenar e intercambiar datos. Dato que puede enviarse fácilmente hacia y desde un servidor para utilizarse como formato de datos de cualquier lenguaje de programación.

[Volver al Índice](#índice)

## Diferencia con XML

Utilizar JSON o XMl depende de las circunstancias y de las preferencias que en cada momento se determinen.

JSON:

    - Ventajas:

        - Es autodescriptivo y fácil de entender

        - Su sencillez le ha permitido posicionarse como la mejor alternativa a XML.

        - Es más rápido en cualquier otro navegador.

        - Es fácil de leer.

        - Es más ligero (bytes) en las transmisiones.

        - Se parsea más rápido.

        - Tiene una velocidad de procesamiento alta.

        - Puede ser entendido de forma nativa por los analizadores de JavaScript.

    - Desventajas:

        - Algunos desarrolladores encuentran su básica notación algo confusa.

        - No cuenta con extensibilidad.

        - No soporta grandes cargas, solo datos comunes.

        - Requiere de mecanismos externos, como expresiones regulares, para la seguridad.

XML:

    - Ventajas:

        - Tiene un formato estructurado y fácil de entender.

        - Separa la información o el contenido de su presentación o alfabeto.

        - Está diseñado para ser utilizado en cualquier lenguaje o alfabeto.

        - La composición de los documentos tiene reglas que son muy estrictas, de manera que el análisis sintáctico resulta sencillo.

        - Tiene soporte para cualquier tipo de datos.

        - Se pueden definir estructuras complejas y reutilizables.

    - Desventajas:

        - El formato es muy estricto.

        - Lleva más tiempo procesarlo.

        - Complejidad de analizador (parser).

        - Un error en cualquier parte del formato puede hacer que el documento en su totalidad sea inválido.

[Volver al Índice](#índice)

## Sintáxis de JSON

Hay dos elementos centrales en un objeto JSON:

    - Claves (Keys): Cadenas de texto descriptivas.

    - Valores (Values): Pueden utilizar cualquier tipo de dato de JavaScript.

Un JSON comienta y termina con llaves {}

```{"key":"value","key":"value","key":"value".}```

Consta de dos estructuras principales:

- Objetos

- Arrays

[Volver al Índice](#índice)

## Objetos

Un objeto es una colección de pares clave-valor encerrada entre llaves { }.

```
{
    "nombre": "Juan",
    "edad": 30,
    "ciudad": "Madrid"
}

```

Aquí, "nombre", "edad" y "ciudad" son claves, y sus respectivos valores son "Juan", 30 y "Madrid".


- Ejemplo en Java:

```
public class Puerta{
    int id=1;
    float precio=250.50;
    String nombre="Puerta de Roble";
    String[] etiquetas=ndw String[]{"casa","madera","roble"};
}
```

- Mismo ejemplo en JSON:

```
<body>
<script>
    var puerta=
    {
        "id":1,
        "nombre":"puerta de roble",
        "precio":250.50,
        "etiquetas":["casa","madera","roble"]
    }
</script>
```

[Volver al Índice](#índice)

## Array

Un array es una lista ordenada de valores encerrada entre corchetes [ ].

```
[
    "manzana",
    "banana",
    "cereza"
]
```

Ejemplo práctico con JavaScript:

```
//Declaración del objeto persona

var persona={
    "nombre":"Tom",
    "apellidos":"Jackson",
    "género":"masculino",
    "hobby":["fútbol","lectura","natación"] //Array
}

// Imprimir el valor de la clave: Tom
console.log(persona["nombre"]);
console.log(persona.nombre);

alert(persona.hobby);
alert(persona.hobby[2]);
```

La diferencia entre `persona["nombre"]` y `persona.nombre` radica en cómo se accede a las propiedades del objeto y cuándo es conveniente usar cada una:

| Método             | Uso                  | Ventaja                                       | Ejemplo                            |
|--------------------|---------------------|-----------------------------------------------|------------------------------------|
| `persona.nombre`  | Notación de punto    | Más simple y legible                         | `console.log(persona.nombre);`    |
| `persona["nombre"]` | Notación de corchetes | Permite claves dinámicas y caracteres especiales | `console.log(persona["nombre"]);` |

En la mayoría de los casos, usarás la notación de punto `persona.nombre`, pero la notación de corchetes `persona["nombre"]` es necesaria en ciertos escenarios.

[Volver al Índice](#índice)

## Funciones como Atributos

Se pueden crear funciones dentro de los objetos JSON, desarrolladando la estructura como un atributo más:

```
var persona={
    "nombre":"Tom",
    "apellidos":"Jackson",
    "género":"masculino",
    "hobby":["fútbol","lectura","natación"],
    decirAdios:function(){
        alert("adios");
    }
}

persona.decirAdios();
```

[Volver al Índice](#índice)

## Clases

[Volver al Índice](#índice)

[Volver al Índice](#índice)

[Volver al Índice](#índice)

[Volver al Índice](#índice)

[Volver al Índice](#índice)

[Volver al Índice](#índice)

[Volver al Índice](#índice)

[Volver al Índice](#índice)


---
---
---


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
**insertMultiple() y addMany() no existen en la API de MongoDB**


[Volver al Índice](#índice)


---
---
---


<br>

# Autoevaluación 1

<br>

1. ¿Cuál es la anotación principal utilizada para marcar una clase como una entidad en JPA?
a. @Table
b. @PersistenceContext
C. @ld
d. @Entity 

- La respuesta correcta es:
@Entity

---

2. ¿Cuál es la diferencia principal entre un fichero binario y un fichero de texto?
a. Los ficheros binarios almacenan datos en formato legible, mientras que los de
texto almacenan datos en formato binario
b. Los ficheros binarios son más eficientes en términos de espacio de
almacenamiento
c. Los ficheros binarios no son legibles por humanos, mientras que los de texto sí lo❤
son
d. Los ficheros de texto son más rápidos de leer y escribir


- La respuesta correcta es:
Los ficheros binarios no son legibles por humanos, mientras que los de texto sí lo
son

---

3.  ¿Cuál de los siguientes métodos se utiliza para crear una nueva entidad en JPA? 
a. confirm()
b. save(
c. create()
d. persist)

- La respuesta correcta es:
persist()

---

4.  ¿Por qué es importante manejar las excepciones al intentar abrir un fichero en un programa?
a. Para evitar conflictos de memoria
b. Para reducir la concurrencia de ficheros
c. Para prevenir la pérdida de datos y garantizar la integridad del programa
d. Para aumentar la velocidad de ejecución del programa

- La respuesta correcta es:
Para prevenir la pérdida de datos y garantizar la integridad del programa

---

5. ¿Cómo se comenta una línea en XQuery?
a. */ Comentario */
O b. //comentario
C. <!-- comentario -->
d. (: comentario :)

- La respuesta correcta es:
(: comentario :)

---

6. ¿Cuál es el propósito de un esquema en una base de datos?

a. Definir la estructura y organización de la base de datos
b. Documentar una aplicación
c. Ejecutar scripts de programación
d. Realizar copias de seguridad

- La respuesta correcta es:
Definir la estructura y organización de la base de datos


---

7. ¿Qué es una clave primaria en una base de datos?

a. Un campo para almacenar contraseñas
b. Un campo que permite la duplicación de registros
c. Un campo para almacenar todo tipo de elementos
d. Un campo que identifica de manera única cada registro en una tabla

- La respuesta correcta es:
Un campo que identifica de manera única cada registro en una tabla

---

8. El método createFile() de la clase Files:
a. No devuelve nada
b. Devuelve un path con la ruta del fichero creado.
c. Devuelve true si se ha podido crear la ruta relativa del fichero.
d. Devuelve true si se ha podido crear la ruta absoluta del fichero.

- La respuesta correcta es:
Devuelve un path con la ruta del fichero creado.

---

9. ¿Cuál es el propósito de la clase RandomAccessFile en Java?

a. Escribir datos en un fichero
b. Leer únicamente datos de tipo entero
c. Acceder a registros de un fichero de manera aleatoria

- La respuesta correcta es:
Acceder a registros de un fichero de manera aleatoria

---

10. ¿Cuál de las siguientes es una expresión XPath válida para seleccionar todos los elementos
`<libro>` en un documento XML?

a. //libro
b. xml/libro
c. /libreria/libro
d. @libro

- La respuesta correcta es:
//libro

---

11. ¿Cuál es la principal razón para cerrar adecuadamente un fichero después de su manipulación en
un programa?
a. Ahorrar recursos del sistema
b. Incrementar la velocidad de ejecución del programa
c. Evitar conflictos con otros programas
d. Liberar recursos asociados al fichero y garantizar la integridad de los datos lenguaje de consulta estándar

- La respuesta correcta es:
Liberar recursos asociados al fichero y garantizar la integridad de los datos
lenguaje de consulta estándar

---

12. ¿Qué método se usa para actualizar una entidad en JPA?
a. refresh()
b. merge()
c. update()
d. actualiza()

- La respuesta correcta es:
merge()

---

13. ¿Cuál de los siguientes modos de apertura de ficheros se utiliza para abrir un fichero en modo
solo lectura en la mayoría de los lenguajes de programación?
a. Write
b. Read
c. Create
d. Append

- La respuesta correcta es:
Read

---

14. ¿Qué interfaz de JDBC se utiliza para ejecutar consultas SQL?
a. DriverManager
b. Statement
c. FileReader
d. Connection

- La respuesta correcta es:
Statement

---

15. En Java, ¿cuál es la clase utilizada para leer datos desde un fichero de manera eficiente?
a. BufferedReader
b. FilelnputStream
c. FileWriter

- La respuesta correcta es:
BufferedReader

---

16. Para leer una entidad por su ID en JPA, ¿qué método se utiliza?
a. get()
c. find()
d. read()
b. write()

- La respuesta correcta es:
find()

---

17. ¿Cuál es el propósito principal de los directorios en sistemas operativos?
a. Organizar y estructurar los archivos en un sistema de archivos Correcta
b. Almacenar archivos temporales
c. Mejorar la velocidad de búsqueda de archivos
d. Mejorar la velocidad de búsqueda de archivos

- La respuesta correcta es:
Organizar y estructurar los archivos en un sistema de archivos Correcta

---

18. ¿Cuál es el propósito de la clase FilelnputStream en Java?
Escribir contenido en un archivo como caracteres.
a. Escribir contenido en un archivo como bytes.
b.
C. Leer contenido de un archivo como bytes.
d. Leer contenido de un archivo como caracteres.

- La respuesta correcta es:
Leer contenido de un archivo como bytes.

---

19. ¿Qué es una base de datos?
a. Un programa de edición de imágenes
b. Un programa informático
c. Un archivo de texto sin estructura
d. Un sistema organizado para almacenar y gestionar datos

- La respuesta correcta es:
Un sistema organizado para almacenar y gestionar datos

---

20. ¿Qué es XQuery?
a. Un lenguaje para consultar datos XML.
b. Un lenguaje utilizado en algoritmos de inteligencia artificial
c. Un lenguaje para consultar bases de datos relacionales.
d. Un lenguaje de programación para desarrollo web.

- La respuesta correcta es:
Un lenguaje para consultar datos XML.


<br>

[Volver al Índice](#índice)

<br>

---
---
---

<br>

# Autoevaluación 2

<br>


1. ¿Qué es el encapsulamiento en una base de datos orientada a objetos?

a. La capacidad de ocultar los datos de implementación interna y exponer solo una interfaz.

b. La capacidad de realizar consultas SQL.

c. La capacidad de exponer públicamente los métodos y atributos

d. La capacidad de dividir la base de datos en múltiples tablas.

- La respuesta correcta es:
La capacidad de ocultar los datos de implementación interna y exponer solo una interfaz.

---

2. ¿Qué interfaz de JDBC se utiliza para ejecutar consultas SQL?

a. FileReader

b. Statement

c. DriverManager

d. Connection

- La respuesta correcta es:
Statement

---

3.  ¿Cuál de los siguientes métodos se utiliza para crear una nueva entidad en JPA?

a. save()

b. persist()

c. confirm()

d. create()

- La respuesta correcta es:
persist()

---

4.  ¿Qué es una base de datos orientada a objetos?

a. Un sistema de gestión de bases de datos que almacena documentos

b. Un sistema de gestión de bases de datos que representa la información en forma de objetos.

c. Un sistema de gestión de bases de datos que usa tablas para almacenar datos.

d. Un sistema de gestión de bases de datos utilizado solo para datos numéricos.

- La respuesta correcta es:
Un sistema de gestión de bases de datos que representa la información en forma de objetos.

---

5. ¿Qué significa JPA en el contexto de acceso a datos en Java?

a. Java Programming API

b. Java Persistence API

c. Java Processing Algorithm

d. Java Persistence Architecture

- La respuesta correcta es:
Java Persistence API

---

6. ¿Qué es XQuery?

a. Un lenguaje utilizado en algoritmos de inteligencia artificial

b. Un lenguaje para consultar datos XML.

c. Un lenguaje para consultar bases de datos relacionales.

d. Un lenguaje de programación para desarrollo web

- La respuesta correcta es:
Un lenguaje para consultar datos XML.

---

7. ¿Qué significa JSON?

a. JavaScript Online Notation

b. JavaScript Over None

c. JavaScript Object Notation

d. JavaScript Over Network

- La respuesta correcta es:
JavaScript Object Notation

---

8. La escritura mediante JDBC conlleva:

a. Todas son correctas.

b.  Ejecutar sentencias y almacenar los objetos.

c. Copiar todos los valores de las propiedades de un objeto en la sentencia

d. Abrir una conexión.

- La respuesta correcta es:
Todas son correctas.

---

9. ¿Qué tipo de objeto se utiliza para manejar errores durante la ejecución de consultas en JDBC?

a. JDBCException

b. DatabaseException

c. SQLException

d. QueryException

- La respuesta correcta es:
SQLException

---

10. ¿Cómo se seleccionan los elementos <titulo> de un documento XML utilizando XPath?

a. `/titulo`

b. `>titulo`

c. `//titulo`

d. `titulo/`

- La respuesta correcta es:
//titulo

---

11. ¿Cuál es el formato comúnmente utilizado para representar documentos en MongoDB?

a. CSV

b. JSON/BSON

c. YAML

d. XML

- La respuesta correcta es:
JSON/BSON

---

12. ¿Qué palabra clave en XQuery se usa para ordenar los resultados?

a. GROUP BY

b. SORT BY

c. FILTER BY

d. ORDER BY

- La respuesta correcta es:
ORDER BY

---

13. ¿Qué es el polimorfismo en una base de datos orientada a objetos?

a. La capacidad de un programa para contener múltiples funciones.

b. La capacidad de una clase para tener múltiples subclases.

c. La capacidad de un método para operar con diferentes tipos de datos.

d. La capacidad de una base de datos para contener múltiples tipos de datos.

- La respuesta correcta es:
La capacidad de un método para operar con diferentes tipos de datos.

---

14. ¿Cómo se cierra una conexión a una base de datos en JDBC?

a. Se cierra sin ningún método

b. connection.stop()

c. connection.end()

d. connection.close()

- La respuesta correcta es:
connection.close()

---

15. En MongoDB, ¿qué método se usa para insertar múltiples documentos a la vez?

a. addMultiple()

b. insertMultiple()

c. insertMany()

d. addMany()

- La respuesta correcta es:
insertMany()

---

16. ¿Qué significa NoSQL y cuál es su principal diferencia con las bases de datos relacionales?

a. NoSQL significa "No Standard Query Language" y se refiere a bases de datos que no utilizan un lenguaje de consulta estándar como SQL.

b. No Simple Query Language; no utiliza SQL como lenguaje de consulta.

c. No solo SQL; permite estructuras de datos flexibles.

- La respuesta correcta es:
No solo SQL; permite estructuras de datos flexibles.

---

17. ¿Cuál es la anotación principal utilizada para marcar una clase como una entidad en JPA?

a. @Table

b. @PersistenceContext

c. @Entity

d. @Id

- La respuesta correcta es:
@Entity

---

18. Para leer una entidad por su ID en JPA, ¿qué método se utiliza?

a. find()

b. get()

c. write()

d. read()

- La respuesta correcta es:
find()

---

19. ¿Qué caracteriza a una base de datos documental como MongoDB?

a. Almacena datos exclusivamente en formato binario

b. Solo admite consultas SQL

c. Utiliza un modelo de datos basado en documentos JSON o BSON

d. No permite la indexación de datos

- La respuesta correcta es:
Utiliza un modelo de datos basado en documentos JSON o BSON

---

20. ¿Cómo se comenta una línea en XQuery?

a. `*/ Comentario */`

b. `(: comentario :)`

c. `// comentario`


d. `<!-- comentario -->`

- La respuesta correcta es:
`(: comentario :)`

<br>

[Volver al Índice](#índice)

<br>
