---
title: Element (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
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
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56689506db04ee2aedd484093506db4a4fc7453d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520962"
---
# <a name="element-xelement-dynamic-property"></a>Element (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Element (dynamische XElement-Eigenschaft)](https://docs.microsoft.com/visualstudio/designers/element-xelement-dynamic-property).  
  
Ermittelt einen Indexer, der zum Abrufen der Instanz des untergeordneten Elements verwendet wird, die dem angegebenen erweiterten Namen entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Indexer des Typs `XElement Item(String expandedName)`. Dieser Indexer nimmt einen erweiterten Namensparameter und gibt das zugehörige <xref:System.Xml.Linq.XElement> oder, wenn kein Element mit dem angegebenen Namen existiert, `null` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XContainer.Element%2A>-Methode der <xref:System.Xml.Linq.XContainer?displayProperty=fullName>-Klasse.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Elemente](../designers/elements-xelement-dynamic-property.md)



