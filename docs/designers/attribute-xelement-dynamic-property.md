---
title: Attribute (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e3f373f4732aa80ac0e72f044e7a6a7f08e8a9be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (dynamische XElement-Eigenschaft)
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