---
title: GIT
description: Sistema de control de versiones
---
# GIT

El control de versiones es un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo, de modo que puedas recuperar versiones específicas más adelante. Cualquier tipo de archivo puede ponerse bajo control de versiones.

Un sistema de control de versiones (Version Control System o VCS en inglés) te permite revertir archivos a un estado anterior, revertir el proyecto entero a un estado anterior, comparar cambios a lo largo del tiempo, ver quién modificó por última vez algo que puede estar causando un problema, quién introdujo un error y cuándo, y mucho más. Usar un VCS permite también que si algún archivo se daña o se pierde es posible recuperarlo fácilmente.

Podemos descargar GIT para Windows, GNU/Linux o Mac OS X desde el siguiente [enlace](https://git-scm.com/download).

## Secciones principales de un proyecto Git

Un repositorio está formado por tres árboles o estados locales:

1. **Working dir (directorio de trabajo)**: contiene los ficheros con los que estamos trabajando.
2. **Staging area (área de cambios)**: zona intermedia donde registramos los ficheros modificados (staged), y los preparamos para la próxima confirmación (commit).
3. **Repository (repositorio Git):** donde se almacenan los cambios confirmados.

![Local Operations](imagenes/git-local-operations.png)

## Ciclo de vida de los ficheros 

Un fichero puede estar en cualquiera de los siguientes estados:

- **untracked (no indexado):** indica que el fichero no está en seguimiento; GIT no controla los cambios que se produzcan en el mismo (no forma parte del Índice del repositorio):
  - `git add <fichero>` para añadir el fichero al repositorio (de `untracked` a `unmodified`).
  - `git rm <fichero>` para quitar el fichero del repositorio (de `modified` a `untracked`)
- **unmodified o commited (confirmado):** fichero indexado que no ha sido modificado o cuyos cambios ya han sido confirmados.
- **modified (modificado):** fichero indexado que ha sido modificado.
  - `git add <fichero>` para preparar el fichero modificado (pasarlo al Stage) y que forme parte del próximo `commit`.
  - `git reset` para deshacer los cambios preparados en el Stage.
- **staged (preparado):** se ha preparado el fichero para que sus cambios formen parte del próximo `commit`. Cuando se haga el `commit` (se confirmen los cambios del Stage) el fichero pasará de nuevo a `unmodified`.

![File Status Lifecycle](imagenes/git-file-status-lifecycle.png)

## Crear un repositorio nuevo

Para crea un repositorio GIT en el directorio donde nos encontramos ejecutamos el siguiente comando:

```bash
git init
```

## Crear una copia local de un repositorio remoto

Para crear una copia local de un repositorio remoto, nos situamos en el directorio donde queremos que se haga la copia y ejecutamos el siguiente comando:

```bash
git clone https://host/path/to/repository.git
```

Por ejemplo, para crear una copia de este mismo repositorio:

```bash
git clone https://github.com/fvarrui/DAD.git
```

## Añadir un fichero al repositorio

Para añadir un nuevo fichero al índice (Index ó Stage) del repositorio GIT, ejecutamos el siguiente comando:

```bash
git add <fichero>
```

Por ejemplo, si queremos añadir un fichero README.md a nuestro repositorio:

```bash
echo "#DAD" > README.md
git add README.md
```

