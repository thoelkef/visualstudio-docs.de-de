---
title: "Der Zugriffsmodifizierer kann entweder auf &#39;Get&#39; oder Set&#39; angewendet werden, aber nicht auf beide. | Microsoft Docs"
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
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Zugriffsmodifizierer kann entweder auf &#39;Get&#39; oder Set&#39; angewendet werden, aber nicht auf beide.
Eine Eigenschaftendeklaration gibt Zugriffsebenen sowohl in der [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement), [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) und der [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) an.  
  
 Sie können stets eine Zugriffsebene für die Eigenschaft angeben. Darüber hinaus können Sie eine andere Zugriffsebene für höchstens eine der Eigenschaftenprozeduren \(`Get` oder `Set`\) angeben, sofern diese restriktiver als die Zugriffsebene der Eigenschaft ist. Sie können keine Zugriffsebenen für beide Eigenschaftenprozeduren angeben.  
  
 **Fehler\-ID:** BC31101  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Zugriffsmodifizierer aus der `Get`\- oder `Set`\-Anweisung.  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)