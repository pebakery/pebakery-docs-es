# ExtractAllFiles

Extrae todos los archivos del directorio especificado dentro de un script.

## Sintaxis

```pebakery
ExtractAllFiles,<ScriptFile>,<DirName>,<DestDir>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ScriptFile | La ruta completa al script **Sugerencia:** Use `%ScriptFile%` para hacer referencia al script actual. |
| DirName | La carpeta dentro del script que contiene los archivos. |
| DestDir | La ruta completa del directorio de destino. Si los archivos que se van a extraer ya existen, se sobrescribirán. |

## Observaciones

Ninguna.

## Relacionado

[Encode](./Encode.md), [ExtractFile](./ExtractFile.md)

## Ejemplos

### Ejemplo 1

Estructura de directorios simple dentro de un script.

```pebakery
root/
|--- Folder/
     |--- myApp.exe
     |--- myApp.ini
     |--- moreFiles.7z
|--- Reg/
     |--- mySettings.reg
|--- src/
     |---mySrc.au3
```

Extraer todos los archivos contenidos en el directorio *Folder* del script en ejecución a C:\Temp.

```pebakery
ExtractAllFiles,%ScriptFile%,Folder,C:\Temp
```
