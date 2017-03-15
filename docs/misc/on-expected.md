---
title: "&quot;On&quot; erwartet. | Microsoft Docs"
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
  - "bc36618"
  - "vbc36618"
helpviewer_keywords: 
  - "BC36618"
ms.assetid: 7cb1b205-c4c3-4485-ae3f-8942425692ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;On&quot; erwartet.
Eine `Join`\- oder `Group Join`\-Klausel wurde ohne den `On`\-Operator angegeben. Der `On`\-Operator wird verwendet, um das Schlüsselfeld der Bereichsvariablen für jede Auflistung zu definieren. Schlüsselfelder werden verwendet, um Elemente aus jeder Auflistung abzugleichen.  
  
 **Fehler\-ID:** BC36618  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie der `Join`\- oder `Group Join`\-Klausel den `On`\-Operator und Schlüsselfelder hinzu. Beachten Sie folgendes Beispiel:  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _ Join pet In pets _ On pet.Owner Equals pers _ Select pers.FirstName, PetName = pet.Name  
    ```  
  
## Siehe auch  
 [How to: Combine Data with Joins](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join Clause](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)