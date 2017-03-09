---
title: "&#39;Catch&#39; kann den Typ &#39;&lt;typname&gt;&#39; nicht abfangen, da er weder &#39;System.Exception&#39; ist noch eine Klasse, die von &#39;System.Exception&#39; erbt. | Microsoft Docs"
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
  - "vbc30392"
  - "bc30392"
helpviewer_keywords: 
  - "BC30392"
ms.assetid: 1d513d1d-38f5-4b4e-95bb-9f1209553803
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; kann den Typ &#39;&lt;typname&gt;&#39; nicht abfangen, da er weder &#39;System.Exception&#39; ist noch eine Klasse, die von &#39;System.Exception&#39; erbt.
`Catch` kann nur Ausnahmen abfangen, und Sie haben versucht, etwas abzufangen, das nicht von einer Ausnahme abgeleitet ist.  
  
 **Fehler\-ID:** BC30392  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die `Catch`\-Anweisung, oder ändern Sie das Ziel von `Catch` in eine tatsächliche Ausnahme.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)