---
title: Commandplacement-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739745"
---
# <a name="commandplacement-element"></a>Commandplacement-Element
Das commandplacement-Element ermöglicht das Einschließen von Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder ein Menü. Mit dem commandplacement-Element müssen Sie diese Elemente nicht vollständig neu definieren, um das Aussehen einer Benutzeroberfläche zu ändern.

 Weitere Informationen finden Sie unter [Erstellen wiederverwendbarer Gruppen von Schalt](../extensibility/creating-reusable-groups-of-buttons.md)Flächen.

## <a name="syntax"></a>Syntax

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. Die GUID des Befehlssatzes, wie im [Symbols-Element](../extensibility/symbols-element.md)definiert.|
|id|Erforderlich. Die ID des zu platzierenden Menüs, der Gruppe oder des Befehls, wie in definiert `Symbols Element` .|
|priority|Erforderlich. Bestimmt die visuelle Position des Elements in seinem übergeordneten Element.|
|Bedingung|Optional. Siehe [bedingte aattribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Parent|Erforderlich. Das Menü oder die Gruppe, das das zu platzierende Element hostet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Commandplacement-Element](../extensibility/commandplacements-element.md)|Gibt Gruppen von commandplacement-und commandplacement-Elementen an.|

## <a name="example"></a>Beispiel

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Weitere Informationen
- [Commandplacement-Element](../extensibility/commandplacements-element.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
