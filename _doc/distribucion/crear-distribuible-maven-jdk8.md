# Crear un distribuible con Maven para Java 8

En este guía se explica el proceso para crear un ejecutable (.EXE) e intaladores de una aplicación Java para poder distribuirla.

## Entorno

El entorno en el que se han realizado las pruebas es el siguiente:

* **Windows 10 Enterprise**
* **Eclipse Oxygen.2 Release (4.7.2)**
* **Java JDK 1.8.0_144**

Para generar los instaladores en Windows es necesario disponer de las siguientes aplicaciones:

* [**Inno Setup**](http://www.jrsoftware.org/isdl.php): si queremos generar un asistente de instalación (EXE).
* [**WIX**](http://wixtoolset.org/): si queremos generar un instalador de tipo Microsoft Installer (MSI).

> Son complementarias, por lo que si disponemos de ambas, Maven generará ambos artefactos.

> Para que funcione WIX es necesario que su binario se encuentre en el PATH del sistema. 

Como ejemplo, se va a usar el siguiente proyecto:

![Proyecto HolaMundoFXML](crear-distribuible-maven-jdk8/proyecto-holamundofxml.png)

Es necesario que el proyecto sea de tipo Maven para poder usar [`javafx-maven-plugin`](https://github.com/javafx-maven-plugin/javafx-maven-plugin), que a su vez hace uso de la herramienta `javapackager` incluida en el JDK.

## Procedimiento 

Los pasos a seguir son los siguientes:

1. Añadir el siguiente fragmento al `pom.xml` del proyecto dentro de la etiqueta `plugins`:

    ```xml
    <plugin>
        <groupId>com.zenjava</groupId>
        <artifactId>javafx-maven-plugin</artifactId>
        <version>8.6.0</version>
        <configuration>
            <appName>HolaMundoFXML</appName>
            <mainClass>dad.holamundo.fxml.HolaMundoApp</mainClass>
            <vendor>Fran Vargas</vendor>
        </configuration>
        <executions>
            <execution>
                <id>create-jfxjar</id>
                <phase>package</phase>
                <goals>
                    <goal>build-jar</goal>
                </goals>
            </execution>
            <execution>
                <id>create-native</id>
                <phase>package</phase>
                <goals>
                    <goal>build-native</goal>
                </goals>
            </execution>
        </executions>
    </plugin>
    ```

    Donde:

    * `appName` es el nombre de la aplicación
    * `mainClass` es la ruta completa a la clase principal de la aplicación
    * `vendor` es el nombre del desarrollador de la aplicación

    > Existen más propiedades que podemos añadir a la etiqueta `configuration`. Destacar también que existe un generador de configuraciones disponible en el siguiente [enlace](http://javafx-maven-plugin.github.io/).

1. Ejecutar con Maven el objetivo `package` desde la opción del menú "Run" > "Run as" > "Maven build...".

    ![Maven Package Goal](crear-distribuible-maven-jdk8/maven-package-goal.png)

    > Es recomendable hacer un `clean` antes de `package`.

    Tras unos segundos, se generarán los siguientes artefactos en el directorio `target` de nuestro proyecto:

    ![Artefactos generados](crear-distribuible-maven-jdk8/artefactos-generados.png)

3. Distribuir la aplicación:

    Los artefactos necesarios para distribuir la aplicación se generan por defecto en `target/jfx`, organizados de la siguiente forma:

    * **Directorio `app`:** aquí se genera el JAR ejecutable (`HolaMundoFXML-jfx.jar`).

    * **Directorio `native`:** aquí se generan los distribuibles nativos (en este caso, para Windows).

Ahora sólo debemos distribuir el contenido del directorio `HolaMundoFXML`, o alguno de los instaladores generados (`HolaMundoFXML-1.0.exe` generado con **InnoSetup**, u `HolaMundoFXML-1.0.msi` generado con **Wix**) dentro de `native`.

> Destacar que cuando se instale la aplicación, se instalará en el equipo el mismo contenido que hay en el directorio `target/jfx/native/HolaMundoFXML`.

## Configuración del plugin

Para obtener una lista detallada de las opciones que podemos utilizar para configurar el plugin ejecutamos Maven con el objetivo  `jfx:help -Ddetail=true`.

![Maven jfx:help Goal](crear-distribuible-maven-jdk8/maven-jfx-help-goal.png)
