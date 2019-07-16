---
title: Include-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7287f4e8b611f55ea28e648aec3f95d1407bf07e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350099"
---
# <a name="include-element"></a>Include-element
Das Include-Element gibt eine Datei, die gefunden werden, kann für die angegebenen Includepfad für das Einfügen in die aktuelle Datei.  Alle Symbole und Typen, die definiert, werden Teil des kompilierten Ergebnisses.

## <a name="syntax"></a>Syntax

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|href|Erforderlich. Der Pfad zur Headerdatei:<br /><br /> href="stdidcmd.h"|
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Keine|Keine|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CommandTable-element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen, d. h. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern –, die eine VSPackage für die IDE bietet.|

## <a name="example"></a>Beispiel

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Siehe auch
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)