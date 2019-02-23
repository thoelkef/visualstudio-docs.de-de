---
title: Symbole Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b6c5dcbd3601a6075097a44d2cd5dd625b4a87
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706690"
---
# <a name="symbols-element"></a>Symbols-Element
Definiert GUIDs und IDs, die durch andere VSCT-Elemente verwendet werden. Für nicht verwalteten Code, diese Informationen in der Regel stammen aus den Headerdateien, die vom angegebenen [Extern-Element](../extensibility/extern-element.md). Verwalteten Code verwendet die untergeordneten Elemente des Symbols-Element, um diese Informationen zu definieren.

 Wenn Sie eine VSCT-Datei aus einer vorhandenen CTO-Datei erstellen, werden die Symbole als untergeordnete Elemente des Elements Symbole generiert. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTO-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Das Element Symbole dürfen nicht verwechselt werden, mit der [Element definieren](../extensibility/define-element.md), das Name-Wert-Paare für die Verwendung durch den Präprozessor definiert.

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

|Attribut|Beschreibung|
|---------------|-----------------|
|Keine||

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|GuidSymbol|Definiert eine GUID-Symbol. GuidSymbol hat zwei obligatorische Attribute: Name-Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert der GUID als Zeichenfolge.<br /><br /> Zum Beispiel:\<GuidSymbol-Name = "guidVsPackage1Pkg" Value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|
|IDSymbol|Definiert ein Symbol an. IDSymbol hat zwei obligatorische Attribute: Name-Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert des Symbols als Zeichenfolge.<br /><br /> Zum Beispiel:\<IDSymbol-Name = "MyMenuGroup" Value = "0x1020" / >|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Das Stammelement der VSCT-Datei.|

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

## <a name="see-also"></a>Siehe auch
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)