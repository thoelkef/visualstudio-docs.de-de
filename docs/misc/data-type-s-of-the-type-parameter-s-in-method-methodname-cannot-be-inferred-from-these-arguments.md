---
title: "Die Datentypen der Typparameter in der &quot;&lt;Methodenname&gt;&quot;-Methode k&#246;nnen nicht von diesen Argumenten abgeleitet werden. | Microsoft Docs"
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
  - "vbc36648"
  - "bc36645"
  - "bc36648"
  - "vbc36645"
helpviewer_keywords: 
  - "BC36648"
  - "BC36648"
ms.assetid: cc8c67bb-6cbb-4d7c-ba26-fe1d38908434
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Datentypen der Typparameter in der &quot;&lt;Methodenname&gt;&quot;-Methode k&#246;nnen nicht von diesen Argumenten abgeleitet werden.
Die Datentypen der Typparameter in der "\<Methodenname\>"\-Methode können nicht von diesen Argumenten abgeleitet werden. Sie können diesen Fehler möglicherweise beheben, indem Sie die Datentypen explizit angeben.  
  
 Beim Auswerten eines Aufrufs einer generischen Prozedur wurde versucht, über den Typrückschluss den Datentyp \(oder die Datentypen\) der Typparameter zu bestimmen. Der Compiler kann jedoch keinen Datentyp für die Typparameter in dieser Methode finden und gibt die Fehlermeldung aus.  
  
> [!NOTE]
>  Wenn die Angabe von Argumenten keine Option ist \(z. B. für Abfrageoperatoren in Abfrageausdrücken\), wird nur der erste Satz der Fehlermeldung angezeigt.  
  
 Im folgenden Codebeispiel wird der Fehler erläutert.  
  
```vb#  
Module Module1 Sub Main() '' Not valid. 'GenericMethod("Hello", "World") End Sub Sub GenericMethod(Of T)(ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface  
```  
  
 **Fehler\-ID:** BC36648 und BC36645  
  
### So beheben Sie diesen Fehler  
  
-   Anstelle des Typrückschlusses können Sie einen Datentyp für den oder die Typparameter angeben.  
  
## Siehe auch  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)