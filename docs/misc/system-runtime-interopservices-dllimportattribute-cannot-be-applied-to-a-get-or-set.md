---
title: "&quot;System.Runtime.InteropServices.DllImportAttribute&quot; kann nicht auf &quot;Get&quot; oder &quot;Set&quot; angewendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31524"
  - "bc31524"
helpviewer_keywords: 
  - "BC31524"
ms.assetid: 3603e33a-a80b-448d-83e0-e5dbc9af4dcf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;System.Runtime.InteropServices.DllImportAttribute&quot; kann nicht auf &quot;Get&quot; oder &quot;Set&quot; angewendet werden
Das `DllImportAttribute`\-Attribut wurde auf eine `Get`\- oder `Set`\-Eigenschaftenprozedur angewendet.  
  
 **Fehler\-ID:** BC31524  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie `DllImportAttribute` aus `Get`\- und `Set`\-Eigenschaftenprozeduren.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)