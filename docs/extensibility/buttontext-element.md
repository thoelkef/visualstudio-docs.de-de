---
title: ButtonText-Element | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739904"
---
# <a name="buttontext-element"></a>ButtonText-Element
In diesem Feld können Sie den Text angeben, der in verschiedenen Menüs angezeigt wird. Standardmäßig wird das- `ButtonText` Element in Menü Controllern angezeigt. Das- `ButtonText` Element wird auch der Standardwert, wenn die anderen Textfelder leer sind. Das `ButtonText` Element darf nicht leer sein, auch wenn die anderen Textfelder angegeben werden.

## <a name="syntax"></a>Syntax

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Strings-Element](../extensibility/strings-element.md)|Gruppiert Textelemente, wie z `ButtonText` `CommandName` . b. und.|

## <a name="text-value"></a>Textwert
 Der Textwert des- `ButtonText` Elements stellt den Text bereit, der für Menü Elemente, Combos und andere Benutzeroberflächen Elemente (UI) angezeigt wird, die über sichtbaren Text verfügen.

## <a name="see-also"></a>Siehe auch
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
