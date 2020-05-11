---
title: ButtonText-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739904"
---
# <a name="buttontext-element"></a>ButtonText-Element
Mit diesem Feld können Sie den Text angeben, der in verschiedenen Menüs angezeigt wird. Standardmäßig wird `ButtonText` das Element in Menücontrollern angezeigt. Das `ButtonText` Element wird auch zum Standardwert, wenn die anderen Textfelder leer sind. Das `ButtonText` Element darf auch dann nicht leer sein, wenn die anderen Textfelder angegeben sind.

## <a name="syntax"></a>Syntax

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Strings-Element](../extensibility/strings-element.md)|Gruppiert Textelemente, `ButtonText` z. B. und `CommandName`.|

## <a name="text-value"></a>Textwert
 Der Textwert `ButtonText` des Elements stellt den Text bereit, der für Menüelemente, Kombinationen und andere Benutzeroberflächenelemente mit sichtbarem Text angezeigt wird.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
