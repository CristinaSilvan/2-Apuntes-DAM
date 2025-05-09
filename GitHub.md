# Índice
- [Conceptos importantes](#conceptos-importantes)

- [Explicación de comandos básicos](#explicación-de-comandos-básicos)

- [Crear un repositorio](#crear-un-repositorio)
    - [Nivel Básico](#nivel-básico)
    - [Nivel Avanzado](#nivel-avanzado)

- [Descargar un repositorio con contenido](#descargar-un-repositorio-con-contenido)

- [Subir cambios](#subir-cambios)

- [Recuperar un archivo de una versión previa](#recuperar-un-archivo-de-una-versión-previa)

- [Parámatros avanzados para los comandos](#parámetros-avanzados-para-los-comandos)
    - [Para el comando: `git commit`](#parámetros-para-git-commit)
    - [Para el comando: `git add`](#parámetros-para-git-add)
    - [Para el comando: `git rm`](#parámtros-para-git-rm)
    - [Para el comando: `git clean`](#parámtros-para-git-clean)
    
- [Instrucciones avanzadas](#instrucciones-avanzadas)

<br>

---
---
---

<br>

# Conceptos importantes

<br>

## Git vs Git Bash

`Git` es un sistema de control de versiones distribuido que permite llevar un registro de los cambios en tu código a lo largo del tiempo. Git te permite trabajar de manera eficiente en proyectos de software con múltiples colaboradores.

`Git Bash` es un emulador de terminal que proporciona una interfaz de línea de comandos similar a la de Linux o Mac, pero en Windows. Puedes usar Git Bash para ejecutar comandos de Git.

`Git GUI` es una interfaz gráfica de usuario para interactuar con Git. A través de Git GUI, los usuarios pueden realizar las mismas operaciones que en la terminal, pero en un entorno visual y fácil de usar, lo que puede hacer que trabajar con Git sea más accesible para aquellos que prefieren una interfaz gráfica en lugar de la línea de comandos.

<br>

## Repositorios (Local vs Remoto)

- `Repositorio Local` es el repositorio que tienes en tu computadora, donde se guardan todos tus archivos y el historial de cambios (commits) en el proyecto.

- `Repositorio Remoto` es un repositorio alojado en un servidor (como GitHub, GitLab o Bitbucket). Es donde puedes subir tu código para compartirlo o colaborar con otros.

<br>

## Staging Area
`Staging` es el área intermedia entre tu trabajo y el historial de versiones en Git. Cuando realizas cambios en tus archivos, Git no los guarda inmediatamente en el historial. Primero debes agregar esos cambios al `staging area` o `área de preparación`

<br>

## Commits

`Commit` es el proceso de guardar tus cambios de manera oficial en el historial de Git. 

Un commit es como un "punto de control" que incluye los cambios que has hecho en los archivos y directorios locales desde el último commit.

<br>

## Push y Pull

`push` significa subir los cambios de tu repositorio local al repositorio remoto.

`pull` o `fetch` significa obtener los cambios más recientes del repositorio remoto y traerlos a tu repositorio local.

<br>

## Untracked (No Rastreados)

Son los archivos y directorios que están en tu directorio local pero que Git no está siguiendo. 

Es decir, Git no los está controlando ni los tiene registrados en su base de datos para hacer seguimiento de los cambios porque no han sido añadidos al área de `staging` con `git add`

Los que estén en `staging`, aunque no se haya hecho todavía el `push`, no se consideran archivos no rastreados. Esos archivos están en una `fase de staging` y están listos para ser `confirmados` o `commited`

<br>

## .gitignore

`.gitignore` es un archivo donde defines qué archivos o carpetas no deben ser rastreados por Git. 

Es útil para evitar que archivos temporales, de configuración local o binarios (que no son necesarios para el proyecto) se suban al repositorio remoto.

Si no quieres que se suban archivos de configuración del editor, puedes poner algo como:

```
*.log
*.tmp
.vscode/
```

<br>

## Branchs (Ramas)

`Branch` es una línea de desarrollo que te permite trabajar de forma aislada en nuevas características sin afectar el código principal.

<br>

## Merge Conflicts (Conflictos de fusión)

Los conflictos de fusión ocurren cuando Git no puede combinar dos `branchs`

Esto sucede cuando los mismos archivos han sido modificados de manera diferente en las dos ramas que se están fusionando, y Git no sabe cuál de las versiones debe mantener.

<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---

<br>

# Explicación de comandos básicos

<br>

## 1. Configuración inicial
Antes de empezar a trabajar con Git, necesitas configurar tu nombre y correo electrónico, ya que Git usará esta información en los commits.

```
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@ejemplo.com"
```

Estos comandos configuran tu identidad para todos los repositorios en tu máquina. Si solo quieres configurar esta información para un repositorio específico, omite --global.

<br>

## 2. Crear un repositorio local

### `Git Clone`
---

Cuando estás trabajando en equipo, el primer paso generalmente es clonar un repositorio de GitHub a tu máquina local para poder trabajar en él. Copia todo lo que se encuentra en remoto y lo vuelca en tu ordenador. Igualmente, este comando puede usarse para crear un repositorio desde cero.

```git clone https://github.com/usuario/repositorio.git .```


> Es importante el punto tras la ruta para que no se cree una subcarpeta y dé problemas de sincronización

<br>
<br>


### `Git Init` y `Git Remote`
---

Si por el contrario, el repositorio remoto lo has creado o está vacío, se debe ejecutar primero `git init`

Convierte un directorio en un repositorio de Git donde puedes empezar a hacer un seguimiento de los cambios, realizar commits, y gestionar versiones de tu proyecto. 

Este comando crea una carpeta oculta llamada `.git` dentro del directorio que contiene toda la información que Git necesita, como las configuraciones, los registros de commits, las referencias, entre otros.

<br>
<br>

Posteriormente, se ejecuta el comando:

`git remote add origin https://github.com/usuario/repositorio.git`

> Este comando no necesita el punto tras la ruta, para que no cree subcarpetas y se produzcan errores de sincronización

<br>
<br>

`git remote` se refiere a los repositorios remotos asociados a tu repositorio local.

`add` es la acción de agregar un nuevo repositorio remoto.

`origin` es el nombre estándar dado al repositorio remoto.

`<URL del repositorio remoto>` es la dirección del repositorio remoto en GitHub.
La URL puede ser en HTTPS o SSH, dependiendo de cómo quieras autenticarte con el repositorio remoto.

<br>

## 3. Ver el estado del repositorio
Para ver qué archivos han cambiado, qué archivos están listos para ser "commiteados", o qué archivos han sido añadidos al staging area, podemos usar ```git status```

Este comando te mostrará una visión general de los cambios en tu repositorio.

<br>

## 4. Añadir cambios a la zona de "staging" (preparar para commit)
Cuando haces cambios en tu código, esos cambios primero deben ser añadidos a la zona de "staging" para ser preparados antes de hacer un commit. 

Para añadir todos los cambios ```git add .```

<br>
<br>

Si solo quieres añadir un archivo en particular:

```git add nombre_archivo```
> Ejemplo:  `git add index.html`  `git add script.js`  `git add style.css` 

Si solo quieres actualizar una carpeta:

`git add mi_carpeta/`

<br>

## 5. Hacer un commit
Un commit es como un "punto de restauración" en tu proyecto. Cada vez que haces un commit, estás guardando el estado de tu trabajo.

```git commit -m "Descripción de los cambios"```

No se puede hacer un commit vacío.

<br>

## 6. Ver el historial de commits y Control de Cambios

```git log``` muestra una lista de todos los commits realizados en el repositorio.

Para salir del log y volver a la terminal, presiona la tecla `Q`

<br>

Para ver el historial de commits de forma más compactas y visual se usa el comando:

```git log --oneline --graph --decorate --all```

<br>

`git status` muestra el estado actual del repositorio, qué archivos han sido modificados, cuáles están en el área de staging, y cuáles no han sido rastreados.

<br>

`git diff` muestra las diferencias entre los archivos modificados y los no guardados en el área de staging.

<br>

## 7. Actualizar tu repositorio local con los cambios remotos
Cuando trabajas en equipo, otros pueden haber realizado cambios en el repositorio que tú no tienes en tu máquina local. Para actualizar tu repositorio local con los últimos cambios remotos, usas:

```git pull origin main``` o `git pull` si previamente has establecido la rama remota como predeterminada para futuras referencias con el parametro `-u` o `--set-upstream`

Este comando trae los cambios desde el repositorio remoto y los fusiona con tu copia local. Si la rama se llama de otra forma, cambiar `main` por el nombre de la rama de la que quieres hacer el volcado en tu PC.

<br>

## 8. Enviar tus cambios al repositorio remoto (GitHub)
Una vez que hayas hecho tus commits localmente, puedes subir esos cambios al repositorio remoto en GitHub para que otros los vean:

```git push origin main``` o `git push` si previamente has establecido la rama remota como predeterminada para futuras referencias con el parametro `-u` o `--set-upstream`

Este comando sube tus cambios a la rama main del repositorio remoto. Si estás trabajando con una rama diferente, reemplaza main por el nombre de la rama que estés usando.

Por sí solo `git push` generalmente intenta empujar los cambios a la rama predeterminada de tu repositorio remoto hacia la rama en la que estás trabajando localmente.

El problema es que en un repositorio nuevo o en ciertas configuraciones, Git no sabe a qué rama remota debes enviar los cambios, por lo que puede fallar o no hacer nada si no tienes una rama predeterminada configurada.

En el comando ```git push origin main``` estás especificando exactamente en qué rama del repositorio remoto `origin` quieres que Git suba las modificaciones de tu rama `main` de tu repositorio local.

`origin` es el nombre por defecto que Git le da al repositorio remoto que clonaste de GitHub,pero puede ser configurada para que tenga un nombre diferente en tu `gitbash` 

`main` es el nombre de la rama principal. Anteriormente, se usaba master como nombre por defecto para la rama principal, pero en muchos proyectos nuevos, se ha cambiado por convención.

<br>

## 9. Ver las ramas

Para ver las ramas existentes en tu repositorio local:

```git branch```

<br>

Para ver las ramas existentes en el repositorio remoto:

```git branch -r```

<br>


Para ver tanto las ramas en remoto y local:

```git branch -a```

<br>

## 10. Crear una nueva rama (branch)
Cuando trabajas en equipo, generalmente se recomienda trabajar en ramas para no afectar la rama principal `main` pudiendo hacer commits en la nueva rama sin afectar el trabajo en `main`

Para crear una nueva rama: 

```git checkout -b nombre-de-la-rama```


<br>

## 11. Cambiar entre ramas
Si ya has creado varias ramas y quieres cambiarte a una de ellas, usa:

```git checkout nombre-de-la-rama```

<br>

## 12. Fusionar (merge) una rama
Cuando terminas de trabajar en una rama y quieres fusionarla con la rama principal, puedes usar:

```
git checkout main
git merge nombre-de-la-rama
```
Este comando fusionará los cambios de `nombre-de-la-rama` en `main`

<br>

## 14. Eliminar una rama
Una vez que una rama ha sido fusionada y ya no la necesitas, puedes eliminarla localmente con:

```git branch -d nombre-de-la-rama```

Si la rama aún no ha sido fusionada y estás seguro de que deseas eliminarla, usa `-D` en lugar de `-d`

<br>

## 15. Eliminar untracked files (archivos no rastreados)

Elimina archivos y directorios que están en el repositorio local pero que no han sido agregados al staging con `git add`

```git clean```

También elimina archivos están listados en el archivo `.gitignore` pero no están siendo rastreados por Git.

<br>

## 16. Mostrar el historial de los cambios de referencia

Permite ver el registro de todas las actualizaciones que han afectado a las referencias de tu repositorio (como HEAD, ramas, etc.) a lo largo del tiempo.

```git reflog```

Cada vez que se mueve una referencia, como cuando cambias de rama, haces un commit, un merge, un rebase o incluso cuando se hace un reset, Git registra esos cambios en el reflog. Es útil para recuperar referencias anteriores o para deshacer cambios que de otro modo habrías perdido, ya que Git guarda información sobre estos movimientos incluso después de que los cambios sean eliminados o se "pierdan".

```
$ git reflog
b0981a7 HEAD@{0}: commit: Agregado nuevo archivo
342f672 HEAD@{1}: checkout: moving from featureX to main
4a13f9a HEAD@{2}: commit: Corregido bug en la función Y
90df18e HEAD@{3}: commit (amend): Modificado el commit anterior
```

- ID del commit: El hash del commit que se realizó en ese momento.

- Referencia anterior (HEAD@{n}): Muestra una referencia a los estados anteriores de tu HEAD, donde n es el número de referencia.

- Acción realizada: Qué operación ocurrió (como un commit, checkout, merge, rebase, etc.).

- Mensaje del commit o acción: Un resumen del mensaje o acción correspondiente.

<br>

## 17. Vaciar repositorio local

Elimina todos los archivos excepto el `.git`

```find . -not -path './.git*' -exec rm -rf {} +```

<br>
<br>

[Volver al índice](#índice)

<br>
---
---
---

<br>

# Crear un repositorio

<br>

## Nivel Básico

## 1. Abrir el GitBash sobre la carpeta que se convertirá en el repositorio local o crearlo

Abrir el Git Bash en la carpeta donde queremos que se cree el repositorio o navegar hasta la ruta desde el Git Bash con el siguiente comando:

```
cd /c/Users/TuUsuario/Documents/GitHub <-- El bash debe tener la URL en inglés
mkdir mi-repositorio
cd mi-repositorio
```

> Las rutas en Git Bash son diferentes a las rutas de la consola de Windows 

- Windows cmd:

    ```C:/Usuario/TuUsuario/Documentos/```

- Git Bash:

    ```/c/Users/TuUsuario/Documents/```

<br>

## 2. Acceder si no lo has hecho previamente

```
git config --global user.name "Tu Nombre"

git config user.email "email_de_github@...com"
```

> Esta configuración es global para tu pc, si necesitas una configuración para un repositorio en específico, se ejecuta la misma sentencia sin `--global`

<br>

## 3. Enlazar con el repositorio remoto

```git clone https://github.com/usuario/repositorio.git .```

> `git clone` realiza todas las tareas que `git init` hace, por lo que no es necesario ejecutar `git init` si vas a hacer un `git clone`.

> Es importante el punto tras la ruta para que no se cree una subcarpeta y dé problemas de sincronización

<br>

## 4. Hacer el primer commit

> Si has creado el respositorio remoto con un `README.md` o una `licencia` por accidente en lugar de crearlo vacío, debes hacer este paso para [solucionar conflictos](#6-volcar-los-archivos-en-el-repositorio-local) antes de continuar

<br>

Para subir un cambio específico:

```git add archivo.txt```

Para subir cualquier cambio en el repositorio local:

```git add .```

Añadir un mensaje descriptivo al commit:

```git commit -m "Descripción de los cambios"```

<br>

## 5. Subir los cambios al repositorio remoto

Tras ejecutar este comando la primera vez, se puede realizar el resto de cambios directamente con `git push` sin tener que especificar `origin` y `main` cada vez.

```git push -u origin main```

`origin` es el nombre de tu repositorio remoto.

`main`es la rama principal (si estás usando una rama que no sea la creada por defecto, cambia el nombre en el comando)

`-u` establece la rama remota como predeterminada para futuras referencias

Una vez hecho estos pasos, ya puedes actualizar el repositorio remoto de forma más sencilla cuando trabajes sobre tu repositorio local -> [Cómo subir cambios](#subir-cambios)

> La diferencia entre `git push --set-upstream origin main` y `git push -u origin main` es básicamente sinónima. Ambos comandos logran el mismo objetivo, pero la diferencia radica en la forma en que se escribe el comando. El `-u` es una forma corta (alias) de `--set-upstream`.

<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---

<br>

## Nivel Avanzado

## 1. Abrir el GitBash sobre el repositorio local

```
cd /c/Users/TuUsuario/Documents/GitHub <-- El bash quiere la URL en inglés
mkdir mi-repositorio
cd mi-repositorio

```

<br>

## 2. Acceder si no lo has hecho previamente

```
git config --global user.name "Tu Nombre"

git config user.email "email_de_github@...com"
```

<br>

## 3. Inicializar el repositorio local:

```git init```

<br>

## 4. Enlazar con el repositorio remoto

Agrega un repositorio remoto a tu repositorio local existente:

```git remote add origin https://github.com/TuUsuario/mi-repositorio.git```

Verifica las configuraciones remotas para comprobar que `push` y `fetch` están configurados correctamente:

```git remote -v```

<br>

## 5. Asegurar el nombre de la rama principal como main

GitHub, a partir de 2020, decidió cambiar el nombre de la rama predeterminada de master a main en los nuevos repositorios. Por lo tanto, cuando creas un repositorio en GitHub, en vez de crear una rama master por defecto, se crea main.

Cuando clonas un repositorio de GitHub o trabajas en un repositorio local recién creado, es posible que aún estés trabajando en la rama master (si el repositorio tiene una rama predeterminada más antigua o si tú mismo usaste el nombre anterior).

```git branch -M main```

`-M` indica que el nombre de la rama se cambiará de manera forzada (si ya existe una rama con ese nombre, la reemplazará). En este caso, cambia el nombre de la rama actual (por defecto master) a main.

<br>

## 6. Volcar los archivos en el repositorio local

En caso de que haya un README.md o un LICENSE por ejemplo en lugar de tener un repositorio vacío, para evitar conflictos ejecutar la sentencia:

```git pull origin main --allow-unrelated-histories```

Como GitHub tiene un commit inicial, usarás el comando `git pull` con la opción ``--allow-unrelated-histories`` porque estás fusionando dos historiales de commits que no tienen relación entre sí (el historial local vacío y el historial remoto con un commit).

<br>

## 7. Hacer el primer commit

```git add .```

```git commit -m "Descripción de los cambios"```

<br>

## 8. Subir los cambios al repositorio remoto

Tras ejecutar este comando la primera vez, se puede realizar el resto de cambios directamente con `git push` sin tener que especificar `origin` y `main` cada vez.

```git push -u origin main```

`-u` establece la rama remota como predeterminada para futuras referencias

La diferencia entre `git push --set-upstream origin main` y `git push -u origin main` es básicamente sinónima. Ambos comandos logran el mismo objetivo, pero la diferencia radica en la forma en que se escribe el comando. El `-u` es una forma corta (alias) de `--set-upstream`.

<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---

<br>

# Descargar un repositorio con contenido

<br>

## 1. Abrir el GitBash sobre la carpeta que se convertirá en el repositorio local o crearlo

Abrir el Git Bash en la carpeta donde queremos que se cree el repositorio o navegar hasta la ruta desde el Git Bash con el siguiente comando:

```
cd /c/Users/TuUsuario/Documents/GitHub <-- El bash debe tener la URL en inglés
mkdir mi-repositorio
cd mi-repositorio
```

<br>

## 2. Acceder si no lo has hecho previamente

```
git config --global user.name "Tu Nombre"

git config user.email "email_de_github@...com"
```

> Esta configuración es global para tu pc, si necesitas una configuración para un repositorio en específico, se ejecuta la misma sentencia sin `--global`

<br>

## 3. Enlazar con el repositorio remoto

```git clone https://github.com/usuario/repositorio.git .```

`git clone` realiza todas las tareas que `git init` hace, por lo que no es necesario ejecutar `git init` si vas a hacer un `git clone`.

> Es importante el punto tras la ruta para que no se cree una subcarpeta y dé problemas de sincronización


<br>
<br>


Verifica las configuraciones remotas para comprobar que `push` y `fetch` están configurados correctamente:

```git remote -v```

<br>

## 4. Asegurar el nombre de la rama principal como main

GitHub, a partir de 2020, decidió cambiar el nombre de la rama predeterminada de master a main en los nuevos repositorios. Por lo tanto, cuando creas un repositorio en GitHub, en vez de crear una rama master por defecto, se crea main.

Cuando clonas un repositorio de GitHub o trabajas en un repositorio local recién creado, es posible que aún estés trabajando en la rama master (si el repositorio tiene una rama predeterminada más antigua o si tú mismo usaste el nombre anterior).

```git branch -M main```

`-M` indica que el nombre de la rama se cambiará de manera forzada (si ya existe una rama con ese nombre, la reemplazará). 

En este caso, cambia el nombre de la rama actual a `main`

<br>

## 6. Volcar los archivos en el repositorio local


```git pull origin main``` o `git pull`


<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---

<br>

# Subir cambios

Teniendo GitBash abierto en el repositorio remoto: 

## Paso 1: Agregar cambios al Stage

`git add .`

> `git add nombre_archivo.txt` si solo quieres que se actualice un archivo
> `git add mi_carpeta/` si solo quieres actualizar una carpeta

<br>

## Paso 2: Confirmar cambios

`git commit -m "Mensaje descriptivo de los cambios`

<br>

## Paso 3: Aplicar los cambios al Repositorio remoto

`git push`

<br>

Recuerda que si este el primer `push` que haces, debes utilizar el comando `git push -u origin main` para establecer la rama remota como predeterminada para futuras referencias.

Después de eso, puedes simplemente usar el comando `git push`cada vez que modifiques tu repositorio local.

> La diferencia entre `git push --set-upstream origin main` y `git push -u origin main` es básicamente sinónima. Ambos comandos logran el mismo objetivo, pero la diferencia radica en la forma en que se escribe el comando. El `-u` es una forma corta (alias) de `--set-upstream`.

<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---

<br>

# Recuperar un archivo de una versión previa

<br>

## 1. Ver el historial de commits

Para encontrar el commit en el que el archivo aún existía, ejecuta:

```git log --oneline```

Este comando mostrará los commits anteriores con sus identificadores (hash) en una forma corta. Busca el commit en el que el archivo aún estaba presente. Si sabes aproximadamente cuándo fue, esto te ayudará a encontrarlo más rápido.

<br>

## 2. Ver el contenido del archivo en un commit anterior

Una vez tengas el hash del commit que contiene el archivo, puedes usar el siguiente comando para recuperar el archivo desde ese commit:

```git checkout <commit_hash> -- <ruta/del/archivo>```

Sustituye <commit_hash> por el hash del commit que encontraste y <ruta/del/archivo> por la ruta al archivo que quieres recuperar.

Por ejemplo, si el hash es abc123 y el archivo se llama index.html, el comando sería:

```git checkout abc123 -- index.html```

<br>

## 3. Verifica que el archivo se haya recuperado

Después de ejecutar el comando, el archivo aparecerá en tu directorio de trabajo, y ya estará listo para ser añadido nuevamente al repositorio si lo deseas.

<br>

## 4. Añadir el archivo de vuelta a Git (opcional)

Si quieres que el archivo vuelva a formar parte de tu repositorio, ejecuta los siguientes comandos:

```
git add <ruta/del/archivo>
git commit -m "Recuperado el archivo <nombre del archivo>"
git push
```

<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---

<br>

# Parámetros avanzados para los comandos

<br>

## Parámetros para `git commit`

### `-a` y `--all`
La opción -a hace que Git agregue automáticamente todos los archivos modificados y rastreados (pero no los nuevos archivos no añadidos aún con git add) al área de preparación antes de hacer el commit. Esto ahorra tiempo si ya has modificado archivos pero olvidaste añadirlos manualmente con git add.

```git commit -a -m "Corregir errores en el código"```

Este comando hará un commit de todos los archivos modificados y previamente rastreados (sin necesidad de hacer git add antes).

<br>

### `--amend`
Si cometiste un error en tu último commit (por ejemplo, olvidaste añadir un archivo o cometiste un error tipográfico en el mensaje), puedes usar la opción --amend para modificar el commit anterior.

```git commit --amend -m "Actualizar mensaje del commit"```

Este comando abre una oportunidad para modificar el último commit, ya sea para cambiar el mensaje o incluir cambios adicionales. Ten en cuenta que esto reescribe el historial, por lo que debes tener cuidado al usarlo si ya has compartido el commit con otros colaboradores.

<br>

### `--no-edit`
Cuando usas git commit --amend para modificar el commit anterior y no quieres cambiar el mensaje, puedes usar --no-edit. Esto mantiene el mensaje original del commit.

```git commit --amend --no-edit```

Modifica el commit anterior, pero conserva el mensaje original.

<br>

### `--date`
Si necesitas establecer una fecha personalizada para un commit (por ejemplo, cuando estás trabajando en un repositorio y quieres que el commit aparezca como si se hubiera realizado en un día anterior), puedes usar --date para especificar la fecha.

```git commit --date="2025-02-01 15:00:00" -m "Commit con fecha personalizada"```

Crea el commit como si se hubiera realizado en la fecha y hora especificadas.

<br>

### `--author`
Si por alguna razón necesitas hacer un commit con un autor diferente (por ejemplo, si estás trabajando en el repositorio de otra persona o colaborando en un proyecto), puedes especificar un autor con la opción --author.

```git commit --author="Autor Ejemplo <autor@ejemplo.com>" -m "Commit de otro autor"```

<br>

### `--verbose`
Esta opción muestra más detalles sobre los cambios que se están realizando en el commit, como un resumen de los archivos que se modificaron.

```git commit --verbose -m "Explicar detalles del commit"```

<br>

### `--dry-run`
Esta opción te permite ver qué cambios se cometerían, pero sin hacer realmente el commit. Es útil para revisar qué se incluiría en el commit antes de ejecutarlo.

```git commit --dry-run -m "Ver qué cambios se cometen"```

Muestra los archivos que se incluirían en el commit, pero no hace ningún cambio real.

<br>

---

<br>

## Parámetros para `git add`


### `-f`
El -f le dice a Git que añada el archivo a pesar de que esté ignorado en el .gitignore.

```git add -f archivo.png```

<br>

---

<br>

## Parámtros para `git rm`

### `-r --cached`

Limpiar la caché del repositorio

```git rm -r --cached .```

<br>


## Parámtros para `git clean`

### `-n` o `--dry-run`

`git clean -n` o `git clean --dry-run` simulan la operación de eliminación de los archivos no rastreados y te muestra qué archivos o directorios serían eliminados sin borrarlos realmente. 

Es una buena forma de verificar qué pasaría antes de ejecutar el comando de forma definitiva.

Te mostrará los archivos y directorios que serían eliminados si ejecutas el comando `git clean -f` como una "prueba" antes de proceder con la limpieza real.

> Ejemplo de salida: 
>```
>Would remove build/
>Would remove temp.txt
>```

<br>

### `-f` o `--force`

`git clean -f` o `git clean --force` eliminan los archivos no rastreados. Este comando es definitivo y eliminará esos archivos no rastreados. Es importante tener cuidado al usarlo, ya que no hay forma fácil de recuperarlos después de que se eliminen.

El `-f` o `force` es necesario porque Git quiere evitar eliminar archivos accidentalmente sin querer. Si no los usas, Git no eliminará nada.

> No elimina los directorios

<br>

### `-fd`

`git clean -fd` elimina tanto los archivos no rastreados, como los directorios vacíos o aquellos que no están siendo rastreados por Git.

<br>

### `-fx`

`git clean -fx` elimina archivos no rastreados y archivos especificados en `.gitignore`

### `-fdx`

`git clean -fdx` es la combinación de los anteriores.

Borra los archivos no rastreados, los directorios vacíos o no rastreados y los archivos especificados en `.gitignore`

<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---

<br>

# Instrucciones avanzadas

<br>

## Habilitar a Git para que maneje rutas largas

```git config --global core.longpaths true```

<br>

## Forzar al repositorio local a ser exacto al remoto

```
git fetch origin
git reset --hard origin/main
```

<br>
<br>

[Volver al índice](#índice)

<br>

---
---
---
