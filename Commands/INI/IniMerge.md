# IniMerge

Combina el contenido de dos archivos .ini.

## Sintaxis

```pebakery
IniMerge,<SrcFile>,<DestFile>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcFile | La ruta completa del archivo que contiene la nueva información. |
| DestFile | La ruta completa del archivo que se actualizará con la nueva información. |

## Observaciones

+ `SrcFile` nunca será modificado.
+ Si `DestFile` no existe se creará.
+ Solo se fusionarán los contenidos específicos .ini. Cualquier cosa que no sea un nombre [Sección] o parte de un par clave=valor será ignorada. Standard .ini recognized comments such as `; Comment` or `# Comment` as well as PEBakery style comments `// Comment` will likewise be ignored.

## Ejemplo

Supongamos que tenemos los siguientes archivos .ini.

C:\myFile1.ini:

```pebakery
[Variables]
// Aquí hay algunas variables
myvar1="Homes32"
myvar2="ChrisR"

[Interface]
pText1="Mostrar este texto:",1,1,10,8,106,18,8,Normal
pCheckbox1="¿Mostrar ventana?",1,3,10,32,278,18,False

[Interface-2]
pText1="Mostrar otro texto:",1,1,10,8,106,18,8,Normal
```

C:\myFile2.ini:

```pebakery
[Variables]
myvar1="Homes32"
myvar2="lancelot"

[Interface]
pText1="Escribe algo aquí:",1,1,10,8,106,18,8,Normal
pCheckbox1="¿Mostrar ventana?",1,3,10,32,278,18,False
```

En el siguiente ejemplo, el archivo `SrcFile` *C:\myFile1.ini* se fusionará en `DestFile` *C:\myFile2.ini*

```pebakery
IniMerge,C:\myFile1.ini,C:\myFile2.ini
```

El resultante archivo C:\myFile2.ini:

```pebakery
[Variables]
myvar1="Homes32"
myvar2="ChrisR"

[Interface]
pText1="Mostrar este texto:",1,1,10,8,106,18,8,Normal
pCheckbox1="¿Mostrar ventana?",1,3,10,32,278,18,False

[Interface-2]
pText1="Mostrar otro texto:",1,1,10,8,106,18,8,Normal
```

Como podemos ver, han sucedido varias cosas.

+ El comentario `// Here are some variables` no se fusionó porque no es un componente de archivo .ini válido.
+ La clave `myvar2` se actualizó con el valor del `SrcFile`.
+ La etiqueta para el elemento *pText1* fue cambiada.
+ La sección `Interface-2` no existía en el `DestFile` por lo que fue creada.
+ `myvar1` y `pCheckbox1` fueron idénticos en ambos archivos por lo que no fueron modificados.
