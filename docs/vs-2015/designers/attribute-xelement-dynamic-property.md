---
title: Attribute (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 750e84a386360880cf30e76fc0157145820c654c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512790"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Attribute (dynamische XElement-Eigenschaft)](https://docs.microsoft.com/visualstudio/designers/attribute-xelement-dynamic-property).  
  
Sucht nach einem Indexer, der zum Abrufen der Attributinstanz verwendet wird, die dem angegebenen erweiterten Namen entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Indexer des Typs `XAttribute Item(String expandedName)`. Dieser Indexer nimmt den erweiterten Namen des angegebenen Attributs und gibt das zugehörige <xref:System.Xml.Linq.XAttribute> zurück. Wenn kein Attribut mit dem angegebenen Namen existiert, wird `null` zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XElement.Attribute%2A>-Methode der <xref:System.Xml.Linq.XElement?displayProperty=fullName>-Klasse.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Wert](../designers/value-xattribute-dynamic-property.md)



