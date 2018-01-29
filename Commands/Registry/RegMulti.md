# RegMulti

Modificar un valor de varias cadenas en el registro.

## Sintaxis

```pebakery
RegMulti,<HKey>,<KeyPath>,<ValueName>,<Action>,<Arg1>[,Arg2]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| HKEY | La clave raíz debe ser una de las siguientes: |
|| HKEY_LOCAL_MACHINE or HKLM |
|| HKEY_CURRENT_CONFIG or HKCC |
|| HKEY_CLASSES_ROOT or HKCR |
|| HKEY_CURRENT_USER or HKCU |
|| HKEY_USERS or HKU |
| KeyPath | La ruta completa de la clave de registro. |
| ValueName | El valor de varias cadenas para modificar. |
| Action | La acción debe ser una de las siguientes palabras clave: |
|| APPEND - Escribe una cadena al final del valor especificado. |
|| PREPEND - Escribe una cadena al comienzo del valor especificado. |
|| BEFORE - Escribe una cadena antes de la cadena de búsqueda coincidente. |
|| BEHIND - Escribe una cadena después de la cadena de búsqueda coincidente. |
|| PLACE - Escribe una cadena en el índice especificado. |
|| DELETE - Elimina la cadena especificada de la lista de valores. |
|| INDEX - Consulta el índice de la cadena especificada. Si la cadena no existe, el valor devuelto es 0. |
| Arg1 | Cadena o índice |
| Arg2 | Cadena o %Variable% |

## Observaciones

Si la `cadena` ya existe en `ValueName`, se registra una advertencia y se ignora la `Action`.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md), [RegHiveUnload](./RegHiveUnload.md)

## Ejemplos

### Ejemplo 1

Anexar una cadena al final de la lista de valores.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
// RegMulti,<HKEY>,<KeyPath>,<ValueName>,APPEND,<String>
RegMulti,HKLM,Tmp_System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,APPEND,snapman
RegHiveUnLoad,Tmp_System
```

### Ejemplo 2

Anteponer una cadena al comienzo de la lista de valores.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
// RegMulti,<HKEY>,<KeyPath>,<ValueName>,PREPEND,<String>
RegMulti,HKLM,Tmp_System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,PREPEND,snapman
RegHiveUnLoad,Tmp_System
```

### Ejemplo 3

Escribe una cadena antes de un valor especificado. En este ejemplo, escribiremos el valor `snapman` antes del valor `rdyboost`.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
// RegMulti,<HKEY>,<KeyPath>,<ValueName>,BEFORE,<SearchString>,<String>
RegMulti,HKLM,Tmp_System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,BEFORE,rdyboost,snapman
RegHiveUnLoad,Tmp_System
```

### Ejemplo 4

Escribe una cadena después de un valor especificado. En este ejemplo, escribiremos el valor `snapman` después del valor `rdyboost`.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
// RegMulti,<HKEY>,<KeyPath>,<ValueName>,BEHIND,<SearchString>,<String>
RegMulti,HKLM,Tmp_System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,BEHIND,rdyboost,snapman
RegHiveUnLoad,Tmp_System
```

### Ejemplo 5

Escribe una cadena en un índice específico. En este ejemplo, escribiremos el valor `snapman` en la tercera posición de la lista.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
// RegMulti,<HKEY>,<KeyPath>,<ValueName>,PLACE,<Index>,<String>
RegMulti,HKLM,Tmp_System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,PLACE,3,snapman
RegHiveUnLoad,Tmp_System
```

### Ejemplo 6

Eliminar una cadena de la lista.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
// RegMulti,<HKEY>,<KeyPath>,<ValueName>,DELETE,<String>
RegMulti,HKLM,Tmp_System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,DELETE,snapman
RegHiveUnLoad,Tmp_System
```

### Ejemplo 7

Encuentre la posición de una cadena especificada si existe en la lista.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
// RegMulti,<HKEY>,<KeyPath>,<ValueName>,INDEX,<String>,<DestVar>
RegMulti,HKLM,Tmp_System\ControlSet001\Control\Class\{71A27CDD-812A-11D0-BEC7-08002BE2092F},UpperFilters,INDEX,snapman,%varPos%
Echo,"snapman is located at position: %varPos%"
RegHiveUnLoad,Tmp_System
```
