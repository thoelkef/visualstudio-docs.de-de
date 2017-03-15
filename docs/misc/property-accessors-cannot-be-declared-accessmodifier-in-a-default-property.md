---
title: "Eigenschaftenaccessoren k&#246;nnen in einer &#39;Default&#39;-Eigenschaft nicht als &#39;&lt;Zugriffsmodifizierer&gt;&#39; deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eigenschaftenaccessoren k&#246;nnen in einer &#39;Default&#39;-Eigenschaft nicht als &#39;&lt;Zugriffsmodifizierer&gt;&#39; deklariert werden.
Eine [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) oder [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) in einer Standardeigenschaft enthält das `Private`\-Schlüsselwort.  
  
 Eine Standardeigenschaft kann nicht `Private` sein, und dasselbe gilt für ihre einzelnen Eigenschaftenprozeduren \(`Get` oder `Set`\).  
  
 **Fehler\-ID:** BC31107  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Private`\-Schlüsselwort aus der `Get`\- oder `Set`\-Anweisung, oder entfernen Sie `Default` aus der [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement).  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)