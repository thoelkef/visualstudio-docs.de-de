---
title: "&quot;&lt;Prozedurename1&gt;&quot; kann &quot;&lt;Prozedurename2&gt;&quot; nicht &#252;berschreiben, da in diesem Kontext nicht darauf zugegriffen werden kann. | Microsoft Docs"
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
  - "bc31417"
  - "vbc31417"
helpviewer_keywords: 
  - "BC31417"
ms.assetid: 1a36acbf-cead-43a0-b12f-f52f94d09124
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Prozedurename1&gt;&quot; kann &quot;&lt;Prozedurename2&gt;&quot; nicht &#252;berschreiben, da in diesem Kontext nicht darauf zugegriffen werden kann.
Eine Prozedur oder Eigenschaft überschreibt eine Prozedur oder Eigenschaft, die einen Zugriffsebene hat, die den Zugriff für die überschreibende Prozedur bzw. Eigenschaft verhindert.  
  
 Ist eine Prozedur beispielsweise in einer Assembly als `Friend` deklariert, kann nicht außerhalb dieser Assembly auf die Prozedur zugegriffen werden. Versucht eine Prozedur, die sich in einer anderen Assembly im selben Projekt befindet, die `Friend`\-Prozedur zu überschreiben, kann sie nicht auf diese Prozedur zugreifen, um sie zu überschreiben.  
  
 **Error ID:** BC31417  
  
### So beheben Sie diesen Fehler  
  
-   Verschieben Sie die überschreibende Prozedur oder Eigenschaft in die Assembly, zu der die Prozedur oder Eigenschaft gehört, die sie überschreiben soll.  
  
     \- oder \-  
  
-   Entfernen Sie das `Overrides`\-Schlüsselwort.  
  
## Siehe auch  
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)