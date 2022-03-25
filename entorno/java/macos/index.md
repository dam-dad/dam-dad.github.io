# Cómo preparar un entorno de desarrollo Java en Mac OS X

Esta guía explica cómo preparar un entorno de desarrollo Java en Mac OS X desde la línea de comandos, lo que permite automatizar todo el proceso de configuración mediante un script.

Éste es el software que se va a instalar a continuación:

- OpenJDK
- Eclipse for Java developers
- Maven
- Git
- GitHub Desktop
- MarkText

## Instalar el gestor de paquetes SDKMAN!

El gestor de paquetes **SDKMAN!** facilita la instalación de software para desarrolladores en sistemas Mac OS y GNU/Linux (*nix).

Para instalarlo abre un terminal y ejecuta el siguiente comando:

```bash
curl -s "https://get.sdkman.io" | bash
```

> SDKMAN! instala el software sólo para el usuario que ejecuta el comando, por eso no es necesario ejecutar el comando anterior con privilegios elevados (`sudo`).

> Es necesario abrir un terminal nuevo para poder empezar a utilizar el comando `sdk`.

## Instalar el gestor de paquetes brew

El gestor de paquete **brew** facilita la instalación de software en un sistema Mac OS.

Para instalarlo abre un terminal y ejecuta el siguiente comando:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

> Durante el proceso de instalación se requiere intervención del usuario en algunos momentos.

## Instalar JDK

Para instalar la última versión **JDK**, abre un terminal y ejecuta el siguiente comando:

```bash
sdk install java
```

> Si quieres instalar una versión diferente consulta las versiones disponibles mediante el siguiente comando:
> 
> ```bash
> sdk list java
> ```

## Instalar Eclipse

Para instalar la última versión de **Eclipse for Java developers**, abre un terminal y ejecuta el siguiente comando:

```bash
brew cask install eclipse-java
```

## Instalar Maven

Para instalar la última versión de **Maven**, abre un terminal y ejecuta el siguiente comando:

```bash
sdk install maven
```

## Instalar Git

Mac OS X ya dispone de **git**, pero si queremos disponer de una versión más reciente ejecutamos el siguiente comando en un terminal:

```bash
brew install git
```

## Instalar GitHub Desktop

Descargar **GitHub Desktop** para Mac OS ejecutando el siguiente comando en un terminal:

```
curl -L -o GitHubDesktop.zip https://central.github.com/deployments/desktop/desktop/latest/darwin
```

Y extraemos el contenido del fichero ZIP descargado en `/Applications`:

```bash
unzip GitHubDesktop.zip -d /Applications
```

## Instalar Mark Text

Descargamos **Mark Text** ejecutando el siguiente comando en un terminal:

```bash
curl -L -O https://github.com/marktext/marktext/releases/latest/download/marktext.dmg
```

Abrimos la imagen DMG:

```bash
open ./marktext.dmg
```

Lo instalamos en **Applications**:

```bash
cp -R /Volumes/marktext/marktext.app /Applications
```

Desmontamos la imagen:

```bash
umount /Volumes/marktext
```

## Referencias

- [SDKMAN!](https://sdkman.io/)
- [Homebrew - the missing package manager for macOS (or Linux)](https://brew.sh/)