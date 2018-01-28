# ExtractFile

Extrae un solo archivo desde dentro de un script.

## Sintaxis

```pebakery
ExtractFile,<ScriptFile>,<DirName>,<FileName>,<DestDir>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ScriptFile | La ruta completa al script **Sugerencia:** Use `%ScriptFile%` para hacer referencia al script actual. |
| DirName | La carpeta dentro de la secuencia de comandos que contiene el archivo. |
| FileName | El nombre del archivo para extraer. |
| DestDir | La ruta completa del directorio de destino. Si `FileName` ya existe, se sobrescribirá. |

## Observaciones

Ninguna.

## Relacionado

[Encode](./Encode.md), [ExtractAllFiles](./ExtractAllFiles.md)

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

Extraer mySettings.reg del directorio *Reg* del script en ejecución.

```pebakery
ExtractFile,%ScriptFile%,Reg,mySettings.reg,c:\Temp
```
