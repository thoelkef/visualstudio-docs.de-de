---
title: "Das Attribut &#39;&lt;Attributname&gt;&#39; kann nicht auf eine Assembly angewendet werden. | Microsoft Docs"
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
  - "bc30548"
  - "vbc30548"
helpviewer_keywords: 
  - "BC30548"
ms.assetid: bc36f094-626a-4907-b80b-f195155fa5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Attribut &#39;&lt;Attributname&gt;&#39; kann nicht auf eine Assembly angewendet werden.
Sie haben versucht, ein Attribut auf eine Assembly anzuwenden, deren `AttributeUsageAttribute` kein `AttributeTargets.Assembly` angibt. Das Attribut wurde beim Deklarieren nicht für die Anwendung auf eine Assembly definiert.  
  
 **Fehler\-ID:** BC30548  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Attributdeklaration, und geben Sie `AttributeTargets.Assembly` oder `AttributeTargets.All` an.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>