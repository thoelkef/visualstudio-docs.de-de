---
title: CommandTable-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739642"
---
# <a name="commandtable-element"></a>CommandTable-Element
CommandTable ist das Stammelement der *.vsct-Datei.* Dies ist die Datei, die das tatsächliche Layout und den Typ der Befehle definiert, die ein VSPackage für die IDE bereitstellt. Befehle können Menüelemente, Menüs, Symbolleisten und Kombinationsfelder enthalten. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellendateien (.vsct) .](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

| attribute | BESCHREIBUNG |
|-----------| - |
| xmlns | Erforderlich. XML-Namespaces:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| language | Optional. Das Sprachattribut kann verwendet werden, um \<die Standardsprache aller Strings> Elemente in der Befehlstabelle anzugeben.  Wenn die Sprache nicht angegeben ist, wird die Sprache des aktuellen Prozesses verwendet:<br /><br /> language="en-uns" |

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Externes Element](../extensibility/extern-element.md)|Optional. Enthält Präprozessordirektiven für den Compiler.|
|[Include-Element](../extensibility/include-element.md)|Optional. Enthält Pfade zu allen Dateien, die in die Kompilierung aufgenommen werden sollen.|
|[Definieren des Elements](../extensibility/define-element.md)|Optional. Definiert ein Symbol mit seinem Namen und Wert.|
|[Befehlselement](../extensibility/commands-element.md)|Optional. Das übergeordnete Element, das alle Befehle für das VSPackage definiert, das alle anderen Elemente enthält.|
|[CommandPlacements-Element](../extensibility/commandplacements-element.md)|Optional. Definiert, wo auf der Befehlsleiste die Befehle platziert werden sollen.|
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Optional. Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|
|[KeyBindings-Element](../extensibility/keybindings-element.md)|Optional. Gibt die Tastenkombinationen für die Befehle an.|
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Optional. Ermöglicht einem VSPackage, optional eine eigene Version der Funktionalität zu implementieren, die ursprünglich von anderen VSPackages unterstützt wird.|
|[Symbols-Element](https://www.microsoft.com/download/details.aspx?id=55984)|Optional. Enthält alle Symboldaten -- GUIDs, IDs usw. -- für den Compiler.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine||

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
