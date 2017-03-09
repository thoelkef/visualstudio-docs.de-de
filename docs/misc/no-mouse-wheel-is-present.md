---
title: "Es ist kein Mausrad vorhanden. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoWheelIsPresent"
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es ist kein Mausrad vorhanden.
Die `My.Computer.Mouse.WheelScrollLines`\-Eigenschaft wurde aufgerufen, aber die Maus besitzt kein Mausrad.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die `My.Computer.Mouse.WheelExists`\-Eigenschaft, um festzustellen, ob die Maus über ein Mausrad verfügt, bevor Sie die `My.Computer.Mouse.WheelScrollLines`\-Eigenschaft aufrufen.  
  
     \- oder \-  
  
-   Installieren Sie auf dem Computer eine Maus mit einem Mausrad.  
  
## Siehe auch  
 [My.Computer.Mouse.WheelScrollLines\-Eigenschaft](http://msdn.microsoft.com/de-de/67600f96-25d7-4dd9-946a-b46e1fc6a57f)   
 [My.Computer.Mouse.WheelExists\-Eigenschaft](http://msdn.microsoft.com/de-de/332d44f7-0b66-4eaa-b4ce-d7f161bfbd07)   
 [Ausnahmen\- und Fehlerbehandlung in Visual Basic](http://msdn.microsoft.com/de-de/3e351e73-cf23-40ab-8b60-05794160529e)