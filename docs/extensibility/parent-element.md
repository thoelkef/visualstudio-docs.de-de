---
title: Übergeordnetes Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7220e435090cc688d32a2d6d26917a8c05510d4f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687912"
---
# <a name="parent-element"></a>Übergeordnetes Element
Das übergeordnete Element eines Felds Schaltfläche oder ein Kombinationsfeld kann nur eine Gruppe sein. Das übergeordnete Element eines Menü oder einer Gruppe kann einem anderen Menü oder einer Gruppe sein. In einem [CommandPlacement-Element](../extensibility/commandplacement-element.md), dieses Element ist erforderlich; in allen anderen Fällen ist er optional. Wenn dieses Element nicht angegeben ist, das übergeordnete Element des `Group_Undefined:0` wird abgeleitet werden.

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. GUID der GUID/ID Befehlsbezeichner.|
|id|Erforderlich. ID des GUID/ID Befehlsbezeichner.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CommandTable-element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle, die eine VSPackage bietet die integrierte Entwicklungsumgebung (IDE) darstellen. Beispielsweise Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern.|
|[Buttons-element](../extensibility/buttons-element.md)|Gruppen [Schaltflächenelement](../extensibility/button-element.md) Elemente.|
|[Menus-element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|
|[Groups-element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen eines VSPackage definieren.|

## <a name="see-also"></a>Siehe auch
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)