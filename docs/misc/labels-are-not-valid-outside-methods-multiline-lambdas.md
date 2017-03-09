---
title: "Bezeichnungen sind au&#223;erhalb von Methoden/mehrzeiligen lambda-Ausdr&#252;cken ung&#252;ltig. | Microsoft Docs"
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
  - "vbc30016"
  - "bc30016"
helpviewer_keywords: 
  - "BC30016"
ms.assetid: 17d12a96-d759-4df9-882c-5e45c1d814a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bezeichnungen sind au&#223;erhalb von Methoden/mehrzeiligen lambda-Ausdr&#252;cken ung&#252;ltig.
Sie können einer Anweisung eine Bezeichnung nur in einer `Sub`\-, `Function`\-, Eigenschaften\-`Get`\- oder Eigenschaften\-`Set`\-Prozedur hinzufügen. Nur eine ausführbare Anweisung kann eine Bezeichnung haben, und alle ausführbaren Anweisungen müssen sich in Prozeduren befinden.  
  
 **Fehler\-ID:** BC30016  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Bezeichnung aus der Anweisung, oder verschieben Sie die Anweisung in eine Prozedur.  
  
## Siehe auch  
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)