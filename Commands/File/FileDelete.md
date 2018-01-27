# FileDelete (Eliminar archivo)

Elimina un archivo.

Se admiten comodines, lo que permite eliminar múltiples archivos a la vez.

## Syntax

```pebakery
FileDelete,<FilePath>,[NOWARN],[NOREC]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | Archivo o archivos para eliminar. Los comodines (*,?) están permitidos. |

### Flags (Indicadores)

Los indicadores se pueden especificar en cualquier orden.

| Flag | Descripción |
| --- | --- |
| NOWARN | **(Opcional)** No registrar una advertencia si los archivos no existen. |
| NOREC | **(Opcional)** Ignorar subdirectorios al eliminar archivos usando comodines. |

## Observaciones

Cuando se usan comodines, los archivos en subdirectorios también se eliminarán. Para evitar esto, use la flag `NOREC`.

**Las carpetas eliminadas se eliminan permanentemente y no se pueden recuperar de la papelera de reciclaje.**

## Relacionado

[DirDelete](./DirDelete.md), [FileCopy](./FileCopy.md), [PathMove](./PathMove.md)

## Ejemplos

Supongamos que un directorio `%SrcDir%` *C:\Temp* contiene estos archivos:

```pebakery
C:\Temp\
|--- AAA\
     |--- A.txt
|--- ABB\
     |--- B.ini
|--- ACC\
     |--- C.txt
     |--- D.txt
|--- AEE\
|--- Y.ini
|--- AZ.txt
```

### Ejemplo 1

`C:\Temp\AZ.txt` será borrado.

```pebakery
FileDelete,%SrcDir%\AZ.txt
```

Resultado

```pebakery
C:\Temp\
|--- AAA\
     |--- A.txt
|--- ABB\
     |--- B.ini
|--- ACC\
     |--- C.txt
     |--- D.txt
|--- AEE\
|--- Y.ini
```

### Ejemplo 2

Se eliminarán todos los archivos `.txt` en %SrcDir%, incluidos los ubicados en subdirectorios.

```pebakery
FileDelete,%SrcDir%\*.txt
```

Resultado

```pebakery
C:\Temp\
|--- AAA\
|--- ABB\
     |--- B.ini
|--- ACC\
|--- AEE\
|--- Y.ini
```

### Ejemplo 3

Todos los archivos `.ini` en %SrcDir% se eliminarán, ignorando cualquier archivo ubicado en los subdirectorios.

```pebakery
FileDelete,%SrcDir%\*.ini,NOREC
```

Resultado

```pebakery
C:\Temp\
|--- AAA\
     |--- A.txt
|--- ABB\
     |--- B.ini
|--- ACC\
     |--- C.txt
     |--- D.txt
|--- AEE\
|--- AZ.txt
```
