---
title: "Keine Maus vorhanden | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoMouseIsPresent"
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Keine Maus vorhanden
Eine der Eigenschaften des `My.Computer.Mouse`\-Objekts wurde aufgerufen, aber der Computer verfügt über keine Maus, oder es ist kein Port für die Maus installiert.  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie rund um den Aufruf der Eigenschaft des `My.Computer.Mouse`\-Objekts einen `Try...Catch`\-Block hinzu.  
  
     Oder...  
  
-   Installieren Sie auf dem Computer eine Maus.  
  
## Siehe auch  
 [My.Computer.Mouse Object](/dotnet/visual-basic/language-reference/objects/my-computer-mouse-object)   
 [Ausnahmen\- und Fehlerbehandlung in Visual Basic](http://msdn.microsoft.com/de-de/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)