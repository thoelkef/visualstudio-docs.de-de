---
title: CommandPlacement-Element | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739745"
---
# <a name="commandplacement-element"></a>CommandPlacement-Element
Mit dem CommandPlacement-Element können Schaltflächen, Gruppen und Menüs in mehr als einer Gruppe oder einem Menü enthalten sein. Wenn Sie das CommandPlacement-Element verwenden, müssen Sie diese Elemente nicht vollständig neu definieren, um das Aussehen einer Benutzeroberfläche zu ändern.

 Weitere Informationen finden Sie unter [Erstellen wiederverwendbarer Schaltflächengruppen](../extensibility/creating-reusable-groups-of-buttons.md).

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
|guid|Erforderlich. Die GUId des Befehlssatzes, wie im [Symbols-Element](../extensibility/symbols-element.md)definiert.|
|id|Erforderlich. Die ID des Menüs, der Gruppe oder des `Symbols Element`Befehls, die platziert werden soll, wie in der definiert.|
|priority|Erforderlich. Bestimmt die visuelle Position des Elements im übergeordneten Element.|
|Bedingung|Optional. Siehe [Bedingte Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Parent|Erforderlich. Das Menü oder die Gruppe, in der das zu postende Element gehostet wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandPlacements-Element](../extensibility/commandplacements-element.md)|Gibt Gruppen von CommandPlacements- und CommandPlacement-Elementen an.|

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
- [CommandPlacements-Element](../extensibility/commandplacements-element.md)
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
