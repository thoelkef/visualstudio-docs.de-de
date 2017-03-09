---
title: "Die Datentypen der Typparameter in der in &lt;Typname&gt; definierten Erweiterungsmethode &lt;Methodenname&gt; k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da mehrere Typen m&#246;glich sind. | Microsoft Docs"
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
  - "bc36655"
  - "vbc36652"
  - "vbc36655"
  - "bc36652"
helpviewer_keywords: 
  - "BC36655"
  - "BC36655"
ms.assetid: 49836f20-c877-4267-8bdc-6f6d108fb8c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Datentypen der Typparameter in der in &lt;Typname&gt; definierten Erweiterungsmethode &lt;Methodenname&gt; k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da mehrere Typen m&#246;glich sind.
Die Datentypen der Typparameter in der in \<Typname\> definierten Erweiterungsmethode \<Methodenname\> können nicht von diesen Argumenten abgeleitet werden, da mehrere Typen möglich sind. Sie können diesen Fehler möglicherweise beheben, indem Sie die Datentypen explizit angeben.  
  
 In einem Aufruf einer generischen Erweiterungsmethode wurde versucht, über den Typrückschluss den Typ \(oder die Typen\) des bzw. der Typparameter zu bestimmen. Der Compiler findet mehrere mögliche Datentypen für einen oder mehrere Typparameter und meldet diesen Fehler.  
  
> [!NOTE]
>  Wenn die Angabe von Argumenten keine Option ist \(z. B. für Abfrageoperatoren in Abfrageausdrücken\), wird nur der erste Satz der Fehlermeldung angezeigt.  
  
 Der folgende Code verdeutlicht den Fehler.  
  
```vb#  
Option Strict Off Imports System.Runtime.CompilerServices Module Module1 Sub Main() Dim caller As New Class1 '' Not valid. 'caller.targetExtension(1, "2") End Sub <Extension()> _ Sub targetExtension(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **Fehler\-ID:** BC36655 \(in [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)]\-Abfragen\) und BC36652 \(außerhalb von Abfragen\)  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Fehler außerhalb einer Abfrage angezeigt wird, versuchen Sie es mit der expliziten Angabe des Datentyps des Typparameters bzw. der Typparameter:  
  
    ```  
    caller.targetExtension(Of Integer)(1, "2") caller.targetExtension(Of String)(1, "2")  
    ```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)