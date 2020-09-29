# Entorno de desarrollo para Mac OS X

Esta guía explica cómo preparar un entorno de desarrollo Java en Mac OS X.

## Instalar el gestor de paquetes brew

El gestor de paquete **brew** facilita la instalación de software en un sistema Mac OS.

Para instalarlo abre un terminal y ejecuta el siguiente comando:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

> Durante el proceso de instalación se requiere intervención del usuario en algunos puntos.

## Instalar AdoptOpenJDK

Para instalar la última versión de **AdoptOpenJDK**, abre un terminal y ejecuta el siguiente comando:

```bash
brew cask install adoptopenjdk
```

> Si quieres instalar una versión diferente consulta el siguiente [enlace](https://github.com/AdoptOpenJDK/homebrew-openjdk).

## Instalar Maven

Para instalar la última versión de **Maven**, abre un terminal y ejecuta el siguiente comando:

```bash
brew install maven
```



## 