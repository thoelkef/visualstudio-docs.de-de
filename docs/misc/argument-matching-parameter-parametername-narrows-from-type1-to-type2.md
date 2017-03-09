---
title: "Der mit dem Argument &#252;bereinstimmende Parameter &quot;&lt;Parametername&gt;&quot; wird von &quot;&lt;Typ1&gt;&quot; auf &quot;&lt;Typ2&gt;&quot; reduziert. | Microsoft Docs"
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
  - "vbc30520"
  - "bc30520"
helpviewer_keywords: 
  - "BC30520"
ms.assetid: 652ff70b-156d-4d1c-af19-fa1c53e2d0b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der mit dem Argument &#252;bereinstimmende Parameter &quot;&lt;Parametername&gt;&quot; wird von &quot;&lt;Typ1&gt;&quot; auf &quot;&lt;Typ2&gt;&quot; reduziert.
Sie haben eine überladene Methode aufgerufen, der Compiler findet jedoch keine Methode, die ohne eine einschränkende Konvertierung aufgerufen werden kann. Eine einschränkende Konvertierung ändert einen Wert in einen Datentyp, der möglicherweise nicht in der Lage ist, alle möglichen Werte exakt zu speichern.  
  
 **Fehler\-ID:** BC30520  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie `Option Strict Off` an.  
  
## Siehe auch  
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)