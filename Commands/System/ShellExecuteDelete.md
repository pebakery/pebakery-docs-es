# ShellExecuteDelete

Ejecuta un programa externo y espera a que finalice antes de que el procesamiento continúe. Una vez que el programa finaliza, se eliminará.

## Sintaxis

```pebakery
ShellExecuteDelete,<Action>,<FilePath>[,Params][,WorkDir][,%ExitOutVar%]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Action | El método utilizado para iniciar el archivo externo. Puede ser uno de los siguientes: |
|| Open - Si el archivo es un ejecutable, se lanzará. Si el archivo no es ejecutable, se abrirá con la aplicación predeterminada asociada a ese tipo de archivo.  |
|| Hide - El archivo se iniciará en modo oculto. Los programas de la consola que escriben en las secuencias StdOut y StdErr tendrán su salida redireccionada a la ventana de compilación PEBakery y se escribirá en el registro. |
|| Print - Imprimir el contenido del archivo con la impresora predeterminada del sistema. |
|| Explore - Abra una ventana del explorador. (Se puede usar para mostrar los contenidos del sistema de archivos local). |
|| Min - Igual que Open, pero inicia el programa minimizado a la barra de tareas. |
| FilePath | El archivo para ejecutar Si no se especifica una ruta completa, PEBakery intentará localizarla utilizando la variable %PATH% del sistema operativo. |
| Params | **(Opcional)** Cualquier argumento que desee pasar al programa. Use ("") para ninguno. |
| WorkDir | **(Opcional)** El directorio de trabajo para el programa. Use ("") para especificar el directorio de trabajo actual. |
| %ExitOutVar% | **(Optional)** Variable que se actualizará con el *Código de Salida* devuelto por la aplicación. Esto se puede usar para validar una ejecución exitosa o devolver un valor al script para su posterior procesamiento. Si no especifica este argumento, puede leer el *Código de Salida* de la variable fija `%ExitCode%`, que siempre contendrá el *Código de Salida* de la última instancia `ShellExecute`. |

## Observaciones

Este comando está diseñado para ser utilizado para ejecutar pequeñas herramientas / scripts / archivos autoextraíbles y "limpiar" después de que haya terminado.

**Advertencia:**
Este comando está destinado a usuarios experimentados solamente. ¡No hay recuperación!

Usar la acción `Ocultar` con una aplicación que no se cierra automáticamente cuando termina hará que la secuencia de comandos se cuelgue hasta que finalice el proceso manualmente.

## Relacionado

[ShellExecute](./ShellExecute.md), [ShellExecuteEx](./ShellExecuteEx.md)

## Ejemplos

### Ejemplo 1

```pebakery
// ejecutar un programa para realizar un proceso en nuestro %TargetDir%, luego eliminar myTool.exe cuando haya terminado.
ShellExecuteDelete,hide,myTool.exe,"/process",%TargetDir%
```
