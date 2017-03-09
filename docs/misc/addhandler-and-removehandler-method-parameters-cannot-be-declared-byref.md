---
title: "Die Methodenparameter &#39;AddHandler&#39; und &#39;RemoveHandler&#39; k&#246;nnen nicht &#39;ByRef&#39; deklariert werden. | Microsoft Docs"
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
  - "vbc31134"
  - "bc31134"
helpviewer_keywords: 
  - "BC31134"
ms.assetid: 942f0b91-e71a-499a-ad10-a5dfcb4e72b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Methodenparameter &#39;AddHandler&#39; und &#39;RemoveHandler&#39; k&#246;nnen nicht &#39;ByRef&#39; deklariert werden.
Die Parameter der `AddHandler`\- und der `RemoveHandler`\-Methode können nicht mit dem `ByRef`\-Modifizierer deklariert werden.  
  
 **Fehler\-ID:** BC31134  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `ByRef`\-Schlüsselwort aus der Anweisung.  
  
## Siehe auch  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler – löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler – löschen](http://msdn.microsoft.com/de-de/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)