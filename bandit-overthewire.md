# OverTheWire: Bandit Writeups

## Nivel 0 -> 1
**Objetivo:** Obtener la contraseña para el siguiente nivel almacenada en el archivo `readme` en el directorio home.

**Procedimiento:**
1.  **Conexión:** Se estableció una sesión SSH inicial al servidor `bandit.labs.overthewire.org` en el puerto `2220` usando las credenciales por defecto (`bandit0`).
2.  **Reconocimiento de archivos:** Se utilizó el comando `ls` para listar los archivos disponibles en el directorio actual.
    * *Resultado:* Se identificó el archivo `readme`.
3.  **Extracción de datos:** Se ejecutó el comando `cat readme` para visualizar el contenido del archivo en la salida estándar (stdout).

**Comandos utilizados:**
* `ssh`: Para acceso remoto seguro.
* `ls`: Para listar el contenido del directorio.
* `cat`: Para concatenar y mostrar el contenido de archivos.

**Password Bandit1:** ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
## Nivel 1 -> 2
**Objetivo:** Localizar y leer la contraseña almacenada en un archivo cuyo nombre es un carácter especial (`-`).

**Procedimiento:**
1.  **Identificación:** Se utilizó `ls` para confirmar la existencia del archivo `-` en el directorio home.
2.  **Análisis del Problema:** En sistemas Linux, el carácter `-` es interpretado por la mayoría de comandos como un operador de opciones (flags). Ejecutar `cat -` resulta en un error de ejecución o una espera de entrada estándar (stdin).
3.  **Solución Técnica:** Se utilizó una **ruta relativa** (`./`) para referenciar el archivo. Al ejecutar `cat ./-`, se le indica explícitamente al sistema operativo que el guion es un nombre de archivo ubicado en el directorio actual y no un parámetro del comando.

**Comandos utilizados:**
* `cat ./-`: Lectura de archivo con nombre de carácter especial mediante ruta relativa.

**Password Bandit2:** 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
## Nivel 2 -> 3
**Objetivo:** Acceder a un archivo con un nombre complejo que incluye guiones iniciales/finales y espacios (`--spaces in this filename--`).

**Procedimiento:**
1.  **Validación Visual:** Se ejecutó `ls -la` para confirmar el nombre exacto del activo, identificando que contenía guiones decorativos que el comando `cat` interpreta como opciones.
2.  **Resolución de Conflicto:** Se utilizó una ruta relativa explícita (`./`) combinada con comillas dobles para encapsular el nombre. Esto evita que la shell interprete los caracteres `--` como el inicio de un parámetro de comando.
3.  **Comando Final:** `cat "./--spaces in this filename--"`

**Password Bandit3:** MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
## Nivel 3 -> 4
**Objetivo:** Localizar y leer un archivo oculto dentro de una estructura de directorios.

**Procedimiento:**
1.  **Exploración:** Se detectó el directorio `inhere`. Tras ingresar en él, un comando `ls` simple no mostró resultados.
2.  **Uso de Flags de Visibilidad:** Se ejecutó `ls -la` para listar todos los archivos, incluyendo los ocultos (dotfiles).
    * *Resultado:* Se identificó el archivo `...Hiding-From-You`.
3.  **Extracción:** Se utilizó el comando `cat` con comillas para manejar los puntos iniciales del nombre del archivo.

**Comandos utilizados:**
* `ls -la`: Listado detallado de archivos ocultos.
* `cat "...Hiding-From-You"`: Lectura de archivo oculto sin espacios.

**Password Bandit4:** 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
## Nivel 4 -> 5
**Objetivo:** Identificar y leer el único archivo con contenido legible para humanos (ASCII text) dentro de un directorio con múltiples archivos binarios.

**Procedimiento:**
1.  **Exploración:** Se ingresó al directorio `inhere`, donde se localizaron múltiples archivos con nombres que inician con guion (`-file00` a `-file09`).
2.  **Análisis de Tipos de Archivo:** Se utilizó el comando `file ./*` para inspeccionar la naturaleza de los datos de cada archivo sin abrirlos.
    * *Resultado:* Se determinó que `./-file07` es el único que contiene "ASCII text", mientras que los demás contienen "data" no legible.
3.  **Extracción:** Aplicando la lección de niveles anteriores, se utilizó `cat ./-file07` para leer el archivo usando una ruta relativa, evitando conflictos con el guion inicial.

**Comandos utilizados:**
* `file ./*`: Determina el tipo de contenido de todos los archivos en el directorio actual.
* `cat ./-file07`: Lectura del archivo de texto identificado.

**Password Bandit5:** 4oQYVPkxZOOE005pTW81FB8j8lxXGUQw
