# Operadores (Operators)

PEBakery admite la siguiente comparación y operadores lógicos.

## Operadores de comparación

Estos operadores se utilizan junto con el comando `If` para comparar valores. Si la prueba devuelve verdadero, se ejecuta un comando.

| Operador | Descripción |
| --- | --- |
| Equal<br/>== | Prueba si dos valores son iguales. p.ej. `If,%var%,==,5,<Command>` (verdadero si %Var% es igual a 5). Sin distinción de mayúsculas y minúsculas cuando se utiliza con cadenas. |
| EqualX | Prueba si dos cadenas son iguales. Distingue mayúsculas y minúsculas. Los valores izquierdo y derecho se convierten a cadenas si ya no son cadenas. Este operador solo debe usarse si las comparaciones de cadenas deben ser sensibles a mayúsculas y minúsculas. |
| != | Prueba si dos valores no son iguales. Insensible a mayúsculas y minúsculas cuando se usa con cadenas. Para hacer una comparación sensible a mayúsculas y minúsculas use `If,Not,%var1%,EqualX,%var2%, <Command>` |
| Smaller<br/>< | Prueba si el primer valor es menor que el segundo. |
| SmallerEqual<br/><= | Prueba si el primer valor es menor o igual que el segundo. |
| Bigger<br/>> | Prueba si el primer valor es mayor que el segundo. |
| BiggerEqual<br/>>= | Comprueba si el primer valor es mayor o igual que el segundo. |

## Pruebas condicionales

Estas pruebas se utilizan junto con el comando `If` para determinar si existe o no un archivo, directorio, sección de script, valor de registro, macro, variable o conexión de red. Si la prueba devuelve verdadero, entonces se ejecuta un comando. Según la prueba específica seleccionada, uno o más argumentos adicionales pueden ser necesarios.

| Prueba | Descripción |
| --- | --- |
| ExistFile | Verifica si existe un archivo. |
| ExistDir | Verifica si existe un directorio. |
| ExistSection | Verifica si existe una [Sección] dentro de un archivo. |
| ExistRegSubKey<br/>ExistRegSection | Comprueba si existe una clave dentro de una sección del registro. |
| ExistRegValue<br/>ExistRegKey | Comprueba si existe un valor dentro de una sección del registro. |
| ExistVar | Comprueba si una variable está definida. |
| ExistMacro | Verifica si se define una macro. |
| ExistRegMulti | Comprueba la existencia de una subcadena en un valor de cadena múltiple. |
| Online | Comprueba si la computadora tiene una conexión de red activa. |
| Ping | Comprueba si se puede llegar a un host remoto enviando una solicitud de eco ICMP a un host especificado. Devuelve verdadero si se recibe una respuesta de eco ICMP válida. *Nota: La presencia y configuración de proxies, equipos de traducción de direcciones de red (NAT) o firewalls pueden evitar que Ping tenga éxito.* |

## Operadores Lógicos

| Operador | Descripción |
| --- | --- |
| Not | Operación lógica No. |

## Observaciones

**Todas las pruebas pueden ser negativas prefijando el operador lógico `No` a la prueba condicional.**

## Relacionado

[If](./If.md), [If-Else](./If-Else.md), [If,Question](./If-Question.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Operadores
Description=Mostrar los operadores que PEBakery soporta.
Level=5
Version=1
Author=Homes32

[Variables]
%Value1%=1
%Value2%=2
%Value3%="Hello World!"
%Value4%="HeLlO wOrLd!"
myMacro=Message,"I'm A Macro!"

[process]
// Cambie los valores de las variables anteriores para ver resultados diferentes con los siguientes comandos.

// Sintaxis: If,<Value1>,Bigger,<Value2>,<Command>
If,%Value1%,Bigger,%Value2%,Message,"%Value1% is bigger then %Value2%"

// Sintaxis: If,<Value1>,BiggerEqual,<Value2>,<Command>
If,%Value1%,BiggerEqual,%Value2%,Message,"%Value1% is equal to or bigger then %Value2%"

// Sintaxis: If,<Value1>,Equal,<Value2>,<Command>
If,%Value1%,Equal,%Value2%,Message,"%Value1% is equal to %Value2%"

// Sintaxis: If,<Value1>,EqualX,<Value2>,<Command>
If,Not,%Value3%,EqualX,%Value4,Message,"%Value3%#$xis not equal to#$x%Value4%"

// FPara pruebas que no son iguales, podemos usar el operador != O negar el comando Igual.
// Sintaxis: If,<Value1>,!=,<Value2>,<Command>
If,%Value1%,!=,%Value2%,Message,"%Value1% is != to %Value2%"
// Sintaxis: If,Not,<Value1>Equal,<Value2>,<Command>
If,Not,%Value1%,Equal,%Value2%,Message,"%Value1% is not equal to %Value2%"

// Sintaxis: If,<Value1>,Smaller,<Value2>,<Command>
If,%Value2%,Smaller,%Value1%,Message,"%Value2% is smaller then %Value1%"

// Sintaxis: If,<Value1>,SmallerEqual,<Value2>,<Command>
If,%Value2%,SmallerEqual,%Value1%,Message,"%Value2% is equal to or smaller then %Value1%"

// Sintaxis: If,ExistDir,<DirPath>,<Command>
If,ExistDir,C:\Temp,Message,"C:\Temp Exists"

// Sintaxis: If,ExistFile,<FilePath>,<Command>
If,ExistFile,C:\Temp\myFile.txt,Message,"C:\Temp\myFile.txt Exists"

// Sintaxis: If,ExistMacro,<Macro>,<Command>
If,ExistMacro,myMacro,Message,"myMacro Exists!"

// Sintaxis: If,ExistRegValue,<HKey>,<KeyPath>,<ValueName>
If,ExistRegValue,HKLM,SOFTWARE\Microsoft\Windows NT\CurrentVersion,ProductName,Message,"Registry value exists"

// Sintaxis: If,ExistRegMulti,<HKey>,<KeyPath>,<ValueName>,<SubValue>,<Command>
If,ExistRegMulti,HKLM,System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,volsnap,Message,"volsnap exists in RegMulti UpperFilters"

// Sintaxis: If,ExistRegSubKey,<HKey>,<KeyPath>,<Command>
If,ExistRegSubKey,HKLM,SOFTWARE\Microsoft\Windows NT\CurrentVersion,Message,"Registry key exists"

// Sintaxis: If,ExistSection,<FileName>,<Section>,<Command>
If,ExistSection,%ScriptFile%,Process,Message,"Process section exists in %ScriptFile%"

// Sintaxis: If,ExistVar,<Variable>,<Command>
If,ExistVar,%Value1%,Message,"Variable: #$pValue1#$p Exists"

// Sintaxis: If,Online,<Command>
If,Online,Message,"Network Connection Found"

// Ping puede usar nombre IP o DNS.
// Sintaxis: If,Ping,<Dest>,<Command>
If,Ping,127.0.0.1,Message,"I can ping 127.0.0.1"
If,Ping,google.com,Message,"I can ping google.com"
```
