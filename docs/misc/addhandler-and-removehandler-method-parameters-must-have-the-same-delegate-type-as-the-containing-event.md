---
title: "AddHandler- und RemoveHandler-Methodenparameter m&#252;ssen den gleichen Delegattyp wie das enthaltende Ereignis aufweisen. | Microsoft Docs"
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
  - "bc31136"
  - "vbc31136"
helpviewer_keywords: 
  - "BC31136"
ms.assetid: 199b2f7b-a85e-465d-9853-0995156e7ab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# AddHandler- und RemoveHandler-Methodenparameter m&#252;ssen den gleichen Delegattyp wie das enthaltende Ereignis aufweisen.
Eine `Custom Event`\-Deklaration muss `AddHandler`\- oder `RemoveHandler`\-Deklarationen aufweisen, von denen jede einen einzelnen Parameter des Delegattyps übernimmt, der durch die `As`\-Klausel des benutzerdefinierten Ereignisses angegeben wird.  
  
 **Fehler\-ID:** BC31136  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Typ des Parameters so, dass er mit dem Delegattyp identisch ist, der durch die `As`\-Klausel des benutzerdefinierten Ereignisses angegeben ist.  
  
## Beispiel  
 Dieses Beispiel zeigt ein benutzerdefiniertes Ereignis mit den richtigen Parametertypen für die Deklarationen `AddHandler` und `RemoveHandler`.  
  
 [!code-vb[VbVbalrEventError#1](../misc/codesnippet/VisualBasic/addhandler-and-removehandler-method-parameters-must-have-the-same-delegate-type-as-the-containing-event_1.vb)]  
  
## Siehe auch  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- löschen](http://msdn.microsoft.com/de-de/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)