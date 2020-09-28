---
title: GIT
---

El control de versiones es un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo, de modo que puedas recuperar versiones específicas más adelante. Cualquier tipo de archivo puede ponerse bajo control de versiones.

Un sistema de control de versiones (Version Control System o VCS en inglés) te permite revertir archivos a un estado anterior, revertir el proyecto entero a un estado anterior, comparar cambios a lo largo del tiempo, ver quién modificó por última vez algo que puede estar causando un problema, quién introdujo un error y cuándo, y mucho más. Usar un VCS permite también que si algún archivo se daña o se pierde es posible recuperarlo fácilmente.

## Secciones principales de un proyecto Git

Un repositorio está formado por tres árboles o estados locales:

1. **Working dir (directorio de trabajo)**: contiene los ficheros con los que estamos trabajando.
2. **Staging area (área de cambios)**: zona intermedia donde registramos los ficheros modificados (staged), y los preparamos para la próxima confirmación (commit).
3. **Repository (repositorio Git):** donde se almacenan los cambios confirmados.

![Local Operations](imagenes/git-local-operations.png)

## Ciclo de vida de los ficheros 

Un fichero puede estar en cualquiera de los siguientes estados:

- **untracked (no indexado):** indica que el fichero no está en seguimiento; GIT no controla los cambios que se produzcan en el mismo (no forma parte del Índice del repositorio):
  - `git add <file>` para añadir el fichero al repositorio (de `untracked` a `unmodified`).
  - `git rm <file>` para quitar el fichero del repositorio (de `modified` a `untracked`)
- **unmodified o commited (confirmado):** fichero indexado que no ha sido modificado o cuyos cambios ya han sido confirmados.
- **modified (modificado):** fichero indexado que ha sido modificado.
  - `git add <file>` para preparar el fichero modificado (pasarlo al Stage) y que forme parte del próximo `commit`.
  - `git reset` para deshacer los cambios preparados en el Stage.
- **staged (preparado):** se ha preparado el fichero para que sus cambios formen parte del próximo `commit`. Cuando se haga el `commit` (se confirmen los cambios del Stage) el fichero pasará de nuevo a `unmodified`.

![File Status Lifecycle](imagenes/git-file-status-lifecycle.png)

## Cómo usar GIT desde la línea de comandos

### Instalar GIT

Podemos descargar GIT para Windows, GNU/Linux o Mac OS X desde el siguiente [enlace](https://git-scm.com/download).

### Configurar GIT por primera vez

Establecer nombre de usuario y correo electrónico:

```bash
git config --global user.name "tu nombre"
git config --global user.email "tu@email.es"
```

> En Windows, las credenciales de acceso al repositorio remoto se almacenan en el "Administrador de credenciales" del "Panel de control".

### Comprobar la configuración

Para reviar la configuración que tenemos establecida para GIT usamos el siguiente comando:

```bash
git config --list
```

Para consultar la configuración general para todo el sistema:

```bash
git config --system --list
```

Para consultar la configuración como usuario:

```bash
git config --global --list
```

Para consultar la configuración de un repositorio debemos situarnos dentro del mismo:

```bash
git config --local --list
```

### Acciones con GIT

![Fetch, Merge y Pull](imagenes/git-pull-fetch.png)



### Crear un repositorio

#### Repositorio nuevo

Para crea un repositorio GIT en el directorio donde nos encontramos ejecutamos el siguiente comando:

```bash
git init
```

Esto creará en el directorio actual el directorio `.git` con toda la información del repositorio local.

####Copiar un repositorio remoto

Para crear una copia local de un repositorio remoto (*clone*), nos situamos en el directorio donde queremos que se haga la copia y ejecutamos el siguiente comando:

```bash
git clone <url> [<directory>]
```

Donde:

* `url` es la dirección del repositorio remoto que queremos copiar.
* `directory` es el nombre del directorio local (opcional).

Por ejemplo:

```bash
git clone https://github.com/fvarrui/DAD
```

El comando anterior hace lo siguiente:

1. Crea el directorio `DAD`.
2. Inicializa el directorio `.git` en su interior.
3. Descarga toda la información de la última versión del repositorio.

Si queremos que se cree el directorio del repositorio local con otro nombre:

```bash
git clone git clone https://github.com/fvarrui/DAD miNuevoDAD
```

De forma que ahora el directorio para la copia local se llamará `miNuevoDAD` en vez de `DAD`.

### Añadir un fichero al repositorio (tracking)

Para añadir un nuevo fichero al índice (*Index* ó *Stage*) del repositorio ejecutamos el siguiente comando:

```bash
git add <file>
```

Donde:

* `file` es el fichero o directorio que queremos añadir al repositorio.

Por ejemplo, si queremos añadir un fichero `README.md` a nuestro repositorio:

```bash
git add README.md
```

### Comprobar el estado de los archivos

Para comprobar los cambios que hemos realizado en el proyecto ejecutamos el siguiente comando:

```bash
git status
```

### Ignorar archivos

Es posible que archivos que formen parte de nuestro proyecto no queremos que se formen parte del repositorio y que no se sincronicen con el repositorio remoto. 

Para ello creamos el fichero .gitignore en el directorio raíz de nuestro repositorio con una lista de los ficheros que queremos que GIT ignore.

Por ejemplo: fichero `.gitignore`

```
# ignora los archivos terminados en .a
*.a

# pero no lib.a, aun cuando había ignorado los archivos terminados en .a en la linea anterior
!lib.a

# ignora unicamente el archivo TODO de la raiz, no subdir/TODO
/TODO

# ignora todos los archivos del directorio build/
build/

# ignora doc/notes.txt, pero este no doc/server/arch.txt
doc/*.txt

# ignora todos los archivos .txt el directorio doc/
doc/**/*.txt
```

### Preparar cambios para una confirmación (staging)

Para añadir las modificaciones realizadas en el directorio de trabajo (*working directory*) y subdirectorios al Stage:

```bash
git add .
```

El directorio `.` hace referencia al directorio actual, por lo que se añadirán al *Stage* los cambios en eset directorio y subdirectorios.

### Confirmar los cambios (commit)

Para confirmar (*commit*) los cambios que hemos añadido al Stage:

```bash
git commit -m "<message>"
```

Donde

* `message` es el texto descriptivo que se asociará a la confirmación y con el que se etiquerarán los cambios relizados.

### Repositorios remotos

#### Añadir un repositorio remoto

Para añadir un repositorio remoto donde se almacenarán nuestros ficheros ejecutamos el siguiente comando:

```bash
git remote add <remotename> <url>
```

Donde:

* `remotename` es el nombre que daremos al repositorio remoto, por ejemplo `origin`
* `url` es la dirección del repositorio remoto, por ejemplo `https://github.com/fvarrui/DAD`.

Ejemplo:

```bash
git remote add origin https://github.com/fvarrui/DAD
```

#### Enviar los cambios a un repositorio remoto (push)

Para enviar los ambios que hemos confirmado en nuesro repositorio local a un repositorio remoto ejecutamos el siguiente comando:

```bash
git push <remotename> <remotebrach>
```

Donde:

* `remotename` es el nombre que hemos dado al repositorio remoto, por ejemplo `origin`.
* `remotebranch` es el nombre del branch, por ejemplo `master`.

Ejemplo:

```bash
git push origin master
```

#### Traer cambios desde un repositorio remoto (fetch)

Para traer al Stage los cambios realizados por otras personas desde el repositorio remoto:

```bash
git fetch <remotename>
```

Donde:

- `remotename` es el nombre del repositorio remoto, por ejemplo `origin`


#### Combinar los cambios (merge)

Para combinar los cambios locales con los realizados por tras personas:

```bash
git merge <remotename> <branchname>
```

#### Traer cambios y combinarlos (pull)

Para traer los cambios realizados por otrs personas en el repositorio remoto y combinar los cambios con los cambios locales ejecutamos el comando:

```bash
git pull <remotename> <branchname>
```

> Es equivalente a hacer un `fetch` y un `merge`.

## Referencias

* [Pro Git ebook](https://git-scm.com/book/es/v2/)
* [GitHub: Managing remotes](https://help.github.com/categories/managing-remotes/)



