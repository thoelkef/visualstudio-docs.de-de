---
title: "Eine Return-Anweisung in einer AddHandler-, RemoveHandler- oder RaiseEvent-Methode kann keinen Wert zur&#252;ckgeben. | Microsoft Docs"
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
  - "bc30940"
  - "vbc30940"
helpviewer_keywords: 
  - "BC30940"
ms.assetid: 0e4d037a-2d20-40e4-8ead-6d709d1c9c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Return-Anweisung in einer AddHandler-, RemoveHandler- oder RaiseEvent-Methode kann keinen Wert zur&#252;ckgeben.
Die `AddHandler`\-, `RemoveHandler`\- und `RaiseEvent`\-Methode in einer `Custom Event`\-Deklaration kann `Return`\-Anweisungen enthalten, um die Methoden zu beenden. Allerdings kann die `Return`\-Anweisung kann keinen Rückgabewert angeben, da die Methoden keine Werte zurückgeben können.  
  
 **Fehler\-ID:** BC30940  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Ausdruck nach der `Return`\-Anweisung.  
  
## Siehe auch  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- löschen](http://msdn.microsoft.com/de-de/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- löschen](http://msdn.microsoft.com/de-de/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)