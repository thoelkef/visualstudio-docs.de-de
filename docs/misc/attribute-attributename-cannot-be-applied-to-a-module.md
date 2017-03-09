---
title: "Das Attribut &#39;&lt;Attributname&gt;&#39; kann nicht auf ein Modul angewendet werden. | Microsoft Docs"
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
  - "vbc30549"
  - "bc30549"
helpviewer_keywords: 
  - "BC30549"
ms.assetid: b38fea31-6b0b-4c54-9518-b59226505802
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Attribut &#39;&lt;Attributname&gt;&#39; kann nicht auf ein Modul angewendet werden.
Sie haben versucht, ein Attribut auf ein Modul anzuwenden, dessen `AttributeUsageAttribute` kein `AttributeTargets.Module` angibt. Das Attribut wurde beim Deklarieren nicht für die Anwendung auf ein Modul definiert.  
  
 **Fehler\-ID:** BC30549  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Attributdeklaration, und geben Sie `AttributeTargets.Module`oder`AttributeTargets.All` an.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>