# DirDelete (Eliminar directorio)

Elimina un directorio y todos los archivos y subdirectorios que contiene.

## Sintaxis

```pebakery
DirDelete,<DirPath>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DirPath | Ruta completa del directorio para eliminar. |

## Observaciones

**Las carpetas eliminadas se eliminan permanentemente y no se pueden recuperar de la papelera de reciclaje.**

## Relacionado

[FileDelete](./FileDelete)

## Ejemplos

### Ejemplo 1

```pebakery
// C:\Temp será eliminado.
DirDelete,C:\Temp
```
