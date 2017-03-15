---
title: "&#39;&lt;Typname&gt;&#39; kann nicht von einem in ihr bzw. ihm geschachtelten Typ erben. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30908"
  - "vbc30908"
helpviewer_keywords: 
  - "BC30908"
ms.assetid: bca164b2-a4a9-4ed4-9f71-a9a5a42f181a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Typname&gt;&#39; kann nicht von einem in ihr bzw. ihm geschachtelten Typ erben.
Die Definition einer Klasse oder Schnittstelle enthält eine [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement), die einen Typ angibt, der in ihr geschachtelt ist.  
  
 Die Vererbung muss linear verlaufen, nicht kreisförmig. Ein Typ kann nicht von einem Typ erben, der wiederum von ihm selbst erbt.  
  
 Eine verwandte Einschränkung ist, dass ein Typ nicht von einem Typ erben kann, der noch nicht definiert wurde. Ein Merkmal von Vererbung ist die Fähigkeit, Member der Basisklasse wiederzuverwenden. Dies setzt wiederum voraus, dass diese Member definiert sind. Aus diesem Grund kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keinen Code wie im folgenden Beispiel kompilieren.  
  
```  
Public Class outerClass ' The following statement is INVALID because innerClass is not defined. Inherits innerClass Public Class innerClass Public Sub doSomething() End Sub End Class End Class  
```  
  
 **Fehler\-ID:** BC30908  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der erbende Typ \(der äußere Typ in der Schachtelung\) vom inneren Typ erben muss, verschieben Sie den inneren Typs außerhalb des äußeren Typs.  
  
-   Wenn der innere Typ im äußeren Typ geschachtelt sein muss, kann der äußere Typ nicht von ihm erben. Entfernen Sie die [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement).  
  
## Siehe auch  
 [NICHT IM BUILD: Vererbung in Visual Basic](http://msdn.microsoft.com/de-de/e5e6e240-ed31-4657-820c-079b7c79313c)