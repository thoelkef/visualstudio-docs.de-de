---
title: "&lt;Membername&gt; ist kein Member von &lt;Kontextname&gt; und ist im aktuellen Kontext nicht vorhanden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Membername&gt; ist kein Member von &lt;Kontextname&gt; und ist im aktuellen Kontext nicht vorhanden.
Ein nicht vorhandener Membername wurde einer Eigenschaft in der Deklaration eines anonymen Typs zugewiesen. Im folgenden Beispiel sind `.Prop1` und `.Prop2` die Eigenschaften des anonymen Typs. Der Versuch, `.Prop2``.Prop3` zuzuweisen, hat den Fehler verursacht.  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **Fehler\-ID:** BC36657  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie den Code, um zu bestimmen, was Sie zuweisen möchten. Der Name der Variablen ist möglicherweise falsch geschrieben, oder es ist eine Qualifizierung erforderlich, wenn er eine Eigenschaft eines anderen Objekts ist.  
  
## Siehe auch  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Gewusst wie: Ableiten von Eigenschaftennamen und Typen in Deklarationen von anonymen Typen](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)