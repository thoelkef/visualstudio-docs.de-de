---
title: Elemente (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75cb7f8f6a5259151679ecee84bbeb5db336782f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511812"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Elemente (dynamische XElement-Eigenschaft)](https://docs.microsoft.com/visualstudio/designers/elements-xelement-dynamic-property).  
  
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
 [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Element](../designers/element-xelement-dynamic-property.md)   
 [Descendants](../designers/descendants-xelement-dynamic-property.md)



