---
title: Commandtable-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f577b52ad2a9b1fd66ed9c24fb2737621aa8554c
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557779"
---
# <a name="commandtable-element"></a>Commandtable-Element
Commandtable ist das Stamm Element der *vsct* -Datei. Dies ist die Datei, die das tatsächliche Layout und den Typ der Befehle definiert, die ein VSPackage für die IDE bereitstellt. Befehle können Menü Elemente, Menüs, Symbolleisten und Kombinations Felder enthalten. Weitere Informationen finden Sie unter [Visual Studio-Befehls Tabellen Dateien (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="syntax"></a>Syntax

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden die Attribute, untergeordneten und übergeordneten Elemente beschrieben.

### <a name="attributes"></a>Attributes

| attribute | BESCHREIBUNG |
|-----------| - |
| xmlns | Erforderlich. XML-Namespaces:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = "<http://www.w3.org/2001/XMLSchema>" |
| language | Optional. Das Language-Attribut kann verwendet werden, um die Standardsprache aller \<Zeichen folgen > Elemente in der Befehls Tabelle anzugeben.  Wenn die Sprache nicht angegeben wird, wird die Sprache des aktuellen Prozesses verwendet:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Extern-Element](../extensibility/extern-element.md)|Optional. Enthält Präprozessordirektiven für den Compiler.|
|[Include-Element](../extensibility/include-element.md)|Optional. Enthält Pfade zu allen Dateien, die in die Kompilierung eingeschlossen werden sollen.|
|[Define-Element](../extensibility/define-element.md)|Optional. Definiert ein Symbol anhand seines Namens und Werts.|
|[Commands-Element](../extensibility/commands-element.md)|Optional. Das übergeordnete Element, das alle Befehle für das VSPackage definiert, das alle anderen Elemente enthält.|
|[Commandplacement-Element](../extensibility/commandplacements-element.md)|Optional. Definiert, wo in der Befehlsleiste die Befehle platziert werden sollen.|
|[Visibilityschränkt-Element](../extensibility/visibilityconstraints-element.md)|Optional. Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|
|[KeyBinding-Element](../extensibility/keybindings-element.md)|Optional. Gibt ggf. die Tastenkombinationen für die Befehle an.|
|[Usedcommands-Element](../extensibility/usedcommands-element.md)|Optional. Ermöglicht einem VSPackage, optional seine eigene Version der Funktionalität zu implementieren, die ursprünglich von anderen VSPackages unterstützt wurde.|
|[Symbols-Element](https://www.microsoft.com/download/details.aspx?id=55984)|Optional. Enthält beliebige Symbol Daten-GUIDs, IDs usw. für den Compiler.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine||

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)