---
title: Übergeordnetes Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702220"
---
# <a name="parent-element"></a>Übergeordnetes Element
Das übergeordnete Element einer Schaltfläche oder eines Kombinationsfelds darf nur eine Gruppe sein. Das übergeordnete Element eines Menüs oder einer Gruppe kann ein anderes Menü oder eine andere Gruppe sein. In einem [CommandPlacement-Element](../extensibility/commandplacement-element.md)ist dieses Element erforderlich. in allen anderen Instanzen ist es optional. Wenn dieses Element weggelassen `Group_Undefined:0` wird, wird das übergeordnete Element von impliziert.

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. GUID des GUID/ID-Befehlsbezeichners.|
|id|Erforderlich. ID des GUID/ID-Befehlsbezeichners.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen, die ein VSPackage für die integrierte Entwicklungsumgebung (IDE) bereitstellt. Beispielsweise Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.|
|[Buttons-Element](../extensibility/buttons-element.md)|[Gruppen-Schaltflächenelementelemente.](../extensibility/button-element.md)|
|[Menus-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|
|[Gruppenelement](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen eines VSPackage definieren.|

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
