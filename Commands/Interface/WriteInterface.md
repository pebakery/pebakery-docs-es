# WriteInterface

Cambia las propiedades de un control de interfaz.

## Sintaxis

```pebakery
WriteInterface,<Property>,<ScriptFile>,<Interface>,<ControlName>,<Value>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Property | El valor de propiedad para editar:
|| Texto - Valor de texto del control. |
|| Visible - `Verdadero`/`Falso` - Mostrar u ocultar el control. |
|| PosX - Posición horizontal medida desde la esquina superior izquierda del control. |
|| PosY - Posición vertical medida desde la esquina superior izquierda del control. |
|| Ancho - Ancho del control. |
|| Altura - Altura del control. |
|| Valor - Valor del control. |
| ScriptFile | La ruta completa al script **Sugerencia:** Use `%ScriptFile%` para hacer referencia al script actual. |
| Interface | El nombre de la sección que contiene el control de interfaz que desea modificar. |
| ControlName | El nombre del control para modificar. |
| Value | El nuevo valor a escribir. |

## Observaciones

La propiedad `Valor` solo se admite en estos controles:

| Control | Leer valor |
| --- | --- |
| TextBox     | (Cadena) Contenido del control. |
| NumberBox   | (Cadena) Contenido del control. |
| CheckBox    | (Booleano) Verdadero/Falso, Verdadero si está marcado. |
| ComboBox    | (Cadena) Elemento seleccionado. |
| RadioButton | (Booleano) Verdadero/Falso, Verdadero si está marcado. |
| FileBox     | (Cadena) Contenido del control. |
| RadioGroup  | (Entero) Índice basado en cero del elemento seleccionado. |

Tratar de escribir un `Valor` para un control no compatible dará como resultado un error.

```pebakery
// ¡Error! No puede escribir un valor en una etiqueta de texto.
WriteInterface,Value,%ScriptFile%,Interface,pTextLabel1,PEBakery
```

Intentar escribir un tipo no válido también dará como resultado un error.

```pebakery
// ¡Error! La casilla de verificación solo acepta True o False.
WriteInterface,Value,%ScriptFile%,Interface,pCheckBox1,Joveler
```

## Relacionado

[Script Interface](#), [Set](../Control/Set.md), [Visible](./Visible.md)

## Ejemplos

### Ejemplo 1

Un script interactivo que demuestra varios usos.

```pebakery
[main]
Title=WriteInterface Ejemplo
Description=Mostrar el uso de WriteInterface
Level=5
Version=1
Author=Homes32

[variables]

[Process]

[Toggle_Advanced_Options]
System,CURSOR,WAIT
If,%SB_CfgProfile%,Equal,"Advanced",Begin
  WriteInterface,Visible,%ScriptFile%,Interface,BVL_AdvOptions,True
  WriteInterface,Visible,%ScriptFile%,Interface,LBL_AdvOptions,True
  WriteInterface,Visible,%ScriptFile%,Interface,CB_Adv1,True
  WriteInterface,Visible,%ScriptFile%,Interface,CB_Adv2,True
  WriteInterface,Visible,%ScriptFile%,Interface,BTN_SelectAll,True
  WriteInterface,Visible,%ScriptFile%,Interface,BTN_SelectNone,True
  WriteInterface,Visible,%ScriptFile%,Interface,LBL_Info,True
End
Else,Begin
  WriteInterface,Visible,%ScriptFile%,Interface,BVL_AdvOptions,False
  WriteInterface,Visible,%ScriptFile%,Interface,LBL_AdvOptions,False
  WriteInterface,Visible,%ScriptFile%,Interface,CB_Adv1,False
  WriteInterface,Visible,%ScriptFile%,Interface,CB_Adv2,False
  WriteInterface,Visible,%ScriptFile%,Interface,BTN_SelectAll,False
  WriteInterface,Visible,%ScriptFile%,Interface,BTN_SelectNone,False
  WriteInterface,Visible,%ScriptFile%,Interface,LBL_Info,False
End
System,CURSOR,NORMAL

[SelectAll]
WriteInterface,Value,%ScriptFile%,Interface,CB_Adv1,True
WriteInterface,Value,%ScriptFile%,Interface,CB_Adv2,True
WriteInterface,Text,%ScriptFile%,Interface,LBL_Info,"All Options Selected!"

[SelectNone]
WriteInterface,Value,%ScriptFile%,Interface,CB_Adv1,False
WriteInterface,Value,%ScriptFile%,Interface,CB_Adv2,False
WriteInterface,Text,%ScriptFile%,Interface,LBL_Info,"All Options Disabled!"

[ReadValues]
// Leer visibilidad
ReadInterface,Visible,%ScriptFile%,Interface,CB_Adv1,%value%
Message,"The Option 1 check box is Visible: %value%"

// Leer valor
ReadInterface,Value,%ScriptFile%,Interface,CB_Adv1,%value%
Message,"The Option 1 check box is Checked: %value%"

// Leer Texto
ReadInterface,Text,%ScriptFile%,Interface,CB_Adv1,%value%
Message,"The Option 1 check box caption is: %value%"

// Leer dimensiones
ReadInterface,Height,%ScriptFile%,Interface,CB_Adv1,%height%
ReadInterface,Width,%ScriptFile%,Interface,CB_Adv1,%width%
Message,"The Option 1 check box dimensions are : %width%x%height%"

// Leer posición
ReadInterface,PosX,%ScriptFile%,Interface,CB_Adv1,%x%
ReadInterface,PosY,%ScriptFile%,Interface,CB_Adv1,%y%
Message,"The Option 1 check box is located at : %x%#$c%y%"

// Caja de texto
ReadInterface,Text,%ScriptFile%,Interface,TXT_FilePath,%text%
ReadInterface,Value,%ScriptFile%,Interface,TXT_FilePath,%value%
Message,"Text box name: %text% #$x Text box value: %value%"

[BumpLeft]
// Mover el cuadro de texto a la izquierda
ReadInterface,PosX,%ScriptFile%,Interface,TXT_MoveMe,%x%
ReadInterface,PosY,%ScriptFile%,Interface,TXT_MoveMe,%y%
StrFormat,DEC,%x%,1
WriteInterface,PosX,%ScriptFile%,Interface,TXT_MoveMe,%x%
WriteInterface,Text,%ScriptFile%,Interface,LBL_X,%x%
WriteInterface,Text,%ScriptFile%,Interface,LBL_Y,%y%

[BumpRight]
// Mover el cuadro de texto a la derecha
ReadInterface,PosX,%ScriptFile%,Interface,TXT_MoveMe,%x%
ReadInterface,PosY,%ScriptFile%,Interface,TXT_MoveMe,%y%
StrFormat,INC,%x%,1
WriteInterface,PosX,%ScriptFile%,Interface,TXT_MoveMe,%x%
WriteInterface,Text,%ScriptFile%,Interface,LBL_X,%x%
WriteInterface,Text,%ScriptFile%,Interface,LBL_Y,%y%

[Shrink]
// Hacer el cuadro de texto más pequeño
ReadInterface,Width,%ScriptFile%,Interface,TXT_MoveMe,%width%
ReadInterface,Height,%ScriptFile%,Interface,TXT_MoveMe,%height%
StrFormat,DEC,%width%,1
StrFormat,DEC,%height%,1
WriteInterface,Width,%ScriptFile%,Interface,TXT_MoveMe,%width%
WriteInterface,Height,%ScriptFile%,Interface,TXT_MoveMe,%height%
WriteInterface,Text,%ScriptFile%,Interface,LBL_WidthValue,%width%
WriteInterface,Text,%ScriptFile%,Interface,LBL_HeightValue,%height%

[Grow]
// Hacer el cuadro de texto más grande
ReadInterface,Width,%ScriptFile%,Interface,TXT_MoveMe,%width%
ReadInterface,Height,%ScriptFile%,Interface,TXT_MoveMe,%height%
StrFormat,INC,%width%,1
StrFormat,INC,%height%,1
WriteInterface,Width,%ScriptFile%,Interface,TXT_MoveMe,%width%
WriteInterface,Height,%ScriptFile%,Interface,TXT_MoveMe,%height%
WriteInterface,Text,%ScriptFile%,Interface,LBL_WidthValue,%width%
WriteInterface,Text,%ScriptFile%,Interface,LBL_HeightValue,%height%

[Interface]
LBL_CfgProfile="Configuration Profile:",1,1,12,16,120,20,8,Bold
SB_CfgProfile=Advanced,1,4,135,10,150,21,Simple,Advanced,_Toggle_Advanced_Options_,True
TXT_FilePath="File Path",1,0,16,78,200,21,C:\Temp
BVL_AdvOptions=pBevel1,1,12,9,114,170,88,
LBL_AdvOptions="Advanced Options:",1,1,23,120,147,18,8,Bold
CB_Adv1="Option 1",1,3,20,150,145,20,True
CB_ADV2="Option 2",1,3,20,170,135,20,True
BTN_SelectAll="Select All",1,8,94,146,80,25,SelectAll,0,True
BTN_SelectNone="Select None",1,8,94,170,80,25,SelectNone,0,True
LBL_Info="All Options Selected!",1,1,10,206,170,18,8,Bold
BTN_ReadValues="Read Values",1,8,200,135,147,48,ReadValues,0,True
BTN_BumpLeft=<<,1,8,170,276,80,25,BumpLeft,0,True
BTN_BumpRight=>>,1,8,261,276,80,25,BumpRight,0,True
TXT_MoveMe="Use buttons to change me!",1,0,154,247,200,21,abc..
BTN_Shrink=Shrink,1,8,170,303,80,25,Shrink,0,True
BTN_Grow=Grow,1,8,261,303,80,25,Grow,0,True
pBevel1=pBevel1,1,12,146,334,211,40
LBL_PosX="PosX: ",1,1,152,339,32,18,8,Normal
LBL_PosY=PosY:,1,1,151,360,33,18,8,Normal
LBL_X=154,1,1,186,339,58,18,8,Normal
LBL_Y=247,1,1,186,360,58,18,8,Normal
LBL_Width=Width:,1,1,259,339,39,18,8,Normal
LBL_Height=Height:,1,1,258,360,40,18,8,Normal
LBL_WidthValue=200,1,1,301,340,50,18,8,Normal
LBL_HeightValue=21,1,1,301,360,50,18,8,Normal
```

### Ejemplo 2

Supongamos que un archivo %ScriptFile% consta de estas secciones:

```pebakery
[Main]
Title=WriteInterface
Author=ied206
Description=UnitTest
Version=001
Level=5

[Interface]
pTextBox1=Display,1,0,20,20,200,21,StringValue
pTextLabel1=Display,1,1,20,50,230,18,8,Normal
pNumberBox1=pNumberBox1,1,2,20,70,40,22,3,0,100,1
pCheckBox1=pCheckBox1,1,3,20,100,200,18,True
pComboBox1=A,1,4,20,130,150,21,A,B,C,D
pRadioGroup1=pRadioGroup1,1,14,20,160,150,60,Option1,Option2,Option3,0
pImage1=Logo.jpg,1,5,20,230,40,40,
pTextFile1=HelpMsg.txt,1,6,240,20,200,86
pButton1=ShowProgress,1,8,240,115,80,25,Hello,0,False,False,_Hello_,False
pButton2=HideProgress,1,8,330,115,80,25,Hello,0,True,_Hello_,True
pWebLabel1=GitHub,1,10,250,160,32,18,https://github.com/ied206/PEBakery
pRadioButton1=pRadioButton1,1,11,250,180,100,20,False
pBevel1=pBevel1,1,12,240,150,235,60
pFileBox1=C:\Windows\notepad.exe,1,13,240,230,200,20,file
pFileBox2=E:\WinPE\,1,13,240,260,200,20,dir
pTextLabel2=Hidden,0,1,20,50,280,18,8,Normal
```

#### Escribir texto

```pebakery
// Origen : pTextBox1=Display,1,0,20,20,200,21,StringValue
// Resultado : pTextBox1=PEBakery,1,0,20,20,200,21,StringValue
WriteInterface,Text,%ScriptFile%,Interface,pTextBox1,PEBakery
```

#### Escribir visibilidad

```pebakery
// Origen : pTextLabel1=Display,1,1,20,50,230,18,8,Normal
// Resultado : pTextLabel1=Display,0,1,20,50,230,18,8,Normal
WriteInterface,Visible,%ScriptFile%,Interface,pTextLabel1,False
```

#### Escribir valor

```pebakery
// Origen : pTextBox1=Display,1,0,20,20,200,21,StringValue
// Resultado : pTextBox1=Display,1,0,20,20,200,21,PEBakery
WriteInterface,Value,%ScriptFile%,Interface,pTextBox1,PEBakery

// Origen : pNumberBox1=pNumberBox1,1,2,20,70,40,22,3,0,100,1
// Resultado : pNumberBox1=pNumberBox1,1,2,20,70,40,22,2,0,100,1
WriteInterface,Value,%ScriptFile%,Interface,pNumberBox1,2

// Origen : pNumberBox1=pNumberBox1,1,2,20,70,40,22,3,0,100,1
// Resultado : pNumberBox1=pNumberBox1,1,2,20,70,40,22,2,0,100,1
WriteInterface,Value,%ScriptFile%,Interface,pCheckBox1,%Dest%

// Origen : pComboBox1=A,1,4,20,130,150,21,A,B,C,D
// Resultado : pComboBox1=B,1,4,20,130,150,21,A,B,C,D
WriteInterface,Value,%ScriptFile%,Interface,pComboBox1,B

// Origen : pRadioButton1=pRadioButton1,1,11,250,180,100,20,False
// Resultado : pRadioButton1=pRadioButton1,1,11,250,180,100,20,True
WriteInterface,Value,%ScriptFile%,Interface,pRadioButton1,True

// Origen : pFileBox1=C:\Windows\notepad.exe,1,13,240,230,200,20,file
// Resultado : pFileBox1=D:\PEBakery\Launcher.exe,1,13,240,230,200,20,file
WriteInterface,Value,%ScriptFile%,Interface,pFileBox1,D:\PEBakery\Launcher.exe

// Origen : pRadioGroup1=pRadioGroup1,1,14,20,160,150,60,Option1,Option2,Option3,2
// Resultado : pRadioGroup1=pRadioGroup1,1,14,20,160,150,60,Option1,Option2,Option3,0
WriteInterface,Value,%ScriptFile%,Interface,pRadioGroup1,0
>>>>>>> develop
```
