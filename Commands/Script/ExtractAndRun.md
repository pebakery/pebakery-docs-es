# ExtractAndRun

Extrae un solo archivo desde dentro de un script y lo ejecuta.

## Sintaxis

```pebakery
ExtractAndRun,<ScriptFile>,<DirName>,<FileName>[,Parameters]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ScriptFile | La ruta completa al script **Sugerencia:** Use `%ScriptFile%` para hacer referencia al script actual. |
| DirName | La carpeta dentro del script que contiene el archivo. |
| FileName | El nombre del archivo para extraer y ejecutar. |
| Parameters | **(Opcional)** Parámetros para pasar al ejecutable. Los parámetros no deben contener espacios, comillas o comas. Utilice la forma de escape de estos caracteres (es decir, #$s, #$q, #$c) si es necesario. |

## Observaciones

`FileName` se extrae a un subdirectorio nombrado al azar bajo el directorio %TEMP% definido por el sistema operativo (generalmente *C:\Users\username\AppData\Local\Temp*) y se borra cuando finaliza la ejecución.

`FileName` se ejecuta en primer plano y bloquea la acción posterior del script hasta que el proceso finaliza. Si necesita más control sobre la ejecución del proceso, use los comandos **ExtractFile** y **ShellExecute/ShellExecuteDelete** en su lugar.

## Relacionado

[Encode](./Encode.md), [ExtractAllFiles](./ExtractAllFiles.md), [ExtractFile](./ExtractFile.md)

## Ejemplos

### Ejemplo 1

Estructura de directorio simple dentro de un script.

```pebakery
root/
|--- Folder/
     |--- myApp.exe
     |--- myApp.ini
     |--- mySelfExtractingSFX.exe
|--- Reg/
     |--- mySettings.reg
|--- Help/
     |---readme.txt
|--- src/
     |---mySrc.au3
```

Extraer readme.txt y abrir con el programa predeterminado .txt.

```pebakery
ExtractAndRun,%ScriptFile%,Help,readme.txt
```

### Ejemplo 2

Extraer mySelfExtractingSFX.exe y ejecutar con el parámetro */silent /dir="C:\Tools"*.

```pebakery
ExtractAndRun,%ScriptFile%,Folder,mySelfExtractingSFX.exe,"/silent#$s/dir=C:\Tools"
```

### Ejemplo 3

El siguiente método es una alternativa más flexible al comando ExtractAndRun.

```pebakery
[main]
Title=ExtractAndRun Alternativa
Description=Demostrar cómo replicar el comportamiento del comando ExtractAndRun.
Level=5
Version=1
Author=Homes32

// Definir nuestro Marco
[Variables]
ExtractAndRunEx=Run,%ScriptFile%,ExtractAndRunEx,#1,#2,#3,#4,#5

[process]
ExtractAndRunEx,%ScriptFile%,Folder,myApp.exe

[ExtractAndRunEx]
// Sintaxis: ExtractAndRunEx,<Action>,<ScriptFile>,<DirName>,<FileName>,[,<Parameters>]
// #1 = Action (Open/Hide)  #2 = ScriptFile  #3 = DirName  #4 = FileName  #5 = Parameters
ExtractFile,#2,#3,#4,%ProjectTemp%\
ShellExecuteDelete,#1,%ProjectTemp%\#4,#5,%ProjectTemp%
```
