# guia-git-basica
Guía básica de **GIT**  

**git init** → Inicializa un repositorio local.  

Add y commit directamente  
El siguiente comando es un add y un commit directamente:  
![git commit -am fichero](https://raw.githubusercontent.com/KamiKeys/guia-git-basica/master/images/image1.png)  
Otro ejemplo:


Git add
git add nombre o git add * para todo → añadir que git lo controle. Añadir al index.

git status → para ver el estado.

El fichero .gitignore
dentro se pone lo que quieras que gitignore del proyecto, pero tienes que crearlo tu. Y pones dentro lo que quieras ignorar.


al hacer un commit SIEMPRE se pone un mini texto de hasta 50 caracteres para explicar el commit en cuestión y luego otro más extendido:


git log → ver detalles
git log -v → más desglosado
git log -p → ver más detalles
git config -l → ver información de la configuración de git
git status -s → Muestra información si en el add hay algo y luego en nuestro directorio de trabajo se ha añadido.
git status -v → Ver rama actual y trabajo sin add en esa rama.
git diff → Muestra lo que ya está añadido en add por lo nuevo de nuestro directorio de trabajo.

NOTA: Se puede añadir más de un repo remoto en una carpeta y al hacer el push, se elige dónde se va a subir con los alias. La cosa es que se puede tener enlazado con muchos repos.

Arreglar un commit:
git commit --amend → Elimina el último commit
git commit --amend -m ”comentario” → Sobreescribe del tirón el último commit


NOTA: git add *letras de algo por ejemplo (git add *cs → añade todo lo que termine en cs)
NOTA: En la carpeta .git existen los siguientes archivos(dentro de config se pueden ver datos como con el comando git config -l):
git reset HEAD clase2.cs → sirve para quitar un archivo.
git reflog → para ver todas las páginas y sha1.
git reset y las primeras letras de sha1 se vuelve a ese momento del pasado.
git reset --hard commit→ vuelve atrás y borra lo que estuviese delante. (Si hemos subido un push)
git reset --soft HEAD@{1}→ vuelve atrás el último comando (si todavía no hemos hecho push)
git checkout --nombreArchivo → para quitarlo de add o rm, antes del commit.
git rm → elimina archivo.
git rm --cached → Para quitar de la rama el archivo, pero sigue estando en el directorio.
git checkout sha1delcommit → volvemos a un commit anterior
git checkout -b <nombre rama> sh1 commit→ se hace una rama desde el commit indicado.


Repositorios Remotos



git init --bare → Inicializa como repositorio remoto.
git clone → Clona el repositorio.
git remote add origin enlace → añadir un directorio remoto.
git remote →  dice los archivos remotos.
git remote -v → da más detalles.
git remote remove nombreAlias → Borra la referencia.
git remote rename viejo nuevo → Cambia nombre de los alias
git fetch origin master →baja y ve si hay cambios en el repositorio remoto respecto al tuyo local.
git diff origin master → ver los nuevos cambios.
git merge origin master → guarda los nuevos cambios.
git pull = git fetch + git merge.

NOTA: para la resolución de conflictos en diferentes clases pues es muy fácil, se descarga lo del otro y luego añado lo mio. Si se toca de la misma clase hay que ponerse de acuerdo sobre qué dejar y qué quitar. Se hace un pull, se quita lo que queramos y lo subimos again.


2.6 Fundamentos de Git - Etiquetado

Como consejo podemos poner v1.2.4
Donde el primer dígito serían grandes y notables cambios como la interfaz gráfica o nuevas funciones. El segundo dígito arreglo de errores pero sobre todo nuevas pequeñas funcionalidades. Tercer dígito para arreglo de errores.

podemos hacer otro dígito: v1.2.4.Z
donde z sería para los beta tester, número impar (versión inestable) y número par (versión estable).

Tipos de etiquetas

Anotadas (recomendada) → Obliga a poner un mensaje. git tag -a v1.2.0 -m ‘mensaje’

Simple: → etiqueta rápidamente para seguir trabajando, sin documentar. git tag

Para ver a qué pertenece la etiqueta → git show nombreEtiqueta
Para mostrar las etiquetas → git show
Borrar etiqueta → git tag -d nombreEtiqueta

De forma predeterminada etiqueta el último commit. 
Para etiquetar antiguos sería →  git tag -a v0.0.1 -m 'Primera etiqueta' 13434ecf <--(algo del hash de ese commit)

Las etiquetas no se publican en los push. Tengo que hacer un push específico de la etiqueta o de todas. → git push origin v0.0.1 (en este caso es para una solo.)
Sube todas las etiquetas → git push origin --tags

git push -u origin master → guarda origin master para luego hacer más tarde el push son poner lo otro.

Firma electrónica
Ver nuestras claves → gpg --list-secret-keys --keyid-format LONG

Agregar una clave privada a git →  git config --global user.signingkey clave

git tag -s v0.0.3 -m 'Etiqueta firmada por mi' → -s para firmar cifrado.

Ramas
Ver en qué rama estamos → git branch, se marca con * en la que estoy
Crear una rama nueva → git branch nombreRama
Moverse entre ramas → git checkout nombreRama
Volver a Master → git checkout master
Ver ramas de colores → git log --graph
Borrar rama → git branch -d nombreRama


incorpora todos los commits a mi código master que estén en la rama que corrija el bug
git merge nombreRama

borrar rama → git branch -d nombreRama

Dejar lo que estás haciendo → git stash

me dice la rama en la que estoy
git branch

Crear rama y moverme a ella del tiron
git checkout -b nombreRama


Rebase

Es parecido a un merge, solo que un merge crea un commit solo para fusionar dos ramas.
Un rebase poda la rama y la pega delante de la master. No se crea un commit extra innecesario.

Desde la master se hace git rebase nombreRamaAAñadir 
Eso lo copia, por lo que luego se borra la rama que ya no sirve con git branch -d nombreRama


Stashing

Estás picando en tu trabajo y tu jefe te dice que tienes que hacer otra cosa YA.
Vuelca en una pila temporal todos los cambios hechos desde el último commit.

git stash

realizas el trabajo importante

vuelves a lo tuyo
git stash pop

es una pila, por eso el pop. Se puede hacer más stash y el pop te saca el último que entra. Para verlos todos utilizamos → git stash list
y con su código utilizamos git stash código

