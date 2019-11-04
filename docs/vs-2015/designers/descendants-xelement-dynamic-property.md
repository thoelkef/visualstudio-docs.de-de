---
title: Descendants (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b0496a04219c88573b3b555ef879a046d90faa3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664781"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sucht nach einem Indexer, der zum Abrufen aller Nachfolgerelemente des aktuellen Elements verwendet wird, die dem angegebenen erweiterten Namen entsprechen.

## <a name="syntax"></a>Syntax

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert
 Indexer des Typs `IEnumerable<XElement> Item(String expandedName)`. Dieser Indexer nimmt den erweiterten Namen der angegebenen Nachfolgerelemente und gibt die passenden untergeordneten Elemente in einer <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`-Auflistung zurück.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName>-Methode der <xref:System.Xml.Linq.XContainer>-Klasse.

 Die Elemente in der zurückgegebenen Auflistung sind in derselben Reihenfolge aufgeführt wie im XML-Quelldokument.

 Diese Eigenschaft verwendet die verzögerte Ausführung.

## <a name="see-also"></a>Siehe auch
 [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md) [Elemente](../designers/elements-xelement-dynamic-property.md)
