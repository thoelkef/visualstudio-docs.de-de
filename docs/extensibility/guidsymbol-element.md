---
title: GuidSymbol Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711125"
---
# <a name="guidsymbol-element"></a>GuidSymbol-Element
Das `GuidSymbol` Element enthält die GUID des GUID:ID-Paares, das ein Menü, eine Gruppe oder einen Befehl darstellt. Die ID stammt `IDSymbol` von `GuidSymbol` einem Element im Element. Das `GuidSymbol` Element `name` verfügt über ein Attribut, das einen Anzeigenamen `value` für die GUID bereitstellt, der im Attribut enthalten ist.

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

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|name|Erforderlich. Name des GUID-Symbols.|
|value|Erforderlich. GUID des GUID-Symbols.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[IDSymbol-Element](../extensibility/idsymbol-element.md)|Enthält die ID des GUID:ID-Paares, das ein Menü, eine Gruppe oder einen Befehl darstellt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Symbols-Element](../extensibility/symbols-element.md)|Gruppiert `GuidSymbol` Elemente in einer *.vsct-Datei.*|

## <a name="remarks"></a>Bemerkungen
 In der Regel enthält eine `GuidSymbol` `Symbols` *.vsct-Datei* drei Elemente in ihrem Abschnitt, eines für das Paket selbst, eines für den Befehlssatz (die Sammlung von Menüs, Gruppen und Befehlen, die das Paket zur Verfügung stellt) und eines für die Bitmaps, die Symbole für Schaltflächen und andere visuelle Komponenten bereitstellen. Jedes `IDSymbol` Element in `GuidSymbol` einem bestimmten `value`Element muss über eine eindeutige verfügen. Elemente `IDSymbol` mit identischen Werten können jedoch in einem Paket vorhanden sein, solange sie unterschiedliche Eltern haben.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
