# PathMove (Mover ruta)

Mueve un archivo o directorio.

## Sintaxis

```pebakery
PathMove,<SrcPath>,<DestPath>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcPath | Ruta completa del archivo o directorio para mover. |
| DestPath | Ruta de destino. |

## Observaciones

Activando la opción de compatibilidad `FileRename y DirMove funcionan como PathMove` haciendo que FileRename y DirMove sean idénticos a PathMove.

## Relacionado

[DirMove](./DirMove.md), [FileRename](./FileRename.md)

## Ejemplos

### Ejemplo 1

`A.txt` será renombrado a `B.txt`.

```pebakery
PathMove,%SrcDir%\A.txt,%SrcDir%\B.txt
```

### Ejemplo 2

`%SrcDir%\A.txt` se moverá a `%DestDir%\B.txt`.

```pebakery
PathMove,%SrcDir%\A.txt,%DestDir%\B.txt
```

### Ejemplo 3

Si %DestDir% existe: `%SrcDir%\A` se moverá a `%DestDir%\A`.
Si %DestDir% no existe: `%SrcDir%\A` se moverá a `%DestDir%`.

```pebakery
PathMove,%SrcDir%\A,%DestDir%
```
