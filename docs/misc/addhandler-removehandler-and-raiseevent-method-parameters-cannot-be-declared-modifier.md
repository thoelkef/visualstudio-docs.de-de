---
title: "Die &quot;AddHandler&quot;-, &quot;RemoveHandler&quot;- und &quot;RaiseEvent&quot;-Methodenparameter k&#246;nnen nicht als &quot;&lt;Modifizierer&gt;&quot; deklariert werden | Microsoft Docs"
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
  - "vbc31138"
  - "bc31138"
helpviewer_keywords: 
  - "BC31138"
ms.assetid: 6d8df92a-95fc-4a7d-ab1e-06d312155c55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &quot;AddHandler&quot;-, &quot;RemoveHandler&quot;- und &quot;RaiseEvent&quot;-Methodenparameter k&#246;nnen nicht als &quot;&lt;Modifizierer&gt;&quot; deklariert werden
Die Parameter der Methoden `AddHandler`, `RemoveHandler` und `RaiseEvent` können nicht mit dem Modifizierer `Optional` oder `ParamArray` deklariert werden.  
  
 Die Modifizierer `Optional` und `ParamArray` sind nur bei Parametern in den Deklarationen `Declare`, `Function`, `Property` und `Sub` zulässig.  
  
 **Fehler\-ID:** BC31138  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Optional`\- oder `ParamArray`\-Schlüsselwort aus der Parameterliste.  
  
## Siehe auch  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- löschen](http://msdn.microsoft.com/de-de/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- löschen](http://msdn.microsoft.com/de-de/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)