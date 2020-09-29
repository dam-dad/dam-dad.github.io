# Primero pasos con GitHub

## Crear un nuevo repositorio desde la línea de comandos

1. Crear un repositorio GIT en el directorio actual:

    ```bash
    git init
    ```

2. Añadir todos los ficheros del repositorio al **stage**:

    ```bash
    git add .
    ```

3. Hacer un commit de todos los cambios añadidos al **stage**:

    ```bash
    git commit -m "first commit"
    ```

4. Vincular el repositorio local con un repositorio remoto de GitHub:

    ```bash
    git remote add origin https://github.com/usuario/repo.git
    ```

5. Si en el repositorio remoto hay algo, debemos traerlo primero (por ejemplo, si creamos el proyecto en GitHub incluyendo `README.md`, `.gitignore` o `LICENSE`):

    ```bash
    git pull origin master --allow-unrelated-histories
    ```
	> Si el proyecto remoto está vacío, este paso no es necesario:

6. Subir los cambios del repositorio local al remoto:

    ```bash
    git push -u origin master
    ```

## Publicar un repositorio existente desde la línea de comandos

1. Vincular el repositorio local con un repositorio remoto de GitHub:

    ```bash
    git remote add origin https://github.com/usuario/repo.git
    ```

2. Subir los cambios del repositorio local al remoto:

    ```bash
    git push -u origin master
    ```

## Publicar los cambios realizados

1. Añadir los cambios al **stage**:

    ```bash
    git add .
    ```
    > Los cambios pueden ser modificar un fichero, añadir un fichero nuevo, eliminar un fichero, etc.

2. Preparar el **commit** con los cambios que hemos añadido

    ```bash
    git commit -m "comentario"
    ```

3. Descargar los cambios del repositorio remoto antes de subir los nuestros:

    ```bash
    git pull
    ```
    > Si creemos que el repositorio remoto puede haber cambiado (porque trabajamos varias personas en equipo sobre el mismo repo), debemos hacer esto siempre antes del `push`.

4. Subir los cambios del repositorio local al remoto:

    ```bash
    git push
    ```
