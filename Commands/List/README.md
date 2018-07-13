# Comandos de lista

Los comandos de lista le permiten crear y manipular estructuras de lista.

Una PEBakery `Lista` consiste en una matriz unidimensional de cadenas separadas por un delimitador elegido. El primer elemento de la matriz se indexa mediante el subíndice de 1 (índice basado en 1) y se incrementa para cada elemento adicional en la lista.

Ejemplo:

```pebakery
%myList%=Home|Professional|Enterprise|Starter|Ultimate
```

Se traduce lógicamente en:

| | | | | | |
| --- | :---: | :---: | :---: | :---: | :---: |
| **Index** | 1 | 2 | 3 | 4 | 5 |
| **Value** | Home | Professional | Enterprise | Starter | Ultimate |

Haga clic en un nombre de comando para obtener una descripción detallada.

| Comando | Descripción |
| --- | --- |
| [List,Append](./Append.md) | Agregar un valor al final de una lista. |
| [List,Count](./Count.md) | Devuelve la cantidad de elementos en una lista. |
| [List,Get](./Get.md) | Extrae un elemento específico de una lista. |
| [List,Insert](./Insert.md) | Insertar un nuevo valor en una ubicación específica en una lista. |
| [List,LastPos](./LastPos.md) | Devuelve la última posición del valor especificado dentro de la lista especificada. **Insensible a mayúsculas/minúsculas.** |
| [List,LastPosX](./LastPosX.md) | Devuelve la última posición del valor especificado dentro de la lista especificada. **Sensible a mayúsculas/minúsculas.** |
| [List,Pos](./Pos.md) | Devuelve la posición del valor dado dentro de la lista especificada. **Insensible a mayúsculas/minúsculas.** |
| [List,PosX](./PosX.md) | Devuelve la posición del valor dado dentro de la lista especificada. **Sensible a mayúsculas/minúsculas.** |
| [List,Remove](./Remove.md) | Elimina todas las apariciones de un valor de una lista. **Insensible a mayúsculas/minúsculas.** |
| [List,RemoveAt](./RemoveAt.md) | Elimina un valor de un índice específico en una lista. |
| [List,RemoveX](./RemoveX.md) | Elimina todas las apariciones de un valor de una lista. **Sensible a mayúsculas/minúsculas.** |
| [List,Set](./Set.md) | Escribe un valor en un índice específico en una lista. |
| [List,Sort](./Sort.md) | Ordena una lista en orden alfabético/lexicográfico. **Insensible a mayúsculas/minúsculas.** |
| [List,SortN](./SortN.md) | Ordena una lista en orden natural. **Insensible a mayúsculas/minúsculas.** |
| [List,SortNX](./SortNX.md) | Ordena una lista en orden natural. **Sensible a mayúsculas/minúsculas.** |
| [List,SortX](./SortX.md)  | Ordena una lista en orden alfabético/lexicográfico. **Sensible a mayúsculas/minúsculas.** |
