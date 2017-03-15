---
title: "Die in &#39;&lt;typName&gt;&#39; definierte Erweiterungsmethode &#39;&lt;methodenName&gt;&#39; weist nicht die gleiche Signatur wie der Delegat &#39;&lt;delegateName&gt;&#39; auf | Microsoft Docs"
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
  - "bc36580"
  - "vbc36580"
helpviewer_keywords: 
  - "BC36580"
ms.assetid: dc6b6a63-02b0-43d8-b6a7-c1cd397c6ee3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die in &#39;&lt;typName&gt;&#39; definierte Erweiterungsmethode &#39;&lt;methodenName&gt;&#39; weist nicht die gleiche Signatur wie der Delegat &#39;&lt;delegateName&gt;&#39; auf
Es gibt einen Konflikt zwischen den Signaturen der Erweiterungsmethode und des Delegaten, den Sie verwenden möchten. Die `Delegate`\-Anweisung definiert die Parameter\- und Rückgabetypen einer Delegatklasse. Jede Prozedur mit passenden Parametern und Typen sowie passendem Rückgabetyp kann dazu verwendet werden, eine Instanz dieses Delegattyps zu erstellen. Dieser Fehler wird im folgenden Beispiel gemeldet, da die Signatur der Erweiterungsmethode `Example` nicht mit der Signatur des Delegats `Del` kompatibel ist.  
  
```vb#  
' Definition of the delegate, with two parameters. Delegate Sub Del(ByVal m As Integer, ByVal s As String)  
```  
  
```vb#  
' Definition of the extension method, with one parameter. <Extension()> _ Sub Example(ByVal s As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
'' This assignment causes the error. ' Dim exampleDel As Del = AddressOf Example  
```  
  
 **Fehler\-ID:** BC36580  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie, ob der Delegat und die Erweiterungsmethode die gleiche Anzahl von Parametern haben.  
  
-   Überprüfen Sie, ob die Reihenfolge der Parameter im Delegaten und der Erweiterungsmethode gleich ist.  
  
-   Vergleichen Sie den Datentyp jedes einzelnen Delegatparameters mit dem Datentyp des entsprechenden Parameters der Erweiterungsmethode, um sicherzustellen, dass sie kompatibel sind.  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)