---
title: Externes Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711485"
---
# <a name="extern-element"></a>Externes Element
Das Extern-Element verweist auf alle externen Headerdateien (*.h*), um zur Kompilierungszeit mit der *.vsct-Datei* zusammenzuführen. Die zusammenzugeführten Dateien müssen sich auf dem Include-Pfad befinden, der dem VSCT-Compiler gegeben ist oder auf den von einem [Include-Element](../extensibility/include-element.md)verwiesen wird. Bei den Dateien kann es sich um andere *.vsct-Dateien* oder C++-Headerdateien handelt.

 Definitionen in Headerdateien müssen die Form "#define [Symbol] [Wert]" haben. Definitionen können in bedingten Anweisungen von Befehlselementen verwendet werden. Jedes Symbol, das nicht tatsächlich verwendet wird, wird verworfen.

 CommandTable Element Extern Element

## <a name="syntax"></a>Syntax

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|href|Erforderlich. Der Pfad zur Headerdatei:<br /><br /> href="stdidcmd.h"|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Optional. Die Standardsprache [ \<](../extensibility/strings-element.md) aller Strings>Elemente in der Befehlstabelle:<br /><br /> language="en-uns"|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine.|Keine.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen, d. h. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder, die ein VSPackage für die IDE bereitstellt.|

## <a name="example"></a>Beispiel

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
