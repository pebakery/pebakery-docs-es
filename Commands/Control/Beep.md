# Beep (Pitar)

Proporcionar retroalimentación auditiva al usuario.

## Sintaxis

```pebakery
Beep,<Type>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Type | Seleccionar de los siguientes sonidos: |
|| Ok |
|| Error |
|| Asterisco |
|| Confirmación |

## Observaciones

El sonido exacto que se reproduce con cada 'Tipo' se define por el esquema de sonido del sistema operativo.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
Beep,Error
```
