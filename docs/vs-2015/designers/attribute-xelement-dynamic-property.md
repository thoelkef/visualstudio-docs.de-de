---
title: Attribute (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ced05b8da63f9a7a242b166fe64e9e44f78b8065
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776244"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
