---
title: "Die Anweisung deklariert keine AddHandler-, RemoveHandler- oder RaiseEvent-Methode. | Microsoft Docs"
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
  - "vbc31113"
  - "bc31113"
helpviewer_keywords: 
  - "BC31113"
ms.assetid: f8299c9d-6030-43e5-878e-8d2b042191b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Anweisung deklariert keine AddHandler-, RemoveHandler- oder RaiseEvent-Methode.
Die Anweisung gibt keine `AddHandler`, `RemoveHandler`\- oder `RaiseEvent`\-Deklarationsanweisung in Verbindung mit einer `Custom Event`\-Prozedur bereit. Eine benutzerdefinierte Ereignisdeklaration wird als Codeblock definiert, der von den Anweisungen `Custom Event` und `End Event` eingefasst wird. Innerhalb dieses Blocks erscheint jede `Custom Event`\-Prozedur als interner Block, der von einer Deklarationsanweisung und einer `End`\-Anweisung eingefasst wird.  
  
 **Fehler\-ID:** BC31113  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie eine `AddHandler`\-, `RemoveHandler`\- oder `RaiseEvent`\-Deklarationsanweisung bereit.  
  
## Siehe auch  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- löschen](http://msdn.microsoft.com/de-de/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- löschen](http://msdn.microsoft.com/de-de/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)