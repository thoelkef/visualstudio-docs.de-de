---
title: "Module k&#246;nnen nicht generisch sein. | Microsoft Docs"
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
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Module k&#246;nnen nicht generisch sein.
Ein `Module`\-Anweisung verwendet das `Of`\-Schlüsselwort, um generische Typparameter einzuführen.  
  
 Sie können generische Klassen, Strukturen, Schnittstellen, Prozeduren und Delegaten definieren und verwenden. Sie können jedoch keine generischen Module definieren.  
  
 **Fehler\-ID:** BC32073  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das `Of`\-Schlüsselwort aus der `Module`\-Anweisung.  
  
2.  Wenn Sie die Funktionalität eines generischen Moduls benötigen, entspricht diesem am ehesten eine generische Klasse. Verwenden Sie eine [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement) statt einer `Module`\-Anweisung.  
  
## Siehe auch  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Gewusst wie: Definieren einer Klasse, die für unterschiedliche Datentypen die gleiche Funktionalität bereitstellen kann](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)