# Sintaxis de los comandos de .script

Los proyectos y scripts de PEBakery se escriben utilizando un lenguaje de scripts adaptado para crear entornos de preinstalación (PE) de arranque.

El motor de scripts de PEBakery proporciona comandos nativos para tareas comunes como:

- copiar archivos y directorios
- descarga de archivos
- extracción de archivos (.zip, .7z, etc.)
- modificar secciones del Registro
- leer y escribir archivos de configuración
- manipulación de cadenas
- trabajar con archivos WIM

La funcionalidad avanzada incluye la capacidad de definir macros y ejecutar procesos externos, dándole un potencial virtualmente ilimitado para personalizar y extender una funcionalidad de scripts usando herramientas externas tales como el símbolo del sistema de Windows, PowerShell, AutoIt3 o aplicaciones independientes.

## Sintaxis

Los comandos de PEBakery consisten en una palabra clave seguida de uno o más parámetros separados por comas. Los comandos están organizados en "secciones" similares a un archivo _.ini_estándar.

## Comentarios

Los comentarios se pueden usar para proporcionar una explicación o anotación en el script para facilitar que otros desarrolladores entiendan lo que está haciendo el script. También se pueden usar para "comentar" líneas de código mientras se depura un script.

PEBakery admite los comentarios `//` de estilo de C ++, así como los comentarios de estilo _.ini_ utilizando los delimitadores hash `##` o punto y coma`;`. Cada comentario debe colocarse en su propia línea y comenzar con un delimitador de comentario admitido. Un comentario finaliza cuando se inicia una nueva línea. PEBakery no admite comentarios de "bloque" multilínea.

```texto
// Este es un comentario
## Esto también es un comentario
; ¡Este es otro comentario!
```

## Caracteres de escape

A veces, una coma, cita u otro carácter reservado puede necesitar ser utilizado dentro de una cadena o parámetro. En esta situación, el caracter debe ser "escapado".

| Secuencia de escape | Caracter |
| --- | --- |
| #$c | Coma (,) |
| #$p | Porcentaje (%) |
| #$q | Doble comillas (") |
| #$s | Espacio |
| #$t | Tabulación |
| #$x | Nueva línea (\r\n) |
| ##  | Marca Hash (#) |

La secuencia de escape `##` es especialmente importante para recordar si está realizando una operación como `IniWrite` o `RegWrite` que escribirá una cadena que contiene una marca `#` seguida de:

- la letra `a`, `r`, or `c`. - Estos tokens `#a` `#r` y `#c` son utilizados por PEBakery para devolver valores especiales cuando se ejecutan bucles u otras secciones dentro de un script.
- un número `#12345`. - `#<integer>` se interpretan como parámetros PEBakery.

Considera el siguiente ejemplo:

```pebakery
[Main]
Title=Escapes Ejemplo
Author=Homes32
Level=5

[Variables]

[Process]
Run,%ScriptFile%,Test

[Test]
RegHiveLoad,Tmp_System,%RegSystem%

// Resultado previsto: HKLM\Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394#609E&10483\Service
// Debido a que #609 se interpreta como un parámetro
// Resultado actual: HKLM\Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394E&10483\Service
RegWrite,HKLM,0x1,Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394#609E&10483,Service,sbp2port

// Use la forma de escape del carácter # `##`
// Resultado: HKLM\Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394#609E&10483\Service
RegWrite,HKLM,0x1,Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394##609E&10483,Service,sbp2port

RegHiveUnLoad,Tmp_System
```

## Espacio en blanco

Las cadenas que contengan espacios en blanco deben estar entre comillas dobles ("Cadena con espacios").

PEBakery ignora el espacio en blanco al principio y al final de las líneas, así como las líneas en blanco. Siempre que sea factible, se recomienda el uso de líneas en blanco para mantener su código organizado y legible.
