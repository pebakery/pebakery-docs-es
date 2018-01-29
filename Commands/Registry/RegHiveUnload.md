# RegHiveUnload

Descarga una sección de registro externo de su registro local.

## Sintaxis

```pebakery
RegHiveLoad,<KeyPath>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| KeyPath | La clave de registro donde la sección esta cargada. |

## Observaciones

Una sección de registro montada con `RegHiveLoad` debe desmontarse con `RegHiveUnload`.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md)

## Ejemplos

#### Ejemplo 1

```pebakery
RegHiveUnload,Tmp_Software
```
