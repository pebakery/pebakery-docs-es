# FileRename (Renombrar archivo)

**Alias**: `FileMove`

Renombrar o mover un archivo.

## Sintaxis

```pebakery
FileRename,<SrcPath>,<DestPath>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcPath | Ruta completa del archivo para cambiar el nombre. |
| DestPath | Nueva ruta del archivo renombrado. |

## Observaciones

`FileRename` también se puede usar para mover un archivo.

WinBuilder 082 permite a `FileRename` mover un directorio. Al activar la opción de compatibilidad `FileRename y DirMove funcionan como PathMove`, hace a`FileRename` idéntico a `PathMove`.

## Relacionado

[FileCopy](./FileCopy.md), [PathMove](./PathMove.md)

## Ejemplos

### Ejemplo 1

`A.txt` será renombrado a `B.txt`.

```pebakery
FileRename,%SrcDir%\A.txt,%SrcDir%\B.txt
```

### Ejemplo 2

`%SrcDir%\A.txt` se moverá a `%DestDir%\B.txt`.

```pebakery
FileMove,%SrcDir%\A.txt,%DestDir%\B.txt
```
