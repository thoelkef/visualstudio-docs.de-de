---
title: GuidSymbol-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe1d3b39e07862192082eb4950bd268dfcebd175
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863025"
---
# <a name="guidsymbol-element"></a>GuidSymbol-element
Die `GuidSymbol` Element enthält die GUID des das GUID: ID-Paar, das ein Menü, Gruppe oder den Befehl darstellt. Die ID stammt aus einer `IDSymbol` Element in der `GuidSymbol` Element. Die `GuidSymbol` Element verfügt über eine `name` -Attribut, das einen Anzeigenamen für die GUID, der in enthalten ist, enthält die `value` Attribut.

## <a name="syntax"></a>Syntax

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|Name|Erforderlich. Der Name des dem GUID-Symbol.|
|Wert|Erforderlich. GUID der GUID-Symbol.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[IDSymbol-element](../extensibility/idsymbol-element.md)|Enthält die ID der dem GUID: ID-Paar, die ein Menü, Gruppe oder den Befehl darstellt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Symbols-element](../extensibility/symbols-element.md)|Gruppen `GuidSymbol` Elemente in einem *VSCT* Datei.|

## <a name="remarks"></a>Hinweise
 In der Regel eine *VSCT* -Datei enthält drei `GuidSymbol` Elemente in der `Symbols` Abschnitt, der für das Paket selbst, der für den Befehlssatz (die Sammlung von Menüs, Gruppen und Befehle, die das Paket zur Verfügung stellt), und eine für die Bitmaps, die Symbole für die Schaltflächen und anderen visuellen Komponenten bereitstellen. Jede `IDSymbol` Element in einer angegebenen `GuidSymbol` -Element muss einen eindeutigen besitzen `value`. Allerdings `IDSymbol` Elemente, die identische Werte aufweisen können in einem Paket vorhanden, solange sie die verschiedene übergeordneten Elementen verfügen.

## <a name="see-also"></a>Siehe auch
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)