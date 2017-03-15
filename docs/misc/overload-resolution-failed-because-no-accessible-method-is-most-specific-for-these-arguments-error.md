---
title: "Fehler bei der &#220;berladungsaufl&#246;sung, da keine zugreifbare &#39;&lt;Methode&gt;&#39; f&#252;r diese Argumente am spezifischsten ist: &lt;Fehler&gt; | Microsoft Docs"
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
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "Auflösungsfehler"
  - "BC30521"
  - "Fehler bei der Überladungsauflösung"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehler bei der &#220;berladungsaufl&#246;sung, da keine zugreifbare &#39;&lt;Methode&gt;&#39; f&#252;r diese Argumente am spezifischsten ist: &lt;Fehler&gt;
Sie haben eine überladene Methode aufgerufen, aber der Compiler hat zwei oder mehr Überladungen mit Parameterlisten gefunden, in die Ihre Argumentliste konvertiert werden kann, und der Compiler ist nicht in der Lage, die Auswahl zu treffen.  
  
 Der Compiler versucht, die Datentypen in der aufrufenden Argumentliste weitestgehend mit der Liste der Überladungsparameter zu vergleichen. Es ist eine erweiternde Konvertierung jedes Arguments in den entsprechenden Parameter erforderlich, unabhängig davon, ob der Schalter für die Typüberprüfung \([Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) `On` oder `Off` ist.  
  
 Wenn der Compiler mehrere Überladungen findet, die die Erweiterungsanforderung erfüllen, dann sucht er nach der Überladung, die für die Argumentdatentypen am genauesten bestimmt ist, also die geringste Erweiterung erfordert. Der Compiler generiert diese Fehlermeldung, wenn eine Überladung für einen Argumentdatentyp genauer bestimmt ist, während eine andere Überladung für einen anderen Argumentdatentyp genauer bestimmt ist. Weitere Informationen und ein Beispiel finden Sie unter [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 **Fehler\-ID:** BC30521  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie alle Überladungen der Methode und bestimmen Sie, welche aufgerufen werden soll.  
  
2.  Stellen Sie in der aufrufenden Anweisung sicher, dass die Datentypen der Argumente mit den Datentypen der Parameter übereinstimmen, die für die gewünschte Überladung definiert wurden. Möglicherweise müssen Sie die [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function) verwenden, um einen oder mehrere Datentypen in die definierten Typen zu konvertieren.  
  
## Siehe auch  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function)