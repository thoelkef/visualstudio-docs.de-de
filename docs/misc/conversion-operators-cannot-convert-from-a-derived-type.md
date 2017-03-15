---
title: "Konvertierungsoperatoren k&#246;nnen keine Konvertierung eines abgeleiteten Typs durchf&#252;hren. | Microsoft Docs"
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
  - "bc33031"
  - "vbc33031"
helpviewer_keywords: 
  - "BC33031"
ms.assetid: e8cfef89-9fde-4f33-ab0d-cc2094e8b8eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Konvertierungsoperatoren k&#246;nnen keine Konvertierung eines abgeleiteten Typs durchf&#252;hren.
Ein Konvertierungsoperator ist mit einem Parametertyp deklariert, der aus dem Rückgabetyp abgeleitet wird.  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] geht zur Kompilierzeit davon aus, dass eine vordefinierte Konvertierung von jedem Verweistyp in jeden Typ in der Vererbungshierarchie vorhanden ist, d. h. in jeden Typ, von dem der Verweistyp abgeleitet oder der vom Verweistyp abgeleitet werden kann. Eine solche Konvertierung kann zur Laufzeit einen Fehler verursachen. Der Compiler kann jedoch keine Laufzeitergebnisse vorhersagen, deshalb lässt er das Kompilieren solcher Konvertierungen zu.  
  
 Da der Compiler diese Konvertierung als bereits definiert ansieht, lässt er ein erneutes Definieren dieser Konvertierung nicht zu.  
  
 **Fehler\-ID:** BC33031  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie diese Operatordefinition vollständig. Sie ist bereits vordefiniert.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)