---
title: "&#39;Implements&#39; ist f&#252;r Operatordeklarationen nicht g&#252;ltig. | Microsoft Docs"
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
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; ist f&#252;r Operatordeklarationen nicht g&#252;ltig.
In einer [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) ist das Schlüsselwort [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) angegeben.  
  
 Nur eine `Function`\- oder `Sub`\-Prozedur, eine Eigenschaft oder ein Ereignis kann einen Schnittstellenmember implementieren. Weitere Informationen zur Implementierung finden Sie unter [NICHT IM BUILD: Beispiele für die Schnittstellenimplementierung in Visual Basic](http://msdn.microsoft.com/de-de/50bf2a30-73b6-4126-a921-075fd6eec278).  
  
 Eine `Operator`\-Prozedur erfordert sowohl das Schlüsselwort `Public` als auch das Schlüsselwort `Shared`, und ein Konvertierungsoperator erfordert entweder das Schlüsselwort `Widening` oder das Schlüsselwort `Narrowing`. Weitere Informationen finden Sie unter [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **Fehler\-ID:** BC33004  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie in dieser Prozedur einen Schnittstellenmember implementieren möchten, schreiben Sie sie als `Function`\- oder `Sub`\-Prozedur, als Eigenschaft oder als Ereignis neu.  
  
-   Wenn diese Prozedur einen Operator definieren soll, entfernen Sie das `Implements`\-Schlüsselwort aus der Deklaration.  
  
## Siehe auch  
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)