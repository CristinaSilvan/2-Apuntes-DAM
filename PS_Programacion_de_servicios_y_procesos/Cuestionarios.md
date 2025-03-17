# Índice
- [Cuestionario 1 (Programación multiproceso)](#cuestionario-1-programación-multiproceso)

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

[Volver al índice]()

---
---
---