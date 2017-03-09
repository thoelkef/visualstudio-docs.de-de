---
title: "&#39;Group&#39; oder ID erwartet | Microsoft Docs"
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
  - "vbc36707"
  - "bc36707"
helpviewer_keywords: 
  - "BC36707"
ms.assetid: 214e4aa3-d20f-41b3-902c-f1076d31b832
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Group&#39; oder ID erwartet
Der `Into`\-Teil einer `Group By`\- oder `Group Join`\-Klausel enthält das `Group`\-Schlüsselwort nicht. Sie müssen das `Group`\-Schlüsselwort in die `Into`\-Klausel einer `Group By`\- oder `Group Join`\-Klausel einschließen, um den für die gruppierten Ergebnisse zu verwendenden Variablennamen zu erkennen. Dabei kann es sich entweder um einen von Ihnen angegebenen Namen oder um das Schlüsselwort `Group` handeln.  
  
 **Fehler\-ID:** BC36707  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der `Into`\-Teil der `Group By`\- oder `Group Join`\-Klausel das `Group`\-Schlüsselwort enthält, wie im folgenden Beispiel gezeigt.  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## Siehe auch  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Group By\-Klausel](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)