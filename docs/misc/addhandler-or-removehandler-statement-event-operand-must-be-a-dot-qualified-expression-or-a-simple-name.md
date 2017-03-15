---
title: "Der AddHandler- oder RemoveHandler-Anweisungsereignisoperand muss ein punktqualifizierter Ausdruck oder ein einfacher Name sein. | Microsoft Docs"
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
  - "vbc30677"
  - "bc30677"
helpviewer_keywords: 
  - "BC30677"
ms.assetid: b71eb2f0-0bb2-4aeb-94ec-5c37ab960d9e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der AddHandler- oder RemoveHandler-Anweisungsereignisoperand muss ein punktqualifizierter Ausdruck oder ein einfacher Name sein.
Das für das Ereignisargument für `AddHandler` oder `RemoveHandler` angegebene Element wurde nicht als Ereignis erkannt.  
  
 **Fehler\-ID:** BC30677  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie den Namen des Objekts, das das Ereignis auslöst, gefolgt von einem Punkt \(`.`\) und den Ereignisnamen wie im folgenden Beispiel an.  
  
     [!code-vb[VbVbalrEventError#30](../misc/codesnippet/VisualBasic/addhandler-or-removehandler-statement-event-operand-must-be-a-dot-qualified-expression-or-a-simple-name_1.vb)]  
  
## Siehe auch  
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [RemoveHandler Statement](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [NICHT IM BUILD: AddHandler und RemoveHandler](http://msdn.microsoft.com/de-de/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)