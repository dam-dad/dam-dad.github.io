# Cómo preparar un entorno de desarrollo Java en Windows

A continuación se explica como preparar tu sistema Windows de forma rápida y sencilla para desarrollar en Java.

Las herramientas que vamos a necesitar son las siguientes:

- AdoptOpenJDK 14
- Eclipse for Java developers
- Maven
- Git
- GitHub Desktop
- Typora

## Instalar Chocolatey

Vamos a utilizar el gestor de paquetes **Chocolatey** para instalar todo lo necesario para preparar nuestro entorno de desarrollo.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

## Instalar el JDK

Instalamos el Java Development Kit (JDK), necesario para programar con Java. En este caso se va a instalar **AdoptOpenJDK**.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y adoptopenjdk14
```

> Si instalamos el paquete `adoptopenjdk` (sin concatenarle el número de versión de Java), se instalará la última versión disponible.

## Instalar Eclipse for Java developers

Instalamos la edición de Eclipse para desarrolladores Java (Eclipse for Java developers), versión 2019.12.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y eclipse-java-oxygen --version=2019.12
```

> Si obviamos la versión (`--version=2019.12`) en el comando anterior, se instalará la última versión de Eclipse disponible.

## Instalar Maven

Instalamos **Maven** que es una herramienta de construcción de proyectos (building tool) para Java.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y maven
```

## Instalar Git

Instalamos **Git** para disponer del comando `git` desde la línea de comandos.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y git
```

## Instalar GitHub Desktop

Instalamos **GitHub Desktop**, herramienta gráfica que facilita la gestión de repositorios Git publicados en GitHub.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y github-desktop
```

## Instalar Typora

**typora** es un editor de Markdown disponible para múltiples plataformas. Markdown es un formato de texto sencillo para elaborar documentación acerca de nuestros proyectos.

Para instalarlo, abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y typora
```

## Referencias

- [Installing Chocolatey](https://chocolatey.org/install).
- [Chocolatey packages gallery](https://chocolatey.org/packages).
- [Eclipse downloads page](https://www.eclipse.org/downloads/).
- [GitHub Desktop](https://desktop.github.com/).
- [Sitio web oficial de Git](https://git-scm.com/).
- [Typora](https://typora.io/).