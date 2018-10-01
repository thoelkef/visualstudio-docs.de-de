---
title: Xml (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
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
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74fdfa59e791fb8e0262df04b1e45f3b867fbd02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513357"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Xml (dynamische XElement-Eigenschaft)](https://docs.microsoft.com/visualstudio/designers/xml-xelement-dynamic-property).  
  
Ruft den unformatierten XML-Inhalt des Elements ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 <xref:System.String>, die den unformatierten XML-Inhalt des Elements darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29>-Methode der <xref:System.Xml.Linq.XNode?displayProperty=fullName>-Klasse, wobei der `SaveOptions`-Parameter auf <xref:System.Xml.Linq.SaveOptions> festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Wert](../designers/value-xelement-dynamic-property.md)



