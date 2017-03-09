---
title: "Der Wert des ByRef-Parameters &quot;&lt;Parametername&gt;&quot; kann nicht in das entsprechende Argument zur&#252;ckkopiert werden, da der Typ &quot;&lt;Typname1&gt;&quot; nicht in Typ &quot;&lt;Typname2&gt;&quot; konvertiert werden kann. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33037"
  - "BC33037"
helpviewer_keywords: 
  - "BC33037"
ms.assetid: 3ff137e2-e062-4e54-abf5-e902e2d18968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Wert des ByRef-Parameters &quot;&lt;Parametername&gt;&quot; kann nicht in das entsprechende Argument zur&#252;ckkopiert werden, da der Typ &quot;&lt;Typname1&gt;&quot; nicht in Typ &quot;&lt;Typname2&gt;&quot; konvertiert werden kann.
Eine Prozedur ist mit einem Parametertyp deklariert, der nicht zurück in den aufrufenden Argumenttyp konvertiert werden kann.  
  
 Wenn Sie eine Klasse oder Struktur definieren, können Sie einen oder mehrere Konvertierungsoperatoren zum Konvertieren dieses Klassen\- oder Strukturtyps in andere Typen definieren. Sie können auch Operatoren für die umgekehrte Konvertierung definieren, um dieser anderen Typen zurück in den Klassen\- oder Strukturtyp zu konvertieren. Wenn Sie den Klassen\- oder Strukturtyp in einem Prozeduraufruf verwenden, kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mithilfe dieser Konvertierungsoperatoren den Typ eines Arguments in den Typ des entsprechenden Parameters konvertieren.  
  
 Wenn Sie das [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)\-Argument übergeben, kopiert [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zuweilen den Argumentwert in eine lokale Variable in der Prozedur, statt einen Verweis zu übergeben. In diesem Fall muss [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nach Abschluss der Prozedur den Wert der lokalen Variablen zurück in das Argument im aufrufenden Code kopieren.  
  
 Wenn ein `ByRef`\-Argumentwert in die Prozedur kopiert wird und das Argument und der Parameter denselben Typ aufweisen, ist keine Konvertierung erforderlich. Wenn hingegen die Typen unterschiedlich sind, muss [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] die Konvertierung in beide Richtungen ausführen. Wenn einer der Typen Ihr Klassen\- oder Strukturtyp ist, muss [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ihn sowohl in den als auch aus dem anderen Typ konvertieren. Dies bedeutet, dass Sie in beide Richtungen Konvertierungsoperatoren definieren müssen.  
  
 **Fehler\-ID:** BC33037  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie nach Möglichkeit ein aufrufendes Argument, das denselben Typ aufweist wie der Prozedurparameter, sodass [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keine Konvertierung ausführen muss.  
  
-   Wenn Sie die Prozedur mit einem Argument aufrufen müssen, dessen Typ sich vom Parametertyp unterscheidet, jedoch kein Wert in das aufrufende Argument zurückgegeben werden muss, definieren Sie den Parameter als [ByVal](/dotnet/visual-basic/language-reference/modifiers/byval) anstelle von `ByRef`.  
  
-   Wenn ein Wert in das aufrufende Argument zurückgegeben werden muss, definieren Sie den Operator für die umgekehrte Konvertierung, damit [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] die Konvertierung zurück in den aufrufenden Argumenttyp ausführen kann.  
  
## Siehe auch  
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)   
 [Procedure Parameters and Arguments](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)