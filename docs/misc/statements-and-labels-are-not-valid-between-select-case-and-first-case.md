---
title: "Anweisungen und Bezeichnungen sind zwischen &quot;Select Case&quot; und dem ersten Vorkommen von &quot;Case&quot; nicht g&#252;ltig | Microsoft Docs"
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
  - "bc30058"
  - "vbc30058"
helpviewer_keywords: 
  - "BC30058"
ms.assetid: 399b4659-f7df-4377-80be-43019f1e6206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Anweisungen und Bezeichnungen sind zwischen &quot;Select Case&quot; und dem ersten Vorkommen von &quot;Case&quot; nicht g&#252;ltig
Eine Anweisung, die kein Kommentar ist, wird zwischen dem Öffnen der `Select`\- oder der `Select Case`\-Anweisung und der ersten zugehörigen `Case`\-Anweisung angezeigt.  
  
 **Fehler\-ID:** BC30058  
  
### So beheben Sie diesen Fehler  
  
-   Wenn es sich bei der dazwischenstehenden Anweisung um einen Kommentar handelt, fügen Sie davor ein Kommentartrennzeichen ein \(`'` oder `REM`\). Verschieben oder löschen Sie die Anweisung andernfalls.  
  
## Siehe auch  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)