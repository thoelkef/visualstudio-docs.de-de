---
title: CommandPlacement-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9367e412f66ded1fd009b31a4788ed4ecc86a2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891238"
---
# <a name="commandplacement-element"></a>CommandPlacement-element
CommandPlacement-Element kann die Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder ein Menü einbezogen werden. Verwenden Sie das CommandPlacement-Element, müssen Sie keinen dieser Elemente vollständig neu definieren, um das Aussehen einer Benutzeroberfläche zu ändern.

 Weitere Informationen finden Sie unter [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md).

## <a name="syntax"></a>Syntax

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. Die Guid für den Befehlssatz, gemäß der [Symbols-Element](../extensibility/symbols-element.md).|
|id|Erforderlich. Die Id der Menüs, eine Gruppe oder ein Befehl aus, um die Platzierung gemäß der `Symbols Element`.|
|priority|Erforderlich. Bestimmt die visuelle Position des Elements in seinem übergeordneten Element.|
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Übergeordnetes Element|Erforderlich. Der im Menü oder die Gruppe, die das Element platziert werden hostet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CommandPlacements-element](../extensibility/commandplacements-element.md)|Gibt Gruppen von CommandPlacements und CommandPlacement-Elementen.|

## <a name="example"></a>Beispiel

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Siehe auch
- [CommandPlacements-element](../extensibility/commandplacements-element.md)
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
