---
title: "&#39;#ElseIf&#39; kann als Teil eines #If-Blocks nicht auf &#39;#Else&#39; folgen. | Microsoft Docs"
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
  - "bc32030"
  - "vbc32030"
helpviewer_keywords: 
  - "BC32030"
ms.assetid: 248d6464-3019-4753-8a33-7070bbe5d2a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39; kann als Teil eines #If-Blocks nicht auf &#39;#Else&#39; folgen.
Eine bedingte `#ElseIf`\-Kompilierungsdirektive folgt auf eine `#Else`\-Direktive.`#Else` muss die letzte Direktive im bedingten Block vor der `#End If`\-Direktive sein.  
  
 **Fehler\-ID:** BC32030  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, ob das vorausgehende `#Else` ein `#ElseIf` sein soll.  
  
2.  Überprüfen Sie, ob ein vorausgehender `#If`\-Block ordnungsgemäß abgeschlossen wurde und ein neuer `#If`\-Block initiiert wird.  
  
3.  Wenn alles andere richtig ist, verschieben Sie diese `#ElseIf`\-Direktive und ihren entsprechenden Anweisungsblock, damit diese dem `#Else`\-Block vorangestellt sind.  
  
## Siehe auch  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)