---
title: "&#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; oder &#39;Const&#39; erwartet. | Microsoft Docs"
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
  - "vbc30248"
  - "bc30248"
helpviewer_keywords: 
  - "BC30248"
ms.assetid: fa3bf591-8036-459c-8c29-ed7784e444f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; oder &#39;Const&#39; erwartet.
Eine Quellzeile beginnt mit einem `#`\-Zeichen, aber auf das `#` folgt nicht direkt eine gültige bedingte Kompilierungsdirektive. Gültige Direktiven sind `#Const`, `#ExternalSource`, `#If`, `#Else`, `#ElseIf`, `#End If` und `#Region`.  
  
 **Fehler\-ID:** BC30248  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass die bedingte Kompilierungsdirektive richtig geschrieben ist.  
  
2.  Stellen Sie sicher, dass kein Leerzeichen zwischen dem `#`\-Zeichen und der Direktive ist.  
  
3.  Entfernen Sie das `#`\-Zeichen, oder fügen Sie direkt dahinter eine gültige Direktive hinzu.  
  
## Siehe auch  
 [Directives](/dotnet/visual-basic/language-reference/directives/directives)