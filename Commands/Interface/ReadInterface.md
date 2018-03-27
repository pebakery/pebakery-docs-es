# ReadInterface

Lee las propiedades de un control de interfaz.

## Sintaxis

```pebakery
ReadInterface,<Property>,<ScriptFile>,<Interface>,<ControlName>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Property | El valor de propiedad para leer:
|| Texto - Valor de texto del control. |
|| Visible - `Verdadero`/`Falso` - Mostrar u ocultar el control. |
|| PosX - Posición horizontal medida desde la esquina superior izquierda del control. |
|| PosY - Posición vertical medida desde la esquina superior izquierda del control. |
|| Ancho - Ancho del control. |
|| Altura - Altura del control. |
|| Valor - Valor del control. |
|| ToolTip - El texto que se mostrará cuando el usuario se desplaza sobre el control. |
| ScriptFile | La ruta completa al script **Sugerencia:** Use `%ScriptFile%` para hacer referencia al script actual. |
| Interface | El nombre de la sección que contiene la interfaz que desea leer. |
| ControlName | El nombre del control a leer. |
| DestVar | La variable que contendrá el valor de la propiedad seleccionada. |

## Observaciones

La propiedad `Valor` solo se admite en estos controles:

| Control | Valor |
| --- | --- |
| TextBox     | (Cadena) Contenido del control. |
| NumberBox   | (Cadena) Contenido del control. |
| CheckBox    | (Booleano) Verdadero/Falso, Verdadero si está marcado. |
| ComboBox    | (Cadena) Elemento seleccionado. |
| RadioButton | (Booleano) Verdadero/Falso, Verdadero si está marcado. |
| FileBox     | (Cadena) Contenido del control. |
| RadioGroup  | (Entero) Índice basado en cero del elemento seleccionado. |

Intentar leer `Valor` desde un control no compatible dará como resultado un error.

```pebakery
// ¡Error! No puedes leer el valor de una etiqueta de texto.
ReadInterface,Value,%ScriptFile%,Interface,pTextLabel1,%Dest%
```

## Relacionado

[Script Interface](#), [WriteInterface](./WriteInterface.md)

## Ejemplos

### Ejemplo 1

Un script interactivo que demuestra varios usos.

```pebakery
[main]
Title=Read/Write Interface Ejemplo
Description=Mostrar el uso de ReadInterface y WriteInterface
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
// Leer Visibilidad
ReadInterface,Visible,%ScriptFile%,Interface,CB_Adv1,%value%
Message,"The Option 1 check box is Visible: %value%"

// Leer valor
ReadInterface,Value,%ScriptFile%,Interface,CB_Adv1,%value%
Message,"The Option 1 check box is Checked: %value%"

// Leer texto
ReadInterface,Text,%ScriptFile%,Interface,CB_Adv1,%value%
Message,"The Option 1 check box caption is: %value%"

// Leer Dimensiones
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
// Haga el cuadro de texto más pequeño
ReadInterface,Width,%ScriptFile%,Interface,TXT_MoveMe,%width%
ReadInterface,Height,%ScriptFile%,Interface,TXT_MoveMe,%height%
StrFormat,DEC,%width%,1
StrFormat,DEC,%height%,1
WriteInterface,Width,%ScriptFile%,Interface,TXT_MoveMe,%width%
WriteInterface,Height,%ScriptFile%,Interface,TXT_MoveMe,%height%
WriteInterface,Text,%ScriptFile%,Interface,LBL_WidthValue,%width%
WriteInterface,Text,%ScriptFile%,Interface,LBL_HeightValue,%height%

[Grow]
// Haga el cuadro de texto más grande
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
Title=ReadInterface
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

#### Leer texto
```pebakery
// Devolver "Visualización"
ReadInterface,Text,%ScriptFile%,Interface,pTextBox1,%Dest%
```

#### Leer visibilidad

```pebakery
// Devolver "Verdadero"
ReadInterface,Visible,%ScriptFile%,Interface,pTextLabel1,%Dest%
// Devolver "Falso"
ReadInterface,Visible,%ScriptFile%,Interface,pTextLabel2,%Dest%
```

#### Leer valor

```pebakery
// Devolver "StringValue"
ReadInterface,Value,%ScriptFile%,Interface,pTextBox1,%Dest%

// Devolver "3"
ReadInterface,Value,%ScriptFile%,Interface,pNumberBox1,%Dest%

// Devolver "Verdadero"
ReadInterface,Value,%ScriptFile%,Interface,pCheckBox1,%Dest%

// Devolver "A"
ReadInterface,Value,%ScriptFile%,Interface,pComboBox1,%Dest%

// Devolver "Falso"
ReadInterface,Value,%ScriptFile%,Interface,pRadioButton1,%Dest%

// Devolver "C:\Windows\notepad.exe"
ReadInterface,Value,%ScriptFile%,Interface,pFileBox1,%Dest%

// Devolver "0"
ReadInterface,Value,%ScriptFile%,Interface,pRadioGroup1,%Dest%
```
