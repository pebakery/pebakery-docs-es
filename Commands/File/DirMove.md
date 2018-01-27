# DirMove (Mover directorio)

Mueve un directorio.

## Sintaxis

```pebakery
DirMove,<SrcDir>,<DestPath>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcDir | Ruta completa del directorio para moverse. |
| DestPath | Ruta completa del directorio de destino. La estructura del directorio se creará si no existe. Todos los archivos existentes serán sobrescritos. |

## Observaciones

WinBuilder 082 permite a DirMove mover archivos. Al activar la opción de compatibilidad `FileRename y DirMove funcionan como PathMove` haciendo que el comando` DirMove` sea idéntico a `PathMove`.

## Relacionado

[DirCopy](./DirCopy), [DirDelete](./DirDelete), [PathMove](./PathMove.md)

## Ejemplos

### Ejemplo 1

```pebakery
DirMove,%SrcDir%\A,%DestDir%
```
