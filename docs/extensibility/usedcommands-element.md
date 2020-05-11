---
title: UsedCommands Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76732b2a9700f1737af495098c8c23aa4b618819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698756"
---
# <a name="usedcommands-element"></a>UsedCommands-Element
Die UsedCommands-Elemente gruppen UsedCommand-Elemente und andere UsedCommands-Gruppierungen.

 Das UsedCommands-Element ist optional. Wenn Sie keine Außerhalb Ihres Pakets definierten Befehle aufrufen, müssen Sie diesen Abschnitt nicht in Ihre .vsct-Datei aufnehmen.

## <a name="syntax"></a>Syntax

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[UsedCommand-Element](../extensibility/usedcommand-element.md)|Der Befehl, der von anderem Code implementiert wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen (z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder), die ein VSPackage für die integrierte Entwicklungsumgebung (IDE) bereitstellt.|

## <a name="example"></a>Beispiel

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Weitere Informationen
- [UsedCommand-Element](../extensibility/usedcommand-element.md)
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
