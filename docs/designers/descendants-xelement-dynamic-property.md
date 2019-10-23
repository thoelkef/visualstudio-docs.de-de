---
title: Descendants (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fab6b90489624955ddd567492d12f54d8de2686f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637343"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (dynamische XElement-Eigenschaft)

Sucht nach einem Indexer, der zum Abrufen aller Nachfolgerelemente des aktuellen Elements verwendet wird, die dem angegebenen erweiterten Namen entsprechen.

## <a name="syntax"></a>Syntax

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Indexer des Typs `IEnumerable<XElement> Item(String expandedName)`. Dieser Indexer nimmt den erweiterten Namen der angegebenen Nachfolgerelemente und gibt die passenden untergeordneten Elemente in einer <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`-Auflistung zurück.

## <a name="remarks"></a>Anmerkungen

Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName>-Methode der <xref:System.Xml.Linq.XContainer>-Klasse.

Die Elemente in der zurückgegebenen Auflistung sind in derselben Reihenfolge aufgeführt wie im XML-Quelldokument.

Diese Eigenschaft verwendet die verzögerte Ausführung.

## <a name="see-also"></a>Siehe auch

- [Dynamische Eigenschaften der XElement-Klasse](../designers/attribute-xelement-dynamic-property.md)
- [Elemente](../designers/elements-xelement-dynamic-property.md)