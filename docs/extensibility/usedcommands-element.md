---
title: UsedCommands-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e43834517855f72dd32c024c222089cf42c7c3ac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316287"
---
# <a name="usedcommands-element"></a>UsedCommands-Element
UsedCommands-Element gruppiert UsedCommand-Elementen und anderen UsedCommands Gruppierungen.

 UsedCommands-Element ist optional. Wenn Sie Befehle, die außerhalb des Pakets definiert nicht aufrufen, müssen Sie nicht in diesem Abschnitt in der VSCT-Datei enthalten.

## <a name="syntax"></a>Syntax

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[UsedCommand-Element](../extensibility/usedcommand-element.md)|Der Befehl, der durch anderen Code implementiert wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle (z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern), die eine VSPackage bietet die integrierte Entwicklungsumgebung (IDE) darstellen.|

## <a name="example"></a>Beispiel

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Siehe auch
- [UsedCommand-Element](../extensibility/usedcommand-element.md)
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)