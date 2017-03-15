---
title: "Der Name einer Bereichsvariablen darf nicht mit dem Namen eines Members der Object-Klasse &#252;bereinstimmen. | Microsoft Docs"
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
  - "bc36606"
  - "vbc36606"
helpviewer_keywords: 
  - "BC36606"
ms.assetid: 964245e6-2601-4de6-8a51-25c0d9633418
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Name einer Bereichsvariablen darf nicht mit dem Namen eines Members der Object-Klasse &#252;bereinstimmen.
Eine Bereichsvariable in einer LINQ\-Abfrage stimmt mit dem Namen eines Members der <xref:System.Object>\-Klasse überein. Dies verursacht einen Konflikt mit den Objekten, die von Visual Basic für die LINQ\-Abfrage erstellt wurden.  
  
 **Fehler\-ID:** BC36606  
  
### So beheben Sie diesen Fehler  
  
1.  Wählen Sie einen neuen Namen für die Bereichsvariable aus, der keinem Namen eines Members in der <xref:System.Object>\-Klasse entspricht.  
  
## Siehe auch  
 <xref:System.Object>   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [From Clause](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Aggregate Clause](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Select Clause](/dotnet/visual-basic/language-reference/queries/select-clause)