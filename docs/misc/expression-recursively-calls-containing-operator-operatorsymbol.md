---
title: "Der Ausdruck ruft rekursiv den enthaltenden Operator &lt;Operatorsymbol&gt; auf. | Microsoft Docs"
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
  - "BC42004"
  - "vbc42004"
helpviewer_keywords: 
  - "BC42004"
ms.assetid: a874c44a-3aec-447d-90f7-5659f1b2f5f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Ausdruck ruft rekursiv den enthaltenden Operator &lt;Operatorsymbol&gt; auf.
Ein Ausdruck in einer Operatorprozedur verwendet den Operator, der gerade definiert wird. Dies führt dazu, dass die Operatorprozedur aufgrund der verwendeten Datentypen sich selbst aufruft.  
  
 Die Operatorprozedur, die Sie gerade definieren, ruft sich selbst auf, wenn sie denselben Operator verwendet, wie folgende Komponenten:  
  
-   Die gleichen Operanden, für die Sie den Operator definieren;  
  
-   Die Operanden der gleichen Datentypen, für die Sie den Operator definieren; oder  
  
-   Die Operanden der Datentypen, die zu den Datentypen erweitert werden, für die Sie den Operator definieren.  
  
 Als *rekursiver Aufruf* wird eine Prozedur bezeichnet, die sich selbst aufruft. Rekursive Aufrufe können zu einer *Endlosschleife* führen, in der das Steuerelement den gleichen Satz von Anweisungen immer wieder durchläuft, bis die Anwendung extern beendet wird. Wenn Ihr Code keine Tests enthält, mit denen eine mögliche Rekursion beendet werden kann, riskieren Sie eine Endlosschleife.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42004  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Ihre Logik erfordert, dass die Operatorprozedur sich selbst aufruft, stellen Sie sicher, dass Sie mindestens auf eine Bedingung testen, die an einem bestimmten Punkt mit Sicherheit vorkommt, und verwenden Sie diesen Test zum Beenden rekursiver Aufrufe.  
  
-   Wenn Ihre Logik nicht erfordert, dass die Operatorprozedur sich selbst aufruft, entfernen Sie alle rekursiven Aufrufe, oder ersetzen Sie sie durch Anweisungen, die ihre eigene Prozedur nicht aufrufen.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)