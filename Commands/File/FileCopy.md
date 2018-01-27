# FileCopy (Copiar archivo)

Copiar uno o más archivos.

Se admiten comodines, lo que permite que se copien varios archivos a la vez.

## Sintaxis

```pebakery
FileCopy,<SrcFile>,<DestPath>,[PRESERVE],[NOWARN],[NOREC]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcFile | Archivo (s) para copiar. Los comodines (*,?) Están permitidos. |
| DestPath | Ruta de destino. Puede ser un nombre de archivo o un directorio si se van a copiar varios archivos. La estructura del directorio se creará si no existe. |

### Flags (Indicadores)

Los indicadores se pueden especificar en cualquier orden.

| Flag | Descripción |
| --- | --- |
| PRESERVE | **(Opcional)** No sobrescribir los archivos existentes. |
| NOWARN | **(Opcional)** No registrar una advertencia si se sobrescribe un archivo. |
| NOREC | **(Opcional)** No copie archivos en subdirectorios cuando use comodines. |

## Observaciones

Cuando se utiliza comodín en nombre de archivo, `FileCopy` copia subdirectorios de forma predeterminada. Para evitar esto, use la bandera `NOREC`. Los comodines no pueden usarse en directorios.

## Relacionado

[DirCopy](./DirCopy.md), [DirCreate](./DirCreate.md), [FileDelete](./FileDelete.md), [FileMove](./FileMove.md), [PathMove](./PathMove.md)

## Ejemplos

Supongamos que un directorio `%SrcDir%` *C:\Temp\Src* contiene estos archivos:

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

`C:\Temp\AZ.txt` will be copied into %DestDir% `C:\Temp\myFolder\`

```pebakery
FileCopy,%SrcDir%\AZ.txt,%DestDir%
```

Resultado

```pebakery
C:\Temp\myFolder\
|--- AZ.txt
```

### Ejemplo 2

`C:\Temp\AZ.txt` será copiado en %DestDir%\ `C:\Temp\myFolder\` y renombrado `B.txt`

```pebakery
FileCopy,%SrcDir%\AZ.txt,%DestDir%\B.txt
```

Resultado

```pebakery
C:\Temp\myFolder\
|--- B.txt
```

### Ejemplo 3

Todos los archivos `.txt` en %SrcDir% se copiarán en %DestDir%.

```pebakery
FileCopy,%SrcDir%\*.txt,%DestDir%
```

Resultado

```pebakery
C:\Temp\myFolder\
|--- AAA\
     |--- A.txt
|--- ACC\
     |--- C.txt
     |--- D.txt
|--- AZ.txt
```

### Ejemplo 4

Todos los archivos `.txt` en %SrcDir% se copiarán en %DestDir%, ignorando subdirectorios.
```pebakery
FileCopy,%SrcDir%\*.txt,%DestDir%,NOREC
```

Resultado

```pebakery
C:\Temp\myFolder\
|--- AZ.txt
```
