# Introducción a Maven

## ¿Qué es Maven?

**Maven** es una herramienta de software para la gestión y construcción de proyectos Java. Tiene un modelo de configuración basado en XML.

Utiliza un **Project Object Model** (POM) para describir el proyecto de software a construir, sus dependencias de otros módulos y componentes externos, y el orden de construcción de los elementos o artefactos. Aunque provee objetivos (goals) predefinidos para realizar ciertas tareas, como la compilación del código (compile) y su empaquetado (package), está construido usando una arquitectura basada en plugins, lo que permiten extender su funcionalidad, bien utilizando plugins de terceros o desarrollando nuestros propios plugins.

El principal objetivo de Maven es permitir al desarrollador centrarse en programar y liberarlo de ciertas tareas mediante la automatización, gracias a:

- Hacer el proceso de construcción de software sencillo, liberando al desarrollador de ciertos detalles.
- Proveer un sistema de construcción uniforme, de modo que una vez el desarrollador ser familiarice con un proyecto Maven, sabrá como se construyen otros proyectos.
- Proveer de información de calidad sobre el proyecto, como puede ser un registro de cambios en el código, las dependencias utilizadas o informes sobre test unitarios.
- Promover mejores prácticas de desarrollo, mediante el propio ciclo de vida de Maven.

## Instalación de Maven

La instalación de Maven varía de un sistema operativo a otro. 

Para saber cómo instalar Maven puede consultar el apartado **Instalar Maven** en las siguientes guías:

- [Cómo preparar un entorno de desarrollo Java en GNU/Linux](https://dam-dad.github.io/entorno/desarrollo-java-linux/)
- [Cómo preparar un entorno de desarrollo Java en Mac OS X](https://dam-dad.github.io/entorno/desarrollo-java-macos/)
- [Cómo preparar un entorno de desarrollo Java en Windows](https://dam-dad.github.io/entorno/desarrollo-java-windows/)

Una vez instalado, ejecuta el siguiente comando en un terminal para conocer la versión de Maven disponible:
```bash
mvn -v
```
y mostrará algo similar a lo siguiente:
```bash
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: C:\ProgramData\chocolatey\lib\maven\apache-maven-3.6.3\bin\..
Java version: 11.0.8, vendor: AdoptOpenJDK, runtime: C:\Program Files\AdoptOpenJDK\jdk-11.0.8.10-hotspot
Default locale: es_ES, platform encoding: Cp1252
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```

## Creación de un proyecto Java

Para crear proyectos Java con Maven podemos usar los [arquetipos](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html), un sistema de plantillas.

El siguiente comando crea un proyecto Java sencillo:

```bash
mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart
```

En este caso, lo ejecutamos en modo interactivo, de modo que nos pedirá **groupId**, **artifactId**, **version** y el **package** para nuestro nuevo proyecto, tal y como se muestra a continuación:

```bash
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------< org.apache.maven:standalone-pom >-------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] >>> maven-archetype-plugin:3.2.0:generate (default-cli) > generate-sources @ standalone-pom >>>
[INFO]
[INFO] <<< maven-archetype-plugin:3.2.0:generate (default-cli) < generate-sources @ standalone-pom <<<
[INFO]
[INFO]
[INFO] --- maven-archetype-plugin:3.2.0:generate (default-cli) @ standalone-pom ---
[INFO] Generating project in Interactive mode
Define value for property 'groupId': dad.java
Define value for property 'artifactId': PruebaMaven
Define value for property 'version' 1.0-SNAPSHOT: :
Define value for property 'package' dad.java: :
Confirm properties configuration:
groupId: dad.java
artifactId: PruebaMaven
version: 1.0-SNAPSHOT
package: dad.java
 Y: :
[INFO] ----------------------------------------------------------------------------
[INFO] Using following parameters for creating project from Old (1.x) Archetype: maven-archetype-quickstart:1.0
[INFO] ----------------------------------------------------------------------------
[INFO] Parameter: basedir, Value: C:\Users\fvarrui\GitHub
[INFO] Parameter: package, Value: dad.java
[INFO] Parameter: groupId, Value: dad.java
[INFO] Parameter: artifactId, Value: PruebaMaven
[INFO] Parameter: packageName, Value: dad.java
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] project created from Old (1.x) Archetype in dir: C:\Users\fvarrui\GitHub\PruebaMaven
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  11.967 s
[INFO] Finished at: 2020-10-03T22:35:38+01:00
[INFO] ------------------------------------------------------------------------
```

Una vez termina, nos crea un proyecto de nombre **PruebaMaven** (que corresponde con el *artifactId*) con la siguiente estructura:

```bash
PruebaMaven
│   pom.xml
│
└───src
    ├───main
    │   └───java
    │       └───dad
    │           └───java
    │                   App.java
    │
    └───test
        └───java
            └───dad
                └───java
                        AppTest.java
```

## Configurar la versión Java y la codificación del código fuente

Para establecer la versión de Java utilizada para compilar nuestro código fuente, y la codificación en la que se encuentra, debemos añadir el siguiente fragmento al fichero de configuración de nuestro proyecto (**pom.xml**):

```xml
<properties>
	<maven.compiler.target>14</maven.compiler.target>
	<maven.compiler.source>14</maven.compiler.source>
	<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
</properties>
```

> En el ejemplo anterior se está usando Java 14 para compilar y UTF-8 como codificación.

## Compilar el proyecto

Para compilar el código fuente de nuestro proyecto debemos ejecutar el siguiente comando en la raíz del proyecto:

```bash
mvn compile
```

Mostrando una salida como la siguiente:

```bash
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------< dad.java:PruebaMaven >------------------------
[INFO] Building PruebaMaven 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ PruebaMaven ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory C:\Users\fvarrui\GitHub\PruebaMaven\src\main\resources
[INFO]
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ PruebaMaven ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to C:\Users\fvarrui\GitHub\PruebaMaven\target\classes
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.017 s
[INFO] Finished at: 2020-10-04T11:41:28+01:00
[INFO] ------------------------------------------------------------------------
```

Todos los ficheros generados por Maven (incluidos los **.class**) se guardan en el directorio **target**:

```bash
PruebaMaven
│   pom.xml
│
├───src
│   ├───main
│   │   └───java
│   │       └───dad
│   │           └───java
│   │                   App.java
│   │
│   └───test
│       └───java
│           └───dad
│               └───java
│                       AppTest.java
│
└───target
    ├───classes
    │   └───dad
    │       └───java
    │               App.class
    │
    ├───generated-sources
    │   └───annotations
    └───maven-status
        └───maven-compiler-plugin
            └───compile
                └───default-compile
                        createdFiles.lst
                        inputFiles.lst
```

## Convertir en un proyecto Eclipse

Para poder importar el proyecto en Eclipse, podemos importarlo como un proyecto Maven directamente, o convertirlo primero (creando los ficheros **.project** y **.classpath**). Para esto último debemos ejecutar el siguiente comando en la raíz del proyecto (donde está el fichero **pom.xml**):

```bash
mvn eclipse:eclipse
```

Mostrando una salida como la siguiente:

```bash
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------< dad.java:PruebaMaven >------------------------
[INFO] Building PruebaMaven 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] >>> maven-eclipse-plugin:2.10:eclipse (default-cli) > generate-resources @ PruebaMaven >>>
[INFO]
[INFO] <<< maven-eclipse-plugin:2.10:eclipse (default-cli) < generate-resources @ PruebaMaven <<<
[INFO]
[INFO]
[INFO] --- maven-eclipse-plugin:2.10:eclipse (default-cli) @ PruebaMaven ---
[INFO] Using Eclipse Workspace: null
[INFO] Adding default classpath container: org.eclipse.jdt.launching.JRE_CONTAINER
[INFO] Not writing settings - defaults suffice
[INFO] Wrote Eclipse project for "PruebaMaven" to C:\Users\fvarrui\GitHub\PruebaMaven.
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.903 s
[INFO] Finished at: 2020-10-04T11:42:51+01:00
[INFO] ------------------------------------------------------------------------
```

La estructura de nuestro proyecto quedaría entonces así:

```bash
PruebaMaven
│   .classpath
│   .project
│   pom.xml
│
└───src
    ├───main
    │   └───java
    │       └───dad
    │           └───java
    │                   App.java
    │
    └───test
        └───java
            └───dad
                └───java
                        AppTest.java
```

## Configurar el proyecto para su ejecución

Para poder ejecutar nuestro proyecto con Maven debemos indicar la clase principal del proyecto (clase con método `main`) del siguiente modo:

```xml
<properties>
	<exec.mainClass>dad.java.App</exec.mainClass>
</properties>
```

> Debemos indicar la ruta completa a la clase (paquete y nombre de la clase, separados por puntos, sin incluir ".class" ni ".java"). Esa clase debe tener un método `main`.

Y ejecutarlo con el siguiente comando:

```bash
mvn exec:java
```

El resultado en este caso sería el siguiente:

```bash
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------< dad.java:PruebaMaven >------------------------
[INFO] Building PruebaMaven 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- exec-maven-plugin:3.0.0:java (default-cli) @ PruebaMaven ---
Hello World!
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.671 s
[INFO] Finished at: 2020-10-04T11:40:35+01:00
[INFO] ------------------------------------------------------------------------
```