---
title: Elemente (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664690"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sucht nach einem Indexer, der zum Abrufen der untergeordneten Elemente des aktuellen Elements verwendet wird, die dem angegebenen erweiterten Namen entsprechen.

## <a name="syntax"></a>Syntax

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert
 Indexer des Typs `IEnumerable<XElement> Item(String expandedName)`. Dieser Indexer nimmt den erweiterten Namen des gewünschten untergeordneten Elements und gibt die passenden untergeordneten Elemente in einer <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`-Auflistung zurück.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName>-Methode der <xref:System.Xml.Linq.XContainer>-Klasse.

 Die Elemente in der zurückgegebenen Auflistung sind in derselben Reihenfolge aufgeführt wie im XML-Quelldokument.

 Diese Eigenschaft verwendet die verzögerte Ausführung.

## <a name="see-also"></a>Siehe auch
 [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md), [Element](../designers/element-xelement-dynamic-property.md) [Nachfolger](../designers/descendants-xelement-dynamic-property.md)
