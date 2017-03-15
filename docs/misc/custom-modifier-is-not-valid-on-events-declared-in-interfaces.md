---
title: "Der Custom-Modifizierer ist f&#252;r Ereignisse, die in Schnittstellen deklariert sind, nicht g&#252;ltig. | Microsoft Docs"
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
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Custom-Modifizierer ist f&#252;r Ereignisse, die in Schnittstellen deklariert sind, nicht g&#252;ltig.
Ein benutzerdefiniertes Ereignis kann nicht in einer Schnittstelle deklariert werden, da ein benutzerdefiniertes Ereignis eine Implementierung seiner `AddHandler`\-, `RemoverHandler`\- und `RaiseEvent`\-Methoden bereitstellen muss.  
  
 Das `Custom`\-Schlüsselwort kann in einer abgeleiteten Klasse verwendet werden, die das Ereignis implementiert.  
  
 **Fehler\-ID:** BC31121  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Custom`\-Schlüsselwort aus der Ereignisdeklaration in der Schnittstelle.  
  
## Beispiel  
 In diesem Beispiel wird veranschaulicht, wie ein in einer Schnittstelle deklariertes Ereignis als benutzerdefiniertes Ereignis implementiert wird.  
  
 [!code-vb[VbVbalrEventError#3](../misc/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-in-interfaces_1.vb)]  
  
## Siehe auch  
 [Benutzerdefiniert – Löschen](http://msdn.microsoft.com/de-de/dc62be07-c896-4866-a533-982a661d143f)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)