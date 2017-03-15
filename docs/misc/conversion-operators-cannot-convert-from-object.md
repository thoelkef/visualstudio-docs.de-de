---
title: "Konvertierungsoperatoren k&#246;nnen keine Konvertierung von &quot;Object&quot; durchf&#252;hren. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33032"
  - "vbc33032"
helpviewer_keywords: 
  - "BC33032"
ms.assetid: 877f626f-7aa1-41d8-b7ca-eb4337d012d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Konvertierungsoperatoren k&#246;nnen keine Konvertierung von &quot;Object&quot; durchf&#252;hren.
Ein Konvertierungsoperator ist mit einem Parameter vom [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type) deklariert.  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] geht zur Kompilierzeit davon aus, dass eine vordefinierte Konvertierung von jedem Verweistyp in jeden Typ in der Vererbungshierarchie vorhanden ist, d. h. in jeden Typ, von dem der Verweistyp abgeleitet oder der vom Verweistyp abgeleitet werden kann. In [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ist der universelle Datentyp `Object`, daher wird jeder Typ von `Object` abgeleitet.  
  
 Da der Compiler diese Konvertierung als bereits definiert ansieht, lässt er ein erneutes Definieren dieser Konvertierung nicht zu.  
  
 **Fehler\-ID:** BC33032  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie diese Operatordefinition vollständig. Sie ist bereits vordefiniert.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Object als universeller Datentyp \(Visual Basic\)](http://msdn.microsoft.com/de-de/5315bf21-2b22-45ab-98cd-5631dffbcb2f)