---
title: Idsymbol-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710374"
---
# <a name="idsymbol-element"></a>Idsymbol-Element
Das- `IDSymbol` Element enthält die ID des GUID: ID-Paars, das ein Menü, eine Gruppe oder einen Befehl darstellt. Die GUID stammt aus dem übergeordneten `GuidSymbol` Element. Das- `IDSymbol` Element verfügt über ein- `name` Attribut, das einen anzeigen Amen für die ID bereitstellt, die im-Attribut enthalten ist `value` .

## <a name="syntax"></a>Syntax

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|name|Erforderlich. Name des ID-Symbols.|
|value|Erforderlich. Numerischer ID-Wert des ID-Symbols.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Guidsymbol-Element](../extensibility/guidsymbol-element.md)|Enthält die GUID des GUID: ID-Paars, das ein Menü, eine Gruppe oder einen Befehl darstellt. Gruppiert `IDSymbol`-Elemente.|

## <a name="remarks"></a>Bemerkungen
 Jedes `IDSymbol` Element in einem bestimmten `GuidSymbol` Element muss über einen eindeutigen verfügen `value` . Allerdings `IDSymbol` können Elemente mit identischen Werten in einem Paket vorhanden sein, solange Sie über unterschiedliche übergeordnete Elemente verfügen.

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
