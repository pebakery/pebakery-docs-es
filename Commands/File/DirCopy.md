# DirCopy (Copiar directorio)

Copia un directorio junto con todos los subdirectorios y archivos.

Se admiten comodines, lo que permite que se copien varios directorios a la vez.

## Sintaxis

```pebakery
DirCopy,<SrcDir>,<DestDir>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcDir | Ruta completa del directorio para copiar. Los comodines (*,?) Están permitidos. |
| DestDir | Ruta completa al directorio de destino. La estructura del directorio se creará si no existe. Si el directorio existe, se sobrescribirá. |

## Observaciones

Si `DestDir` es un archivo, DirCopy falla.

WinBuilder 082 tiene un error que indica que DirCopy funciona de manera similar a FileCopy cuando se usan comodines. Activar la opción de compatibilidad `Simular WinBuilder's *.* error en DirCopy` simula este error. Ver el Ejemplo 2 para más detalles.

## Relacionado

[DirMove](./DirMove.md),[DirDelete](./DirDelete.md), [FileCopy](./FileCopy.md), [PathMove](./PathMove.md)

## Ejemplos

Supongamos un directorio `%SrcDir%` que contiene estos archivos *C:\Temp\Src*:

```pebakery
C:\Temp\Src\
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

```pebakery
// Todo el %SrcDir% se copiará en %DestDir%.
DirCopy,%SrcDir%,%DestDir%
```

Resultado

```pebakery
C:\Temp\Dest\
|--- Src\
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

### Ejemplo 2

```pebakery
// Todos los archivos de %SrcDir% serán copiado en %DestDir%.
DirCopy,%SrcDir%\A*,%DestDir%
```

Resultado

```pebakery
C:\Temp\Dest\
|--- AAA\
     |--- A.txt
|--- ABB\
     |--- B.ini
|--- ACC\
     |--- C.txt
     |--- D.txt
|--- AEE\
```

**Resultado al usar la opción de compatibilidad para Simular WinBuilder *.* error en DirCopy**

```pebakery
C:\Temp\Dest\
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
