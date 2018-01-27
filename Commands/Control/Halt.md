# Halt (Detener)

Obliga a la construcción actual a terminar.

## Sintaxis

```pebakery
Halt,<Message>
```

### Argumentso

| Argumento | Descripción |
| --- | --- |
| Message | Texto que se mostrará y escribirá en el registro citando el motivo del `Halt`. |

## Observaciones

Si el proyecto ha definido la directiva `System, OnBuildExit`, el comando se procesará antes de que se detenga la compilación. Esto le permite al desarrollador limpiar cualquier archivo temporal y/o puntos de montaje, y descargar cualquier sección de registro.

## Relacionado

[System,OnBuildExit](../System/OnBuildExit.md)

## Ejemplos

### Ejemplo 1

Abortar la compilación actual.

```pebakery
Halt,"Fuente incompatible. Seleccione una fuente válida e intente construir nuevamente."
```
