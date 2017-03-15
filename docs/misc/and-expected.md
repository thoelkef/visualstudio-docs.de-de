---
title: "&#39;And&#39; erwartet. | Microsoft Docs"
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
  - "vbc36620"
  - "bc36620"
helpviewer_keywords: 
  - "BC36620"
ms.assetid: b3d21d4d-86c0-44d2-8afc-c19d375e9ddd
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;And&#39; erwartet.
Es wurde ein anderer Vergleichsoperator als `And` verwendet, um zwei oder mehr `Equals`\-Operatoren in einer `Join`\- oder `Group Join`\-Klausel zu kombinieren. Nur der `And`\-Operator ist zulässig, um mehrere `Equals`\-Operatoren in einer `Join`\- oder `Group Join`\-Klausel zu kombinieren.  
  
 **Fehler\-ID:** BC36620  
  
### So beheben Sie diesen Fehler  
  
1.  Strukturieren Sie die `Equals`\-Klauseln um, um Vergleiche nur über den `And`\-Operator vorzunehmen. Im Folgenden finden Sie ein Beispiel dazu:  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _  
                        Join pet In pets _  
                        On pet.Owner Equals pers And _  
                           pet.Name = pers.PetName_  
                        Select pers, pet  
    ```  
  
## Siehe auch  
 [How to: Combine Data with Joins](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join Clause](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)