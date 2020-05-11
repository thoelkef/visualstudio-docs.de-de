---
title: CommandPlacements-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72b087652a654b563fd4e00bacc52290a29fe1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739698"
---
# <a name="commandplacements-element"></a>CommandPlacements-Element
Das CommandPlacements-Element gruppiert CommandPlacement-Elemente und andere CommandPlacements-Gruppierungen.

 Das CommandPlacements-Element ist optional. Wenn keine Befehle, Gruppen oder Menüs an einem sekundären Speicherort enthalten sein müssen, müssen Sie diesen Abschnitt nicht in die *.vsct-Datei* aufnehmen.

## <a name="syntax"></a>Syntax

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
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
|CommandPlacements|Gruppen CommandPlacement-Elemente und andere CommandPlacements-Gruppierungen.|
|[CommandPlacement-Element](../extensibility/commandplacement-element.md)|Ermöglicht das Eingeschlossen von Schaltflächen, Gruppen und Menüs in mehr als einer Gruppe oder einem Menü.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen.|

## <a name="example"></a>Beispiel

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Weitere Informationen
- [CommandPlacement-Element](../extensibility/commandplacement-element.md)
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
