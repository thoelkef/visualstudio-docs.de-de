---
title: "Die Datentypen der Typparameter in der Methode &lt;Methodenname&gt; k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da mehrere Typen m&#246;glich sind. | Microsoft Docs"
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
  - "bc36651"
  - "bc36654"
  - "vbc36651"
  - "vbc36654"
helpviewer_keywords: 
  - "BC36651"
  - "BC36651"
ms.assetid: d4bf408c-ca1f-44ad-855a-3df898de60c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Datentypen der Typparameter in der Methode &lt;Methodenname&gt; k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da mehrere Typen m&#246;glich sind.
Die Datentypen der Typparameter in der Methode \<Methodenname\> können nicht von diesen Argumenten abgeleitet werden, da mehrere Typen möglich sind. Sie können diesen Fehler möglicherweise beheben, indem Sie die Datentypen explizit angeben.  
  
 In einem Aufruf einer generischen Prozedur wurde versucht, über den Typrückschluss den Typ oder die Typen des bzw. der Typparameter zu bestimmen. Der Compiler findet mehrere mögliche Datentypen für einen oder mehrere Typparameter und meldet diesen Fehler.  
  
> [!NOTE]
>  Wenn die Angabe von Argumenten keine Option ist \(z. B. für Abfrageoperatoren in Abfrageausdrücken\), wird nur der erste Satz der Fehlermeldung angezeigt.  
  
 Der folgende Code verdeutlicht den Fehler.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. 'targetMethod(1, "2") End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **Fehler\-ID:** BC36654 \(in [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)]\-Abfragen\) und BC36651 \(außerhalb von Abfragen\)  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Fehler außerhalb einer Abfrage angezeigt wird, versuchen Sie es mit der expliziten Angabe des Datentyps des Typparameters:  
  
    ```  
    targetMethod(Of Integer)(1, "2")  
    ```  
  
## Siehe auch  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)