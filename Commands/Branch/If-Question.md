# If,Question

Muestra un diálogo que le hace una pregunta al usuario y luego usa su respuesta para determinar si el comando debe ejecutarse.

## Sintaxis

```pebakery
If,QUESTION,<Question>,<Command>
```

```pebakery
If,QUESTION,<Question>,<Timeout>,<DefaultAnswer>
```

### Argumentos

#### Version 1

| Argumento | Descripción |
| --- | --- |
| Question | El texto que se mostrará al usuario. |
| Command | El comando que se ejecutará si el usuario elige `Si` (`Yes`). |

#### Version 2

| Argumento | Descripción |
| --- | --- |
| Question | El texto que se mostrará al usuario. |
| Command | El comando que se ejecutará si el usuario elige `Si` (`Yes`). |
| Timeout | Tiempo en segundos antes de que se seleccione `DefaultAnswer`. |
| DefaultAnswer | La respuesta que se seleccionará automáticamente después de que caduque el período `Timeout`.
|| Yes<br/>True - El `Comando` se ejecuta. |
|| No<br/>False - El `Comando` no se ejecuta. |

## Observaciones

Las preguntas bloquean el procesamiento posterior hasta que se responda la pregunta. A menos que la situación requiera la intervención del usuario, se recomienda establecer un período de tiempo de espera razonable con una respuesta predeterminada.

## Relacionado

[If](./If.md), [If-Else](./If-Else.md)

## Ejemplos

### Ejemplo 1

Haga una pregunta sin usar una respuesta de tiempo de espera/predeterminado.

```pebakery
[main]
Title=If-Question Ejemplo
Description=Mostrar el uso del comando If,Question.
Level=5
Version=1
Author=Homes32

[variables]

[process]
// Ejecute un solo comando si el usuario elige SÍ
If,QUESTION,"¿Te gustan los huevos verdes y el jamón?",Message,"Usted respondió SÍ."

// Ejecute otra sección si el usuario elige SÍ
If,QUESTION,"¿Te gustaría ejecutar otra sección?",Run,%ScriptFile%,Run-Yes

// También podemos usar instrucciones Block para ejecutar comandos adicionales
// o usar una condición Else para realizar otra acción cuando el usuario elija No.
If,QUESTION,"¿Estás seguro de que quieres continuar?",Begin
  Message,"El procesamiento continuará..."
End
Else,Begin
  Message,"El procesamiento se detendrá."
  Exit,"El usuario solicitó detener."
End

[Run-Yes]
Message,"Ejecutando otra sección..."
```

### Ejemplo 2

Haga una pregunta y defina un tiempo de espera de 10 segundos antes de elegir la respuesta predeterminada.

```pebakery
[main]
Title=If-Question Ejemplo
Description=Mostrar el uso del comando If,Question.
Level=5
Version=1
Author=Homes32

[variables]

[process]
// Ejecutar un solo comando si el usuario elige SÍ
// Elijir SÍ como la respuesta predeterminada después de 10 segundos
If,QUESTION,"¿Te gustan los huevos verdes y el jamón?",10,Yes,Message,"Usted respondió SÍ."

// Ejecutar otra sección si el usuario elige SÍ
// Elegir SÍ como la respuesta predeterminada después de 10 segundos
If,QUESTION,"¿Te gustaría ejecutar otra sección?",10,No,Run,%ScriptFile%,Run-Yes

// También podemos usar instrucciones Block para ejecutar comandos adicionales
// o usar una condición Else para realizar otra acción cuando el usuario elija No.
// Elijir SÍ como la respuesta predeterminada después de 10 segundos
If,QUESTION,"¿Estás seguro de que quieres continuar?",10,Yes,Begin
  Message,"El procesamiento continuará..."
End
Else,Begin
  Message,"El procesamiento se detendrá."
  Exit,"El usuario solicitó detener."
End

[Run-Yes]
Message,"Ejecutando otra sección..."
```
