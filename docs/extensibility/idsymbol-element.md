---
title: IDSymbol-Element | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710374"
---
# <a name="idsymbol-element"></a>IDSymbol-Element
Das `IDSymbol` Element enthält die ID des GUID:ID-Paares, das ein Menü, eine Gruppe oder einen Befehl darstellt. Die GUID stammt `GuidSymbol` vom übergeordneten Element. Das `IDSymbol` Element `name` verfügt über ein Attribut, das einen Anzeigenamen `value` für die ID bereitstellt, der im Attribut enthalten ist.

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
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[GuidSymbol-Element](../extensibility/guidsymbol-element.md)|Enthält die GUID des GUID:ID-Paares, das ein Menü, eine Gruppe oder einen Befehl darstellt. Gruppiert `IDSymbol`-Elemente.|

## <a name="remarks"></a>Bemerkungen
 Jedes `IDSymbol` Element in `GuidSymbol` einem bestimmten `value`Element muss über eine eindeutige verfügen. Elemente `IDSymbol` mit identischen Werten können jedoch in einem Paket vorhanden sein, solange sie unterschiedliche Eltern haben.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
