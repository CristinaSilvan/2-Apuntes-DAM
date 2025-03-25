# Índice

<br>

- [Cuestionario 1 (Programación multiproceso)](#cuestionario-1-programación-multiproceso)

<br>

- [Autoevaluación 1](#autoevaluación-1)
- [Autoevaluación 2](#autoevaluación-2)

<br>

---
---
---


# Cuestionario 1 (Programación multiproceso)

1. ¿Qué es un proceso en el contexto de la programación multiproceso?

        a. Un bloque de código que se ejecuta secuencialmente


        b. Una unidad básica de ejecución que tiene su propio espacio de direcciones de memoria


        c. Una función que se ejecuta en el mismo espacio de direcciones

- La respuesta correcta es:
Una unidad básica de ejecución que tiene su propio espacio de direcciones de memoria

---

2. ¿Cuál es la principal diferencia entre un proceso y un hilo?

        a. Los procesos son más rápidos que los hilos


        b. Un proceso tiene su propio espacio de direcciones, mientras que los hilos comparten el mismo espacio de direcciones


        c. Los hilos no pueden comunicarse entre sí, mientras que los procesos pueden

- La respuesta correcta es:
Un proceso tiene su propio espacio de direcciones, mientras que los hilos comparten el mismo espacio de direcciones

---

3. ¿Qué mecanismo se usa para la sincronización entre procesos en un entorno multiproceso?

        a. Buffers de entrada/salida


        b. Semáforos y mutexes


        c. Variables globales

- La respuesta correcta es:
Semáforos y mutexes

--- 

4. ¿Cuál de los siguientes problemas se puede producir en un entorno de programación multiproceso si varios procesos acceden a la misma variable global sin sincronización adecuada?

        a. Race condition (condición de carrera)


        b. Deadlock (interbloqueo)


        c. Starvation (hambre)

- La respuesta correcta es:
Race condition (condición de carrera)

---

5. ¿Qué es un semáforo en la programación multiproceso?

        a. Un tipo de variable global compartida


        b. Un mecanismo para controlar el acceso a recursos compartidos


        c. Un tipo de proceso independiente

- La respuesta correcta es:
Un mecanismo para controlar el acceso a recursos compartidos

---

6. ¿Cuál es la función principal de un mutex en la programación multiproceso?

        a. Gestionar la comunicación entre procesos


        b. Sincronizar el acceso a recursos compartidos para evitar conflictos


        c. Permitir que varios procesos accedan a recursos compartidos simultáneamente

- La respuesta correcta es:
Sincronizar el acceso a recursos compartidos para evitar conflictos

---

7. ¿Qué es un deadlock en el contexto de la programación multiproceso?

        a. Un error de sintaxis en el código


        b. Una condición en la que un proceso se ejecuta más rápido de lo esperado


        c. Una condición en la que dos o más procesos están esperando indefinidamente por recursos que están bloqueados por otros procesos

- La respuesta correcta es:
Una condición en la que dos o más procesos están esperando indefinidamente por recursos que están bloqueados por otros procesos

---

8. ¿Cómo se puede evitar el starvation (hambre) en un sistema multiproceso?

        a. Utilizando semáforos binarios


        b. Incrementando la prioridad de los procesos en espera


        c. Implementando políticas de planificación de procesos justas

- La respuesta correcta es:
Implementando políticas de planificación de procesos justas

---

9. ¿Qué es una condición de carrera en la programación multiproceso?

        a. Una condición en la que el resultado de un proceso depende del orden de ejecución de otros procesos


        b. Un error que ocurre cuando un proceso no tiene suficiente memoria para ejecutarse


        c. Una condición en la que un proceso obtiene acceso exclusivo a un recurso

- La respuesta correcta es:
Una condición en la que el resultado de un proceso depende del orden de ejecución de otros procesos

---

10. ¿Qué técnica se utiliza para asegurar que un recurso compartido sea accesible solo por un proceso a la vez?

        a. Gestión de memoria virtual


        b. Programación orientada a objetos


        c. Exclusión mutua

- La respuesta correcta es:
Exclusión mutua

[Volver al índice](#índice)

---
---
---

<br>

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

<br>

# Autoevaluación 2

<br>

1. ¿Qué característica define principalmente a un sistema Cliente/Servidor?

a.
El procesamiento cooperativo de la información

b.
La existencia de una única base de datos

c.
La necesidad de una red local

d.
El uso exclusivo de protocolos TCP/IP

- La respuesta correcta es:
El procesamiento cooperativo de la información

---

2. ¿Para qué se utiliza el método join()?

a.
Para esperar a que un hilo termine su ejecución antes de continuar

b.
Para unir dos hilos en uno solo

c.
Para sincronizar el acceso a recursos compartidos

d.
Para crear un nuevo hilo

- La respuesta correcta es:
Para esperar a que un hilo termine su ejecución antes de continuar

---

3. ¿Qué es un deadlock en programación multihilo?

a.
Una situación donde dos o más hilos se bloquean mutuamente esperando recursos

b.
Un error de compilación en código multihilo

c.
Cuando un hilo consume demasiada memoria

d.
Cuando todos los hilos terminan su ejecución

- La respuesta correcta es:
Una situación donde dos o más hilos se bloquean mutuamente esperando recursos

---

4. ¿Cuál es una ventaja principal del uso de múltiples hilos?

a.
Mejor aprovechamiento de los recursos del sistema y mayor capacidad de respuesta

b.
Eliminación total de errores de programación

c.
Menor consumo de memoria RAM

d.
Garantía de ejecución más rápida siempre

- La respuesta correcta es:
Mejor aprovechamiento de los recursos del sistema y mayor capacidad de respuesta

---

5. ¿Qué es una condición de carrera en programación multihilo?

a.
Cuando el resultado depende del orden de ejecución de los hilos

b.
Cuando un hilo es más rápido que otro

c.
Cuando dos hilos tienen la misma prioridad

d.
Cuando un hilo termina antes que otro

- La respuesta correcta es:
Cuando el resultado depende del orden de ejecución de los hilos

---

6. Un hilo o thread es:

a.
Una secuencia de tareas encadenadas que puede ser ejecutada por el sistema operativo

b.
Un proceso completo del sistema operativo con su propio espacio de memoria

c.
Una conexión física entre dos componentes del ordenador

d.
Un archivo del sistema operativo

- La respuesta correcta es:
Una secuencia de tareas encadenadas que puede ser ejecutada por el sistema operativo

---

7. ¿Qué recursos comparten los hilos de un mismo proceso?

a.
Código, datos y recursos del sistema operativo

b.
Solo la pila de ejecución

c.
Nada, son completamente independientes

d.
Solo los registros del procesador

- La respuesta correcta es:
Código, datos y recursos del sistema operativo

---

8. ¿Cuál es la principal función del protocolo TCP en una red?

a.
Configurar routers

b.
Comunicar directamente entre dos nodos

c.
Asignar direcciones IP

d.
Gestionar nombres de dominio

- La respuesta correcta es:
Comunicar directamente entre dos nodos

---

9. ¿Qué diferencia hay entre interrupted() e isInterrupted()?

a.
interrupted() es estático y limpia el flag de interrupción, isInterrupted() no lo es.

b.
No hay ninguna diferencia, son sinónimos.

c.
interrupted() termina el hilo, isInterrupted() solo lo pausa.

d.
isInterrupted() es estático y interrupted() no lo es.

- La respuesta correcta es:
interrupted() es estático y limpia el flag de interrupción, isInterrupted() no lo es

---

10. ¿Cuáles son las dos formas de crear un hilo en Java?

a.
Extendiendo Thread e implementando Runnable

b.
Implementando Thread y extendiendo Runnable

c.
Usando new Thread() y new Process()

d.
Implementando Threading y MultiThread

- La respuesta correcta es:
Extendiendo Thread e implementando Runnable

---

11. En una arquitectura Cliente/Servidor, el término "front-end" se refiere a:

a.
El middleware

b.
La base de datos

c.
El proceso cliente

d.
El proceso servidor

- La respuesta correcta es:
El proceso cliente

---

12. ¿Qué elemento proporciona la conectividad entre el cliente y el servidor?

a.
El protocolo HTTP

b.
El middleware

c.
La interfaz gráfica

d.
La base de datos

- La respuesta correcta es:
El middleware

- Explicación: 

 - Aunque HTTP es un protocolo de comunicación, el middleware es la respuesta más completa.

---

13. ¿Cuál es un ejemplo típico de aplicación multihilo?

a.
Un procesador de texto que guarda automáticamente mientras se escribe

b.
Una calculadora básica

c.
Un bloc de notas simple

d.
Un reloj digital básico

- La respuesta correcta es:
Un procesador de texto que guarda automáticamente mientras se escribe

---

14. En el esquema de funcionamiento Cliente/Servidor, ¿cuál es el primer paso?

a.
El servidor envía resultados

b.
El cliente procesa resultados

c.
El servidor procesa la información

d.
El cliente solicita una información al servidor

- La respuesta correcta es:
El cliente solicita una información al servidor

---

15. ¿Cuándo pasa un hilo al estado Blocked?

a.
Cuando está esperando por un recurso o la finalización de una operación I/O

b.
Cuando termina su ejecución

c.
Cuando se crea el hilo

d.
Cuando tiene la mayor prioridad

- La respuesta correcta es:
Cuando está esperando por un recurso o la finalización de una operación I/O

---

16. ¿Para qué se utiliza la palabra clave synchronized en Java?

a.
Para controlar el acceso concurrente a recursos compartidos

b.
Para sincronizar el reloj de todos los hilos

c.
Para ejecutar hilos en orden secuencial

d.
Para aumentar la velocidad de ejecución

- La respuesta correcta es:
Para controlar el acceso concurrente a recursos compartidos

---

17. ¿Cuál es la principal diferencia entre multihilo y multiproceso?

a.
El multihilo comparte recursos dentro de un proceso, el multiproceso ejecuta programas independientes

b.
El multihilo es más lento que el multiproceso

c.
El multiproceso usa menos recursos que el multihilo

d.
No hay diferencia, son términos sinónimos

- La respuesta correcta es:
El multihilo comparte recursos dentro de un proceso, el multiproceso ejecuta programas independientes

---

18. ¿Por qué el cambio de contexto entre hilos es más rápido que entre procesos?

a.
Porque los hilos comparten el espacio de memoria del proceso

b.
Porque los hilos tienen más prioridad

c.
Porque los hilos son más pequeños

d.
Porque los hilos son más modernos

- La respuesta correcta es:
Porque los hilos comparten el espacio de memoria del proceso

---

19. ¿Qué hace el método sleep() en Java?

a.
Pausa la ejecución del hilo actual por un tiempo especificado

b.
Termina la ejecución del hilo

c.
Inicia la ejecución del hilo

d.
Cambia la prioridad del hilo

- La respuesta correcta es:
Pausa la ejecución del hilo actual por un tiempo especificado

---

20. ¿Cuál NO es un estado válido de un hilo?

a.
Hibernating

b.
Running

c.
Blocked

d.
Ready

- La respuesta correcta es:
Hibernating

<br>

[Volver al Índice](#índice)

<br>