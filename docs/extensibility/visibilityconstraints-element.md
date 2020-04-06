---
title: VisibilityConstraints-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698194"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints-Element
Das VisibilityConstraints-Element bestimmt die statische Sichtbarkeit von Befehls- und Symbolleistengruppen. Die Sichtbarkeit wird zunächst [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] durch die integrierte Entwicklungsumgebung (IDE) gesteuert, ohne das VSPackage zu laden.

## <a name="syntax"></a>Syntax

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
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
|[VisibilityItem-Element](../extensibility/visibilityitem-element.md)|Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Bestimmt die statische Sichtbarkeit von Befehlsgruppen und Symbolleistengruppen.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die die Befehle darstellen (z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder), die ein VSPackage für die IDE bereitstellt.|

## <a name="example"></a>Beispiel

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Weitere Informationen
- [VisibilityItem-Element](../extensibility/visibilityitem-element.md)
- [Visual Studio-Befehlstabelle (. Vsct)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
