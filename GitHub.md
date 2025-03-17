# Índice
- [Conceptos importantes](#conceptos-importantes)
- [Comandos básicos](#comandos-básicos)
- [Crear un repositorio](#crear-un-repositorio)
- [Parámtros avanzados](#parámtros-avanzados)
- [Instrucciones avanzadas](#instrucciones-avanzadas)

# Conceptos importantes

## Git vs Git Bash

- Git: Es un sistema de control de versiones distribuido que permite llevar un registro de los cambios en tu código a lo largo del tiempo. Git te permite trabajar de manera eficiente en proyectos de software con múltiples colaboradores.

- Git Bash: Es un emulador de terminal que proporciona una interfaz de línea de comandos similar a la de Linux o Mac, pero en Windows. Puedes usar Git Bash para ejecutar comandos de Git.

- Git GUI: es una interfaz gráfica de usuario para interactuar con Git. A través de Git GUI, los usuarios pueden realizar las mismas operaciones que en la terminal, pero en un entorno visual y fácil de usar, lo que puede hacer que trabajar con Git sea más accesible para aquellos que prefieren una interfaz gráfica en lugar de la línea de comandos.

## Repositorios (Local vs Remoto)

- Repositorio Local: Es el repositorio que tienes en tu computadora, donde se guardan todos tus archivos y el historial de cambios (commits) en el proyecto.

- Repositorio Remoto: Es un repositorio alojado en un servidor (como GitHub, GitLab o Bitbucket). Es donde puedes subir tu código para compartirlo o colaborar con otros.

## Staging Area
- Staging: Es el área intermedia entre tu trabajo y el historial de versiones en Git. Cuando realizas cambios en tus archivos, Git no los guarda inmediatamente en el historial. Primero debes agregar esos cambios al "staging area" (área de preparación).

## Commits

- Commit: Es el proceso de guardar tus cambios de manera oficial en el historial de Git. Un commit es como un "punto de control" que incluye los cambios que has hecho desde el último commit.

## Ramas (Branchs)

- Branch (Rama): Una rama en Git es una línea de desarrollo que te permite trabajar de forma aislada en nuevas características sin afectar el código principal.

## Push y Pull

- git push: Se usa para subir los cambios de tu repositorio local al repositorio remoto.

- git pull: Se usa para obtener los cambios más recientes del repositorio remoto y traerlos a tu repositorio local.

## .gitignore

- .gitignore: Es un archivo donde defines qué archivos o carpetas no deben ser rastreados por Git. Es útil para evitar que archivos temporales, de configuración local o binarios (que no son necesarios para el proyecto) se suban al repositorio remoto.

- Si no quieres que se suban archivos de configuración del editor, puedes poner algo como:
```
*.log
*.tmp
.vscode/
```

## Historial y Control de Cambios

- git status: Muestra el estado actual del repositorio, qué archivos han sido modificados, cuáles están en el área de staging, y cuáles no han sido rastreados.

- git log: Muestra el historial de commits del repositorio.

- git diff: Muestra las diferencias entre los archivos modificados y los no guardados en el área de staging.

## Merge Conflicts (Conflictos de fusión)

- Los conflictos de fusión ocurren cuando Git no puede combinar dos ramas debido a cambios incompatibles en los mismos archivos.

## git clone

- git clone: Se usa para hacer una copia local de un repositorio remoto. Es el primer paso cuando deseas colaborar en un proyecto existente.

- [Volver al índice](#índice)

---
---
---

# Comandos básicos

## 1. Configuración inicial:
Antes de empezar a trabajar con Git, necesitas configurar tu nombre y correo electrónico, ya que Git usará esta información en los commits.
```
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@ejemplo.com"
```

Estos comandos configuran tu identidad para todos los repositorios en tu máquina. Si solo quieres configurar esta información para un repositorio específico, omite --global.

---

## 2. Clonar un repositorio:
Cuando estás trabajando en equipo, el primer paso generalmente es clonar un repositorio de GitHub a tu máquina local para poder trabajar en él.

```git clone https://github.com/usuario/repositorio.git```

---

## 3. Ver el estado del repositorio:
Para ver qué archivos han cambiado, qué archivos están listos para ser "commiteados", o qué archivos han sido añadidos al staging area, puedes usar:

```git status```

Este comando te mostrará una visión general de los cambios en tu repositorio.

---

## 4. Añadir cambios a la zona de "staging" (preparar para commit):
Cuando haces cambios en tu código, esos cambios primero deben ser añadidos a la zona de "staging" para ser preparados antes de hacer un commit. Para añadir todos los cambios.

```git add .```

Si solo quieres añadir un archivo en particular, usa:

```git add nombre_del_archivo```

---

## 5. Hacer un commit:
Un commit es como un "punto de restauración" en tu proyecto. Cada vez que haces un commit, estás guardando el estado de tu trabajo.

```git commit -m "Descripción de los cambios"```

No se puede hacer un commit vacío.

---

## 6. Ver el historial de commits:
Para ver una lista de todos los commits realizados en el repositorio, puedes usar:

```git log```

Para salir del log y volver a la terminal, presiona la tecla Q.

```git log --oneline --graph --decorate --all```

Para ver los registros más compactos y decorados.

--- 

## 7. Actualizar tu repositorio local con los cambios remotos:
Cuando trabajas en equipo, otros pueden haber realizado cambios en el repositorio que tú no tienes en tu máquina local. Para actualizar tu repositorio local con los últimos cambios remotos, usas:

```git pull origin main```

Este comando trae los cambios desde el repositorio remoto (en GitHub) y los fusiona con tu copia local. Si la rama principal se llama master en lugar de main, usa master en lugar de main.

--- 

## 8. Enviar tus cambios al repositorio remoto (GitHub):
Una vez que hayas hecho tus commits localmente, puedes subir esos cambios al repositorio remoto en GitHub para que otros los vean:

```git push origin main```

Este comando sube tus cambios a la rama main del repositorio remoto. Si estás trabajando con una rama diferente, reemplaza main por el nombre de la rama que estés usando.

Por sí solo, git push generalmente intenta empujar los cambios a la rama predeterminada de tu repositorio remoto, que por defecto suele ser origin (el nombre del repositorio remoto por defecto) y la rama en la que estás trabajando localmente.

El problema es que en un repositorio nuevo o en ciertas configuraciones, Git no sabe a qué rama remota debes enviar los cambios, por lo que puede fallar o no hacer nada si no tienes una rama predeterminada configurada.

Aquí, estás especificando exactamente qué repositorio remoto (origin) y qué rama (main) quieres que Git empuje.

origin es el nombre por defecto que Git le da al repositorio remoto que clonaste de GitHub (aunque este nombre puede cambiar si se configura un nombre diferente).

main es el nombre de la rama principal. Anteriormente, se usaba master como nombre por defecto para la rama principal, pero en muchos proyectos nuevos, se ha cambiado a main por convención.

---

## 9. Crear una nueva rama (branch):
Cuando trabajas en equipo, generalmente se recomienda trabajar en ramas para no afectar la rama principal (main). Para crear una nueva rama y cambiarte a ella:

```git checkout -b nombre-de-la-rama```

Después, puedes hacer commits en esta nueva rama sin afectar el trabajo en main.

```git checkout -b nueva-rama```

Crea una nueva rama y te cambia a ella.

--- 

## 10. Cambiar entre ramas:
Si ya has creado varias ramas y quieres cambiarte a una de ellas, usa:

```git checkout nombre-de-la-rama```

--- 

## 11. Fusionar (merge) una rama:
Cuando terminas de trabajar en una rama y quieres fusionarla con la rama principal (generalmente main o master), puedes usar:

```
git checkout main  # Cambias a la rama principal
git merge nombre-de-la-rama
```
Este comando fusionará los cambios de nombre-de-la-rama en main.

---

## 12. Eliminar una rama:
Una vez que una rama ha sido fusionada y ya no la necesitas, puedes eliminarla localmente con:

```git branch -d nombre-de-la-rama```

Si la rama aún no ha sido fusionada y estás seguro de que deseas eliminarla, usa -D en lugar de -d.

## 13. Eliminar archivos no rastreados

Elimina archivos y directorios que están en el repositorio local pero que no han sido agregados al staging con git add.

```git clean```

También elimina archivos están listados en el archivo .gitignore pero no están siendo rastreados por Git.

## 14. Mostrar el historial de los cambios de referencia

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

## 15. Vaciar repositorio local

Elimina todos los archivos excepto el .git

```find . -not -path './.git*' -exec rm -rf {} +```


- [Volver al índice](#índice)

---
---
---

# Crear un repositorio

## 1. Abrir el GitBash sobre la carpeta que se convertirá en el repositorio local o crearlo y navegar hasta este:

```
cd /c/Users/TuUsuario/Documents/GitHub <-- El bash quiere la URL en inglés
mkdir mi-repositorio
cd mi-repositorio

```

## 2. Inicializar el repositorio local:

```git init```

## 3. Enlazar con el repositorio remoto:

```git remote add origin https://github.com/TuUsuario/mi-repositorio.git```

Aquí, origin es el nombre del repositorio remoto, y main es la rama predeterminada (si usas master, usa master en vez de main).

```git remote -v```

Verifica las configuraciones remotas.

## 4. Acceder si no lo he hecho previamente

```
git config --global user.name "Tu Nombre"

git config user.email "email_de_github@...com"
```

## 5. Asegurar el nombre de la rama principal como main (opcional)
GitHub, a partir de 2020, decidió cambiar el nombre de la rama predeterminada de master a main en los nuevos repositorios. Por lo tanto, cuando creas un repositorio en GitHub, en vez de crear una rama master por defecto, se crea main.

Cuando clonas un repositorio de GitHub o trabajas en un repositorio local recién creado, es posible que aún estés trabajando en la rama master (si el repositorio tiene una rama predeterminada más antigua o si tú mismo usaste el nombre anterior).

```git branch -M main```

-M indica que el nombre de la rama se cambiará de manera forzada (si ya existe una rama con ese nombre, la reemplazará). En este caso, cambia el nombre de la rama actual (por defecto master) a main.

## 6. Volcar los archivos en el repositorio local (opcional)
- En caso de que haya un README.md o un LICENSE por ejemplo, para evitar conflictos

```git pull origin main --allow-unrelated-histories```

Como GitHub tiene un **commit inicial**, usarás el comando git pull con la opción **--allow-unrelated-histories** porque estás fusionando dos historiales de commits que no tienen relación entre sí (el historial local vacío y el historial remoto con un commit).


## 7. Añadir un README.md (opcional)
```
echo "# Mi Repositorio" > README.md

git add README.md

git add .

```

## 8. Hacer el primer commit

```git commit -m "Descripción del primer commit"```

## 9. Subir los cambios al repositorio remoto

```git push -u origin main```

**-u** establece la relación entre tu rama local main y la rama remota main.

**origin** es el nombre de tu repositorio remoto.

**main** es la rama principal (si usas master, usa master en lugar de main)


- [Volver al índice](#índice)

# Recuperar un archivo de una versión previa

## 1. Ver el historial de commits

Para encontrar el commit en el que el archivo aún existía, ejecuta:

```git log --oneline```

Este comando mostrará los commits anteriores con sus identificadores (hash) en una forma corta. Busca el commit en el que el archivo aún estaba presente. Si sabes aproximadamente cuándo fue, esto te ayudará a encontrarlo más rápido.

## 2. Ver el contenido del archivo en un commit anterior

Una vez tengas el hash del commit que contiene el archivo, puedes usar el siguiente comando para recuperar el archivo desde ese commit:

```git checkout <commit_hash> -- <ruta/del/archivo>```

Sustituye <commit_hash> por el hash del commit que encontraste y <ruta/del/archivo> por la ruta al archivo que quieres recuperar.

Por ejemplo, si el hash es abc123 y el archivo se llama index.html, el comando sería:

```git checkout abc123 -- index.html```

## 3. Verifica que el archivo se haya recuperado

Después de ejecutar el comando, el archivo aparecerá en tu directorio de trabajo, y ya estará listo para ser añadido nuevamente al repositorio si lo deseas.

## 4. Añadir el archivo de vuelta a Git (opcional)

Si quieres que el archivo vuelva a formar parte de tu repositorio, ejecuta los siguientes comandos:

```
git add <ruta/del/archivo>
git commit -m "Recuperado el archivo <nombre del archivo>"
git push
```

- [Volver al índice](#índice)

---
---
---

# Parámetros avanzados

## git commit

### -a o --all
La opción -a hace que Git agregue automáticamente todos los archivos modificados y rastreados (pero no los nuevos archivos no añadidos aún con git add) al área de preparación antes de hacer el commit. Esto ahorra tiempo si ya has modificado archivos pero olvidaste añadirlos manualmente con git add.

```git commit -a -m "Corregir errores en el código"```

Este comando hará un commit de todos los archivos modificados y previamente rastreados (sin necesidad de hacer git add antes).

### --amend
Si cometiste un error en tu último commit (por ejemplo, olvidaste añadir un archivo o cometiste un error tipográfico en el mensaje), puedes usar la opción --amend para modificar el commit anterior.

```git commit --amend -m "Actualizar mensaje del commit"```

Este comando abre una oportunidad para modificar el último commit, ya sea para cambiar el mensaje o incluir cambios adicionales. Ten en cuenta que esto reescribe el historial, por lo que debes tener cuidado al usarlo si ya has compartido el commit con otros colaboradores.

### --no-edit
Cuando usas git commit --amend para modificar el commit anterior y no quieres cambiar el mensaje, puedes usar --no-edit. Esto mantiene el mensaje original del commit.

```git commit --amend --no-edit```

Modifica el commit anterior, pero conserva el mensaje original.

### --date
Si necesitas establecer una fecha personalizada para un commit (por ejemplo, cuando estás trabajando en un repositorio y quieres que el commit aparezca como si se hubiera realizado en un día anterior), puedes usar --date para especificar la fecha.

```git commit --date="2025-02-01 15:00:00" -m "Commit con fecha personalizada"```

Crea el commit como si se hubiera realizado en la fecha y hora especificadas.

### --author
Si por alguna razón necesitas hacer un commit con un autor diferente (por ejemplo, si estás trabajando en el repositorio de otra persona o colaborando en un proyecto), puedes especificar un autor con la opción --author.

```git commit --author="Autor Ejemplo <autor@ejemplo.com>" -m "Commit de otro autor"```

### --verbose
Esta opción muestra más detalles sobre los cambios que se están realizando en el commit, como un resumen de los archivos que se modificaron.

```git commit --verbose -m "Explicar detalles del commit"```

### --dry-run
Esta opción te permite ver qué cambios se cometerían, pero sin hacer realmente el commit. Es útil para revisar qué se incluiría en el commit antes de ejecutarlo.

```git commit --dry-run -m "Ver qué cambios se cometen"```

Muestra los archivos que se incluirían en el commit, pero no hace ningún cambio real.

---

## git add

### -f
El -f le dice a Git que añada el archivo a pesar de que esté ignorado en el .gitignore.

```git add -f archivo.png```

---

## git rm

### -r --cached

Limpiar la caché del repositorio

```git rm -r --cached .```

## git clean

> NOTA: completar

git clean -n o git clean --dry-run: Simula la operación y te muestra qué archivos y directorios serían eliminados sin borrarlos realmente. Es una buena forma de verificar qué pasaría antes de ejecutar el comando de forma definitiva.

bash
Copiar
Editar
git clean -n
git clean -f o git clean --force: Elimina los archivos no rastreados. Este comando realmente eliminará los archivos, por lo que hay que tener cuidado al usarlo.

bash
Copiar
Editar
git clean -f
git clean -fd: Elimina tanto archivos no rastreados como directorios no rastreados.

bash
Copiar
Editar
git clean -fd
git clean -fx: Elimina archivos que están en el .gitignore además de los no rastreados.

bash
Copiar
Editar
git clean -fx

- [Volver al índice](#índice)

# Instrucciones avanzadas

## Habilitar a Git para que maneje rutas largas

```git config --global core.longpaths true```

- [Volver al índice](#índice)

## Forzar al repositorio local a ser exacto al remoto

```
git fetch origin
git reset --hard origin/main
```

- [Volver al índice](#índice)
---
---
---
