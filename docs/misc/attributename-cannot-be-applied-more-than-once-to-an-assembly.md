---
title: "&quot;&lt;Attributname&gt;&quot; kann nicht mehrmals auf eine Assembly angewendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31521"
  - "vbc31521"
helpviewer_keywords: 
  - "BC31521"
ms.assetid: 7312570f-8afb-4afe-992f-b6f7796f5f26
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Attributname&gt;&quot; kann nicht mehrmals auf eine Assembly angewendet werden
Das angegebene Attribut kann nur einmal auf eine Assembly angewendet werden.  
  
 **Fehler\-ID:** BC31521  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie redundante Anwendungen dieses Attributs.  
  
2.  Wenn Sie ein benutzerdefiniertes Attribut verwenden, das Sie entwickelt haben, ändern Sie `AttributeUsageAttribute`, und legen Sie die `AllowMultiple`\-Eigenschaft auf `True` fest.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName>