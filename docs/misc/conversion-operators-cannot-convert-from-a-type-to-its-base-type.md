---
title: "Konvertierungsoperatoren k&#246;nnen keine Konvertierung eines Typ in den Basistyp durchf&#252;hren | Microsoft Docs"
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
  - "bc33026"
  - "vbc33026"
helpviewer_keywords: 
  - "BC33026"
ms.assetid: 3533cf71-6a52-4fd0-a1f2-127c4ecd56ae
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Konvertierungsoperatoren k&#246;nnen keine Konvertierung eines Typ in den Basistyp durchf&#252;hren
Ein Konvertierungsoperator wird mit einem Rückgabetyp deklariert, von dem der Parametertyp abgeleitet wird.  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] geht zur Kompilierzeit davon aus, dass eine vordefinierte Konvertierung von jedem Verweistyp in jeden Typ in der Vererbungshierarchie vorhanden ist, d. h. in jeden Typ, von dem der Verweistyp abgeleitet oder der vom Verweistyp abgeleitet werden kann. Eine solche Konvertierung kann zur Laufzeit einen Fehler verursachen. Der Compiler kann jedoch keine Laufzeitergebnisse vorhersagen, deshalb lässt er das Kompilieren solcher Konvertierungen zu.  
  
 Da der Compiler diese Konvertierung als bereits definiert ansieht, lässt er ein erneutes Definieren dieser Konvertierung nicht zu.  
  
 **Fehler\-ID:** BC33026  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie diese Operatordefinition vollständig. Sie ist bereits vordefiniert.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)