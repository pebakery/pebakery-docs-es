# IniWrite

Escribe un valor en un archivo .ini estándar.

## Sintaxis

```pebakery
IniWrite,<FileName>,<Section>,<Key>,<Value>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| Section | La sección donde se escribirá el valor. |
| Key | La clave que contendrá el valor.|
| Value | El valor para escribir.|

## Observaciones

Si `FileName` no existe, se creará.

PEBakery optimizará múltiples comandos `IniWrite` en una fila para un solo comando de escritura.

## Ejemplo 1

Supongamos que tenemos el siguiente archivo .ini:

```pebakery
// C:\myFile.ini
[mySection]
myKey=myValue
anotherKey=anotherValue
```

En el siguiente ejemplo, el valor de `1234` se escribirá en la clave `myKey`.

```pebakery
IniWrite,C:\myFile.ini,mySection,myKey,1234
```

## Ejemplo 2

Un uso común de IniWrite es recuperar valores de la interfaz de script y escribirlos en un archivo de configuración de aplicaciones.

Lets assume we have a program that uses the following .ini file:

```pebakery
// C:\myConfig.ini
[Config]
ShowWindow=true
ShowText=MyString
```

Code

```pebakery
[Process]
// Almacenar el valor de una casilla de verificación en el archivo de configuración
IniWrite,C:\myConfig.ini,Config,ShowWindow,%pCheckbox1%

//Almacenar el valor de un cuadro de texto en el archivo de configuración
IniWrite,C:\myConfig.ini,Config,MyString,%pText1%

[Interface]
pText1="Mostrar este texto:",1,1,10,8,106,18,8,Normal
pCheckbox1="¿Mostrar ventana?",1,3,10,32,278,18,False
```
