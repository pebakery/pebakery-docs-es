# ShellExecute

Ejecuta un programa externo y espera a que finalice antes de que el proceso continúe.

## Sintaxis

```pebakery
ShellExecute,<Action>,<FilePath>[,Params][,WorkDir][,%ExitOutVar%]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Action | El método utilizado para iniciar el archivo externo. Puede ser uno de los siguientes: |
|| Open - Si el archivo es un ejecutable, se lanzará. Si el archivo no es ejecutable, se abrirá con la aplicación predeterminada asociada a ese tipo de archivo.  |
|| Hide - El archivo se iniciará en modo oculto. Los programas de la consola que escriben en las secuencias StdOut y StdErr tendrán su salida redireccionada a la ventana de compilación PEBakerys y se escribirá en el registro. |
|| Print -Imprimir el contenido del archivo con la impresora predeterminada del sistema. |
|| Explore - Abra una ventana del explorador. (Se puede usar para mostrar los contenidos del sistema de archivos local). |
|| Min - Igual que Open, pero inicia el programa minimizado a la barra de tareas. |
| FilePath | El archivo para ejecutar Si no se especifica una ruta completa, PEBakery intentará localizarla utilizando la variable %PATH% del sistema operativo. |
| Params | **(Opcional)** Cualquier argumento que desee pasar al programa. Use ("") para ninguno. |
| WorkDir | **(Opcional)** El directorio de trabajo para el programa. Use ("") para especificar el directorio de trabajo actual. |
| %ExitOutVar% | **(Opcional)** Variable que se actualizará con el *Código de Salida* devuelto por la aplicación. Esto se puede usar para validar una ejecución exitosa o devolver un valor al script para su posterior procesamiento. Si no especifica este argumento, puede leer el *Código de Salida* de la variable fija `%ExitCode%`, que siempre contendrá el *Código de Salida* de la última instancia `ShellExecute`. |

## Observaciones

**Advertencia:** Usar la acción `Ocultar` con una aplicación que no se cierra automáticamente cuando termina hará que la secuencia de comandos se cuelgue hasta que finalice el proceso manualmente.

## Relacionado

[ShellExecuteDelete](./ShellExecuteDelete.md), [ShellExecuteEx](./ShellExecuteEx.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=ShellExecute Ejemplo
Author=Homes32
Description=Mostrar el uso del comando ShellExecute.
Version=1
Level=5

[Interface]

[variables]

[process]

// "Abrir" un programa que permanece abierto hasta que se cierre.
Echo,"Ejecutando notepad.exe...#$xDebe cerrar la aplicación Bloc de notas para continuar el proceso."
ShellExecute,open,notepad.exe

// "Abrir" un programa que saldrá cuando esté terminado.
Echo,"¡Ejecutar una aplicación de consola con la acción ABRIR es molesto!#$xUtilice la acción HIDE a menos que su aplicación requiera la intervención del usuario."
ShellExecute,open,cmd.exe,"/C PING 127.0.0.1 -n 10","",%return%
Message,"ShellExecute devuelto: %return%"

// Ejecute un programa "Oculto" que saldrá cuando esté terminado.
Echo,"Ejecutar una aplicación de consola que no requiera la intervención del usuario con la acción OCULTAR para evitar molestos cuadros emergentes y evitar que el usuario cierre accidentalmente el programa antes de que finished.#$xIt también nos permite ver el resultado del programa en el registro."
ShellExecute,hide,cmd.exe,"/C PING 127.0.0.1 -n 10","",%return%
Message,"ShellExecute devuelto: %return%"

// "Abrir" un programa "Minimizado".
Echo,"Ejecutando una aplicación de consola minimizada..."
ShellExecute,min,cmd.exe,"/C PING 127.0.0.1 -n 10","",%return%
Message,"ShellExecute devuelto: %return%"
```
