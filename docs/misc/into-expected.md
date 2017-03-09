---
title: "&#39;Into&#39; erwartet. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36615"
  - "vbc36615"
helpviewer_keywords: 
  - "BC36615"
ms.assetid: 24062dd9-a973-43b6-88d3-c11adc5a3736
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Into&#39; erwartet.
Eine `Aggregate`\-, `Group By`\- oder `Group Join`\-Klausel wurde ohne den `Into`\-Operator angegeben. Sie verwenden den `Into`\-Operator, um Aggregatfunktionen zu identifizieren, die auf das Abfrageergebnis angewendet werden, und um die Member des Abfrageergebnistyps zu identifizieren, die die gruppierten Ergebnisse enthalten sollen \(mithilfe der `Group`\-Aggregatfunktion\).  
  
 **Fehler\-ID:** BC36615  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie den `Into`\-Operator zur `Aggregate`\-, `Group By`\- oder `Group Join`\-Klausel hinzu. Im Folgenden finden Sie ein Beispiel dazu:  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## Siehe auch  
 [Aggregate Clause](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Group By\-Klausel](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)