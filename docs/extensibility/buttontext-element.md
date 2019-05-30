---
title: ButtonText-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe2440258e95ad0d61998b24dae54b731a998c47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321212"
---
# <a name="buttontext-element"></a>ButtonText-element
Dieses Feld ermöglicht die Angabe der Text erscheint in verschiedenen Menüs. In der Standardeinstellung die `ButtonText` Element wird im Menücontroller angezeigt. Die `ButtonText` Element wird auch die Standardeinstellung, wenn die anderen Textfelder leer sind. Die `ButtonText` Element darf nicht leer sein, auch wenn die anderen Textfelder angegeben werden.

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
|[Strings-Element](../extensibility/strings-element.md)|Text-Elemente, wie z. B. gruppiert `ButtonText` und `CommandName`.|

## <a name="text-value"></a>Textwert
 Der Textwert, der die `ButtonText` -Element stellt den Text, der angezeigt wird, für Menüelemente, Combos und andere Elemente der Benutzeroberfläche (UI), die sichtbaren Text bereit.

## <a name="see-also"></a>Siehe auch
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)