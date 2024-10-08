# Cómo preparar un entorno de desarrollo Java en Windows

A continuación se explica como preparar tu sistema Windows de forma rápida y sencilla para desarrollar en Java.

Las herramientas que vamos a necesitar son las siguientes:

- **JDK (Java Development Kit)**
- **JetBrains IntelliJ IDEA (Community Edition)** o **Eclipse for Java developers**
- **Maven**
- **Git**
- **GitHub Desktop**
- **MarkText**

## Instalar Chocolatey

Vamos a utilizar el gestor de paquetes **Chocolatey** para instalar todo lo necesario para preparar nuestro entorno de desarrollo.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

## Instalar el JDK

Instalamos el Java Development Kit (JDK), necesario para programar con Java. En este caso se va a instalar **Eclipse Temurin (JDK 21+)**.

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y temurin
```

> Esto instalará la última versión del OpenJDK [Temurin](https://adoptium.net/).

## Instalar JetBrains IntelliJ IDEA (Community Edition)

Instalamos la última versión de la edición Community de IntelliJ:

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y intellijidea-community
```

## Instalar Eclipse for Java developers

Instalamos la última versión de la edición de Eclipse para desarrolladores Java (Eclipse for Java developers).

Abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y eclipse-java-oxygen
```

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

## Instalar Mark Text

**Mark Text** es un editor de Markdown disponible para múltiples plataformas. Markdown es un formato de texto sencillo para elaborar documentación acerca de nuestros proyectos.

Para instalarlo, abre **PowerShell** como Administrador y ejecuta el siguiente comando:

```powershell
choco install -y marktext
```

## Referencias

- [Installing Chocolatey](https://chocolatey.org/install).
- [Chocolatey packages gallery](https://chocolatey.org/packages).
- [IntelliJ IDEA](https://www.jetbrains.com/idea/)
- [Eclipse downloads page](https://www.eclipse.org/downloads/).
- [GitHub Desktop](https://desktop.github.com/).
- [Sitio web oficial de Git](https://git-scm.com/).
- [MarkText](https://marktext.app/).