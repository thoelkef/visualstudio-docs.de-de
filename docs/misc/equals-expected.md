---
title: "&#39;Equals&#39; erwartet | Microsoft Docs"
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
  - "vbc36619"
  - "bc36619"
helpviewer_keywords: 
  - "BC36619"
ms.assetid: 1fd8c0dc-0e87-47b7-ab30-498809cca033
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; erwartet
Eine `Join`\- oder `Group Join`\-Klausel wurde ohne den `Equals`\-Operator angegeben. Sie verwenden den `Equals`\-Operator zum Identifizieren der `Boolean`\-Operation, um Schlüsselfelder auf übereinstimmende Elemente zu testen.  
  
 **Fehler\-ID:** BC36619  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie der `Join`\- oder `Group Join`\-Klausel den `Equals`\-Operator und Schlüsselfelder hinzu. Zum Beispiel:  
  
    ```vb#  
    Dim petOwnersGrouped = From pers In people _ Group Join pet In pets _ On pers Equals pet.Owner _ Into PetList = Group _ Select pers.FirstName, pers.LastName, _ PetList  
    ```  
  
## Siehe auch  
 [How to: Combine Data with Joins](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join Clause](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)