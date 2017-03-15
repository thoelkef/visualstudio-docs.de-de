---
title: "WriteOnly-Eigenschaften k&#246;nnen keinen Zugriffsmodifizierer f&#252;r &quot;Set&quot; haben. | Microsoft Docs"
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
  - "bc31104"
  - "vbc31104"
helpviewer_keywords: 
  - "BC31104"
ms.assetid: d1ac04a8-e436-4f3e-8d71-fc4569b35fcd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# WriteOnly-Eigenschaften k&#246;nnen keinen Zugriffsmodifizierer f&#252;r &quot;Set&quot; haben.
Eine `WriteOnly`\-Eigenschaftendeklaration gibt Zugriffsebenen sowohl in der [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) als auch in der [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) an.  
  
 Sie können immer eine Zugriffsebene für die Eigenschaft angeben. Darüber hinaus können Sie eine andere Zugriffsebene für höchstens eine der Eigenschaftenprozeduren \(`Get` oder `Set`\) angeben, sofern diese restriktiver als die Zugriffsebene der Eigenschaft ist. Sie können keine Zugriffsebenen für beide Eigenschaftenprozeduren angeben.  
  
 **Fehler\-ID:** BC31104  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Zugriffsmodifizierer aus der `Set`\-Anweisung. Er stellt die gesamte `WriteOnly`\-Eigenschaft dar, und Sie können nicht über zwei Zugriffsebenen für die Eigenschaft verfügen.  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)