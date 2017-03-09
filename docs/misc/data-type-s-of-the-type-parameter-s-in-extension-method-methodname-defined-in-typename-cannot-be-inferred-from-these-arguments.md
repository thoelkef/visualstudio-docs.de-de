---
title: "Die Datentypen der Typparameter in der in &quot;&lt;Typname&gt;&quot; definierten Erweiterungsmethode &quot;&lt;Methodenname&gt;&quot; k&#246;nnen nicht von diesen Argumenten abgeleitet werden | Microsoft Docs"
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
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36646"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Datentypen der Typparameter in der in &quot;&lt;Typname&gt;&quot; definierten Erweiterungsmethode &quot;&lt;Methodenname&gt;&quot; k&#246;nnen nicht von diesen Argumenten abgeleitet werden
Die Datentypen der Typparameter in der in "\<Typname\>" definierten Erweiterungsmethode "\<Methodenname\>" können nicht von diesen Argumenten abgeleitet werden. Sie können diesen Fehler möglicherweise beheben, indem Sie die Datentypen explizit angeben.  
  
 Beim Auswerten eines Aufrufs einer generischen Erweiterungsmethode wurde versucht, über den Typrückschluss den Datentyp \(oder die Datentypen\) des Typparameters \(oder der Typparameter\) zu bestimmen. Der Compiler kann jedoch keinen Datentyp für die Typparameter in dieser Methode finden und gibt die Fehlermeldung aus.  
  
> [!NOTE]
>  Wenn die Angabe von Argumenten keine Option ist \(z. B. für Abfrageoperatoren in Abfrageausdrücken\), wird nur der erste Satz der Fehlermeldung angezeigt.  
  
 Im folgenden Code wird der Fehler veranschaulicht.  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **Fehler\-ID:** BC36649 und BC36646  
  
### So beheben Sie diesen Fehler  
  
-   Anstelle des Typrückschlusses können Sie einen Datentyp für den oder die Typparameter angeben.  
  
## Siehe auch  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)