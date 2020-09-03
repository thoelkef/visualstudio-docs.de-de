---
title: Element (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c6171a5dedfd6985a6f54e748011bf86e03f4d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664649"
---
# <a name="element-xelement-dynamic-property"></a>Element (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ermittelt einen Indexer, der zum Abrufen der Instanz des untergeordneten Elements verwendet wird, die dem angegebenen erweiterten Namen entspricht.

## <a name="syntax"></a>Syntax

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert
 Indexer des Typs `XElement Item(String expandedName)`. Dieser Indexer nimmt einen erweiterten Namensparameter und gibt das zugehörige <xref:System.Xml.Linq.XElement> oder, wenn kein Element mit dem angegebenen Namen existiert, `null` zurück.

## <a name="remarks"></a>Bemerkungen
 Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XContainer.Element%2A>-Methode der <xref:System.Xml.Linq.XContainer?displayProperty=fullName>-Klasse.

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>[Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md) [Elements](../designers/elements-xelement-dynamic-property.md)
