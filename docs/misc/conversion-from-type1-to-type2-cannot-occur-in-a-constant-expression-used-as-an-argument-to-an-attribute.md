---
title: "Eine Konvertierung von &quot;&lt;Typ1&gt;&quot; in &quot;&lt;Typ2&gt;&quot; kann nicht in einem konstanten Ausdruck durchgef&#252;hrt werden, der als Argument f&#252;r ein Attribut verwendet wird. | Microsoft Docs"
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
  - "bc30934"
  - "vbc30934"
helpviewer_keywords: 
  - "BC30934"
ms.assetid: 120e05f9-1d0e-4800-b05c-a8373e286b9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Konvertierung von &quot;&lt;Typ1&gt;&quot; in &quot;&lt;Typ2&gt;&quot; kann nicht in einem konstanten Ausdruck durchgef&#252;hrt werden, der als Argument f&#252;r ein Attribut verwendet wird.
Ein für ein Attributargument verwendeter Ausdruck wird als Datentyp ausgewertet, der sich von dem des entsprechenden Attributparameters unterscheidet, und [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lässt die erforderliche Typkonvertierung für Attributargumente nicht zu.  
  
 Ein Attribut stellt Metadaten für das Element bereit, auf das es angewendet wird, und der Compiler muss zur Kompilierzeit in der Lage sein, alle Metadaten zu erstellen. Daher muss jedes Attribut Werte verwenden, die zur Kompilierzeit konstant sind, und jedes Attributargument muss als ein zur Kompilierzeit konstanter Wert ausgewertet werden.  
  
 Bei bestimmten Typkonvertierungen können keine Werte erzeugt werden, die zur Kompilierzeit konstant sind. Ob beispielsweise `String` in `Double` oder `Date` konvertiert wird, hängt von der Gebietsschemaeinstellung zur Laufzeit ab. Andere Konvertierungen \(z. B. die Konvertierung eines Array eines abgeleiteten Typs in ein `Object`\-Array\) verursachen eine Vielzahl von Problemen, durch die der Compiler sie für Attributargumente nicht zulassen kann.  
  
 **Fehler\-ID:** BC30934  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie einen Ausdruck, der als gleicher Datentyp wie der entsprechende Parameter ausgewertet wird, wie vom Attribut definiert.  
  
## Siehe auch  
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)