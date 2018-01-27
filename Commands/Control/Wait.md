# Wait (Esperar)

Pausar la ejecución por una cantidad específica de tiempo.

## Sintaxis

```pebakery
Wait,<Seconds>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Seconds | Número de segundos para pausar antes de continuar con el procesamiento. |

## Observaciones

El comando `Wait` se puede utilizar para dar tiempo a otros programas para iniciar o finalizar la ejecución antes de que se lleve a cabo otra operación. Otro uso común es pausar el procesamiento durante unos segundos para permitir que el usuario reaccione a un evento, como un mensaje `Echo`.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
// Esperar 5 segundos y luego continúe.
Echo,"Esperando 5 segundos..."
Wait,5
```
