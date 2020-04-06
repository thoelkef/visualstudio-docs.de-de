---
title: Symbole Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699349"
---
# <a name="symbols-element"></a>Symbols-Element
Definiert GUIDs und IDs, die von anderen VSCT-Elementen verwendet werden. Bei nicht verwaltetem Code stammen diese Informationen in der Regel aus den Headerdateien, die von [Extern Element](../extensibility/extern-element.md)angegeben werden. Verwalteter Code verwendet die untergeordneten Elemente des Symbols-Elements, um diese Informationen zu definieren.

 Wenn Sie eine .vsct-Datei aus einer vorhandenen Cto-Datei erstellen, werden die Symbole als untergeordnete Elemente des Symbols-Elements generiert. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen einer . Vsct-Datei aus einer vorhandenen . Cto-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Das Symbols-Element sollte nicht mit dem [Define Element](../extensibility/define-element.md)verwechselt werden, das Name-Wert-Paare für die Verwendung durch den Präprozessor definiert.

## <a name="syntax"></a>Syntax

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|Keine||

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Guidsymbol|Definiert ein GUID-Symbol. GuidSymbol hat zwei erforderliche Attribute: Name und Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert der GUID als Zeichenfolge.<br /><br /> Beispiel:\<GuidSymbol name="guidVsPackage1Pkg" value="'c5f54698-101a-4846-84d3-dc748f9cd848' />|
|IDSymbol|Definiert ein Symbol. IDSymbol hat zwei erforderliche Attribute: Name und Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert des Symbols als Zeichenfolge.<br /><br /> Beispiel:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Das Stammelement der .vsct-Datei.|

## <a name="example"></a>Beispiel

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Weitere Informationen
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
