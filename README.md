# GUÍA BÁSICA DE GIT  
[![GitHub release](https://img.shields.io/github/release/KamiKeys/guia-git-basica.svg)]()
[![GitHub last commit](https://img.shields.io/github/last-commit/KamiKeys/guia-git-basica.svg)]()
[![GitHub issues](https://img.shields.io/github/issues/KamiKeys/guia-git-basica.svg)]()
[![GitHub stars](https://img.shields.io/github/stars/KamiKeys/guia-git-basica.svg)]()
[![GitHub forks](https://img.shields.io/github/forks/KamiKeys/guia-git-basica.svg)](https://github.com/KamiKeys/guia-git-basica/network)
[![GitHub license](https://img.shields.io/github/license/KamiKeys/guia-git-basica.svg)](https://github.com/KamiKeys/guia-git-basica/blob/master/LICENSE)  

## Índice    
1. [Introducción](#id1)
2. [Primeros Pasos](#id2)
3. [Repositorios Remotos](#id3)
4. [Etiquetado](#id4)
5. [Firma Electrónica](#id5)
6. [Ramas](#id6)
7. [Rebase](#id7)
8. [Stashing](#id8)

<br/>

## Introducción<a name="id1"></a>  
Bienvenid@ a una pequeña guía sobre comandos de Git. Aquí no vas a encontrar una extensa "guía de vuelo" con la que te conviertas en todo un profesional, ya que no es la intención. Encontrarás comandos básicos que se usan a diario, y algunos que te pueden sacar de apuros en otros casos.  
Siéntete totalmente libre de participar, añadir o corregir en caso de que encuentres algún error.

<br/>

## Primeros Pasos<a name="id2"></a>  

Lo primero será indicar a git quienes somos, para que pueda indicar quién hizo cada cambio:  
`git config --global user.name "John Doe"` → Configuramos el nombre con el que se nos verá (No es el nombre de usuario).  
`git config --global user.email johndoe@example.com` → Configuramos el correo con el que podrán contactar con nosotros.  

Luego deberemos inicializar un repositorio de manera local, para poder trabajar bajo el control de Git.  
`git init` → Inicializa un repositorio local. 

También se puede hacer un `git init nombreProyecto` y automáticamente se crea la carpeta del proyecto.  

Una vez hemos inicializado el repositorio, deberemos añadir bajo seguimiento los archivos que añadamos o modifiquemos:  
`git add`, `git add nombre` o `git add *` para todo → añadir que git lo controle. Añadir al index.  

Para ver los cambios se utiliza:  
`git status`  

Una vez se añaden los ficheros o modificaciones y queremos que esos cambios queden marcados, se deberá hacer un commit:  
`git commit` → Aparecerá el editor de texto vim, para comentar qué se ha hecho, ya que es obligatorio.  
`git commit -m "" -m ""` → En este caso no aparece el editor, y ponemos el comentario dentro de las "". El primer `-m` es para un título y el segundo para la explicación detallada. Anque se puede poner solo un `-m`.  

Al hacer un commit SIEMPRE se pone un mini texto de hasta 50 caracteres para explicar el commit en cuestión y luego otro más extendido (opcional):  
![git commit -m "texto corto" -m "texto largo"](https://raw.githubusercontent.com/KamiKeys/guia-git-basica/master/images/image3.png) 

**Add y commit directamente**:  
El siguiente comando es un add y un commit directamente:  
![git commit -am fichero](https://raw.githubusercontent.com/KamiKeys/guia-git-basica/master/images/image4.png)  
Otro ejemplo:  
![git commit -am fichero](https://raw.githubusercontent.com/KamiKeys/guia-git-basica/master/images/image5.png)  

Esto solo funciona si antes hemos añadido el fichero bajo el control de versiones, no podemos hacer un `-am` nada más crearlo.  

**El fichero .gitignore**
Dentro se pone lo que quieras que git ignore del proyecto, pero tienes que crearlo tu (o crear el repositorio desde GitHub). Y pones dentro lo que quieras ignorar.  


`git log` → Ver detalles  
`git log -v` → Más desglosado  
`git log -p` → Ver más detalles  
`git config -l` → Ver información de la configuración de git  
`git status -s` → Muestra información si en el add hay algo y luego en nuestro directorio de trabajo se ha añadido.  
`git status -v` → Ver rama actual y trabajo sin add en esa rama.  
`git diff` → Muestra lo que ya está añadido en add por lo nuevo de nuestro directorio de trabajo.  

**Arreglar un commit:**  
`git commit --amend` → Elimina el último commit  
`git commit --amend -m ”comentario”` → Sobreescribe del tirón el último commit  
![git commit --amend -m "explicacion"](https://raw.githubusercontent.com/KamiKeys/guia-git-basica/master/images/image1.png)

**NOTA:** `git add *letras` de algo por ejemplo (`git add *cs` → añade todo lo que termine en cs)  
**NOTA:** En la carpeta `.git` existen los siguientes archivos(dentro de `config` se pueden ver datos como con el comando `git config -l`):  

![ls](https://raw.githubusercontent.com/KamiKeys/guia-git-basica/master/images/image6.png)  
`git reset HEAD clase2.cs` → Sirve para quitar un archivo.  
`git reflog` → Para ver todas las páginas y sha1.  
`git reset` y las primeras letras de **sha1** sin decir el modo, por defecto es --mixed.  
Se puede poner el sha1 para un commit específico, o poner `HEAD@{1}` para volver justo al anterior.  
`git reset --hard commit` → Vuelve atrás al sha1 del commit indicado y borra lo que estuviese delante.  
`git reset --mixed HEAD@{1}` → Vuelve atrás 1 commit, deshace el commit pero mantiene los cambios en los ficheros.  
`git reset --soft HEAD@{1}` → Vuelve atrás el puntero pero mantiene el commit y los cambios.  
`git checkout --nombreArchivo` → Para quitar ficheros de add o rm, antes del commit.  
`git rm` → Elimina archivo.  
`git rm --cached` → Para quitar de la rama el archivo, pero sigue estando en el directorio.  
`git checkout sha1delcommit` → Volvemos a un commit anterior  
`git checkout -b <nombre rama> sh1 commit` → Se hace una rama desde el commit indicado.  

<br/>

## Repositorios Remotos<a name="id3"></a>  

![git init --bare](https://raw.githubusercontent.com/KamiKeys/guia-git-basica/master/images/image7.png)

`git init --bare` → Inicializa como repositorio remoto.  
`git clone` → Clona el repositorio.  
`git remote add origin enlace` → Añadir un directorio remoto.  
`git remote` →  Dice los archivos remotos.  
`git remote -v` → Da más detalles.  
`git remote remove nombreAlias` → Borra la referencia.  
`git remote rename viejo nuevo` → Cambia nombre de los alias  
`git fetch origin master` → Baja y ve si hay cambios en el repositorio remoto respecto al tuyo local.  
`git diff origin/master` → Ver los nuevos cambios, que yo no tengo.  
 `git diff master origin/master` → Ver qué tengo yo y qué pasaría si integro lo nuevo.  
`git merge origin/master` → Integra los nuevos cambios.  
`git pull` = `git fetch` + `git merge`.  

**NOTA:** Para la resolución de conflictos en diferentes clases pues es muy fácil, se descarga lo del otro y luego añado lo mio. Si se toca de la misma clase hay que ponerse de acuerdo sobre qué dejar y qué quitar. Se hace un `pull`, se quita lo que queramos y lo subimos (`push`) again.  


**NOTA:** Se puede añadir más de un repositorio remoto en una carpeta y al hacer el push, se elige dónde se va a subir con los alias. La cosa es que se puede tener enlazado con muchos repositorios.  

<br/>

## Etiquetado<a name="id4"></a>

Como consejo podemos poner `v1.2.4`
Donde el primer dígito serían grandes y notables cambios como la interfaz gráfica o nuevas funciones. El segundo dígito arreglo de errores pero sobre todo nuevas pequeñas funcionalidades. Tercer dígito para arreglo de errores.

Podemos hacer otro dígito: `v1.2.4.Z`
donde z sería para los beta tester, número impar (versión inestable) y número par (versión estable).

**Tipos de etiquetas**

**Anotadas (recomendada)** → Obliga a poner un mensaje. `git tag -a v1.2.0 -m "mensaje"`

**Simple:** → Etiqueta rápidamente para seguir trabajando, sin documentar. `git tag`

**Para ver a qué pertenece la etiqueta** → `git show nombreEtiqueta`  
**Para mostrar las etiquetas** → `git show`  
**Borrar etiqueta** → `git tag -d nombreEtiqueta`  

De forma predeterminada etiqueta el último commit. 
**Para etiquetar antiguos sería** →  `git tag -a v0.0.1 -m 'Primera etiqueta' 13434ecf` <--(algo del hash de ese commit)    

**Las etiquetas no se publican en los push. Tengo que hacer un push específico de la etiqueta o de todas.** → `git push origin v0.0.1` (en este caso es para una solo.)  
**Sube todas las etiquetas** → `git push origin --tags`    

`git push -u origin master` → guarda `origin master` para luego hacer más tarde el push son poner lo otro.  

<br/>

## Firma Electrónica<a name="id5"></a>    
**Ver nuestras claves** → `gpg --list-secret-keys --keyid-format LONG`

**Agregar una clave privada a git** →  `git config --global user.signingkey clave`

`git tag -s v0.0.3 -m "Etiqueta firmada por mi"` → -s para firmar cifrado.

<br/>

## Ramas<a name="id6"></a>    
**Ver en qué rama estamos** → `git branch`, se marca con * en la que estoy  
**Crear una rama nueva** → `git branch nombreRama`  
**Crear una rama apuntando a un commit**  → `git checkout nombreRama sha1DelCommit`  
**Moverse entre ramas** → `git checkout nombreRama`  
**Crear rama y moverse a ella del tirón** → `git checkout -b nombreRama`  
**Volver a Master** → `git checkout master`  
**Ver ramas identificadas por colores** → `git log --graph`  
**Borrar rama** → `git branch -d nombreRama`  


**Incorpora todos los commits a mi código master que estén en la rama que corrija el bug** → `git merge nombreRama`    

**Borrar rama** → `git branch -d nombreRama`  
**Me dice la rama en la que estoy** → `git branch`  

<br/>

## Rebase<a name="id7"></a>  

Es parecido a un `merge`, solo que un `merge` crea un `commit` solo para fusionar dos ramas.
Un `rebase` poda la rama y la pega delante de la `master`. No se crea un `commit` extra innecesario.

Desde la `master` se hace `git rebase nombreRamaAAñadir` 
Eso lo copia, por lo que luego se borra la rama que ya no sirve con `git branch -d nombreRama`


<br/>

## Stashing<a name="id8"></a>

Estás picando en tu trabajo y tu jefe te dice que tienes que hacer otra cosa YA.
Vuelca en una pila temporal todos los cambios hechos desde el último `commit`.

`git stash`

realizas el trabajo importante...

y vuelves a lo tuyo:  
`git stash pop`

Es una pila, por eso el pop. Se puede hacer más `stash` y el `pop` te saca el último que entra.  
**Para verlos todos utilizamos** → `git stash list`  
**y con su código utilizamos** → `git stash código`
