# System,SetLocal

Starts localization of variables within a script.

Localized variables contain a copy of their original value and any further modifications are isolated until a matching `System,EndLocal` command is encountered or the end of the current [Section] is reached.

## Syntax

```pebakery
System,SetLocal
```

### Arguments

This command has no arguments.

### Return Values

| Return Value | Description |
| --- | --- |
| #r | Cuando se llama `System,EndLocal` se descarta el contenido de las variables aisladas. El token `#r` no se ve afectado por las restricciones de `System,SetLocal` y puede usarse para devolver el valor de una variable aislada al proceso principal. `#r` es volátil, por lo que si necesita conservar el valor de retorno cópielo en una variable local. |

## Observaciones

Este comando está destinado a su uso en scripts de "biblioteca" que contienen colecciones de macros. Mantener variables únicas para muchas macros en una sola secuencia de comandos puede ser difícil porque las variables locales están en el alcance de todo el `ScriptFile%`. Al utilizar los comandos `System,SetLocal` y `System,EndLocal` para aislar variables en un ámbito más estrecho, puede asegurarse de que las variables de cada sección estén protegidas de modificaciones no deseadas.

## Relacionado

[System,EndLocal](./EndLocal.md)

## Examples

### Ejemplo 1

```pebakery
[Main]
Title=SetLocal/EndLocal Ejemplo
Author=Homes32
Description=Mostrar el uso del comando System,SetLocal y System,EndLocal.
Version=1
Level=5

[Interface]

[variables]

[process]
Set,%var%,"¡Este valor nunca debería cambiar!"
Run,%ScriptFile%,mySection
Echo,"Verifiquemos que nuestra var1 no cambió."
Echo,"Var1 = %var%"
Echo,"R = #r"

[mySection]
System,SETLOCAL
// Gracias a System,SETLOCAL podemos usar %var% en [miSección] sin cambiar el valor de %var% en nuestra sección [Process].
Echo,"Nuestra copia aislada de var1: %var%"
// ¡Vamos a cambiarlo!
Set,%var%,"¡Hola Mundo!"
Set,#r,%var%
System,ENDLOCAL
```
