# Exit (Salir)

Obliga a la secuencia de comandos actual a finalizar y continúa el procesamiento con la siguiente secuencia de comandos.

## Sintaxis

```pebakery
Exit,<Message>[,NOWARN]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Message | Texto que se mostrará y escribirá en el registro citando el motivo de `Exit`. |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| NOWARN | **(Opcional)** Suprime el estado de Advertencia en el registro. |

## Observaciones

El comportamiento predeterminado es registrar la acción `Exit` como advertencia. Si este no es un evento crítico, puede anular este comportamiento con la flag `NOWARN`.

Si el script ha definido la directiva `System,OnScriptExit`, el comando se procesará antes de que salga el script. Esto le permite al desarrollador realizar más registros y tareas de limpieza según el motivo de `Exit`.

## Relacionado

[System,OnScriptExit](../System/OnScriptExit.md)

## Ejemplos

### Ejemplo 1

Detener el procesamiento del script actual y registrar una advertencia.

```pebakery
Exit,"No se puede continuar porque el archivo no se encontró."
```

### Ejemplo 2

Detener el procesamiento del script actual, pero no registrar una advertencia.

```pebakery
// No es necesario advertir al usuario ya que la acción está destinada a evitar un procesamiento posterior.
Exit,"La aplicación ya está configurada.",NOWARN
```
