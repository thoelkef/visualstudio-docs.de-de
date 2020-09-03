---
title: Übergeordnetes Element | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702220"
---
# <a name="parent-element"></a>Übergeordnetes Element
Das übergeordnete Element einer Schaltfläche oder eines Kombinations Felds darf nur eine Gruppe sein. Das übergeordnete Element eines Menüs oder einer Gruppe kann ein beliebiges anderes Menü oder eine andere Gruppe sein. In einem [commandplacement-Element](../extensibility/commandplacement-element.md)ist dieses Element erforderlich. in allen anderen Instanzen ist es optional. Wenn dieses Element weggelassen wird, wird das übergeordnete Element von `Group_Undefined:0` impliziert.

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. GUID des Befehls Bezeichners GUID/ID.|
|id|Erforderlich. ID des Befehls Bezeichners GUID/ID.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen, die ein VSPackage für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) bereitstellt. Beispielsweise Menü Elemente, Menüs, Symbolleisten und Kombinations Felder.|
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppiert [Schaltflächen Element](../extensibility/button-element.md) -Elemente.|
|[Menüs-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die von einem VSPackage implementiert werden.|
|[Groups-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehls Gruppen eines VSPackage definieren.|

## <a name="see-also"></a>Siehe auch
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
