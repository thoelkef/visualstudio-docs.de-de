---
title: "Fehler bei der &#220;berladungsaufl&#246;sung, da keine zugreifbare &quot;&lt;Methode&gt;&quot; ohne einschr&#228;nkende Konvertierung aufgerufen werden kann: &lt;Fehler&gt; | Microsoft Docs"
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
  - "vbc30519"
  - "bc30519"
helpviewer_keywords: 
  - "BC30519"
ms.assetid: 3b3e724d-6fad-4146-b47d-6525493b2fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehler bei der &#220;berladungsaufl&#246;sung, da keine zugreifbare &quot;&lt;Methode&gt;&quot; ohne einschr&#228;nkende Konvertierung aufgerufen werden kann: &lt;Fehler&gt;
Sie haben eine überladene Methode aufgerufen, der Compiler findet jedoch keine Methode, die ohne eine einschränkende Konvertierung aufgerufen werden kann. Eine einschränkende Konvertierung ändert einen Wert in einen Datentyp, der möglicherweise nicht in der Lage ist, alle möglichen Werte exakt zu speichern.  
  
 **Fehler\-ID:** BC30519  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie `Option Strict Off` an.  
  
## Siehe auch  
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)