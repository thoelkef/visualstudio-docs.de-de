---
title: "„System.ObsoleteAttribute“ kann nicht auf die Definitionen „AddHandler“, „RemoveHandler“ oder „RaiseEvent“ angewendet werden. | Microsoft Docs"
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
  - "bc31142"
  - "vbc31142"
helpviewer_keywords: 
  - "BC31142"
ms.assetid: 2bddde2e-9ca0-4f72-8910-0789a6350af8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „System.ObsoleteAttribute“ kann nicht auf die Definitionen „AddHandler“, „RemoveHandler“ oder „RaiseEvent“ angewendet werden.
„System.ObsoleteAttribute“ kann nicht auf die Definitionen „AddHandler“, „RemoveHandler“ oder „RaiseEvent“ angewendet werden. Wenden Sie das Attribut, falls erforderlich, direkt auf das Ereignis an.  
  
 Ein benutzerdefiniertes Ereignis wendet das <xref:System.ObsoleteAttribute> auf seine `AddHandler`\-, `RemoveHandler`\- oder `RaiseEvent`\-Prozedur an.  
  
 Das <xref:System.ObsoleteAttribute> kennzeichnet ein Programmierelement als nicht mehr in Verwendung und informiert die Benutzer, dass das Element in zukünftigen Versionen des Produkts entfernt wird.  
  
 Es ist nicht sinnvoll, bestimmte Teile eines benutzerdefinierten Ereignisses weiterhin zu verwenden, obwohl andere Teile nicht mehr verwendet werden.  
  
 **Fehler\-ID:** BC31142  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das <xref:System.ObsoleteAttribute> aus der Deklaration der einzelnen Prozedur, und wenden Sie es auf die gesamte Ereignisdeklaration an.  
  
## Siehe auch  
 <xref:System.ObsoleteAttribute>   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [RemoveHandler Statement](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [RaiseEvent Statement](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)