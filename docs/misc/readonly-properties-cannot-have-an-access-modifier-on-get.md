---
title: "ReadOnly-Eigenschaften k&#246;nnen keinen Zugriffsmodifizierer f&#252;r &quot;Get&quot; haben. | Microsoft Docs"
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
  - "vbc31105"
  - "bc31105"
helpviewer_keywords: 
  - "BC31105"
ms.assetid: 54066d8e-eb22-4b99-bb18-45afe61d3b33
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReadOnly-Eigenschaften k&#246;nnen keinen Zugriffsmodifizierer f&#252;r &quot;Get&quot; haben.
Eine `ReadOnly`\-Eigenschaftendeklaration gibt Zugriffsebenen sowohl in der [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) als auch in der [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) an.  
  
 Sie können immer eine Zugriffsebene für die Eigenschaft angeben. Darüber hinaus können Sie eine andere Zugriffsebene für höchstens eine der Eigenschaftenprozeduren \(`Get` oder `Set`\) angeben, sofern diese restriktiver als die Zugriffsebene der Eigenschaft ist. Sie können keine Zugriffsebenen für beide Eigenschaftenprozeduren angeben.  
  
 **Fehler\-ID:** BC31105  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Zugriffsmodifizierer aus der `Get`\-Anweisung. Er stellt die gesamte `ReadOnly`\-Eigenschaft dar, und Sie können nicht über zwei Zugriffsebenen für die Eigenschaft verfügen.  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)