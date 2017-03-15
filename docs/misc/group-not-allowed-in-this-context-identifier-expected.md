---
title: "&#39;Gruppe&#39; in diesem Kontext unzul&#228;ssig; ID erwartet. | Microsoft Docs"
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
  - "bc36708"
  - "vbc36708"
helpviewer_keywords: 
  - "BC36708"
ms.assetid: ef6b453e-68e7-47c2-997c-9fd1ca074217
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Gruppe&#39; in diesem Kontext unzul&#228;ssig; ID erwartet.
Das `Group`\-Schlüsselwort ist im `Into`\-Abschnitt einer `Aggregate`\-Klausel enthalten. Das `Group`\-Schlüsselwort ist nur in den `Group By`\- oder `Group Join`\-Klauseln gültig.  
  
 **Fehler\-ID:** BC36618  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Group`\-Schlüsselwort aus der `Aggregate`\-Klausel. Sie können eine `Group By`\-Klausel zur Abfrage hinzufügen, um die Ergebnisse zu gruppieren.  
  
## Siehe auch  
 [Aggregate Clause](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Group By\-Klausel](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)