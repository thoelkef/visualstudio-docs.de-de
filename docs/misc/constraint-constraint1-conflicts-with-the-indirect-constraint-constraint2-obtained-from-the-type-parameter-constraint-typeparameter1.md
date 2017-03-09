---
title: "Die Einschr&#228;nkung &#39;&lt;Einschr&#228;nkung1&gt;&#39; steht mit der indirekten Einschr&#228;nkung &#39;&lt;Einschr&#228;nkung2&gt;&#39; in Konflikt, die von der Typparametereinschr&#228;nkung &#39;&lt;Typparameter1&gt;&#39; abgerufen wurde. | Microsoft Docs"
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
  - "bc32110"
  - "vbc32110"
helpviewer_keywords: 
  - "BC32110"
ms.assetid: e799214d-23b4-4a3f-b61a-0b9d3387ead3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Einschr&#228;nkung &#39;&lt;Einschr&#228;nkung1&gt;&#39; steht mit der indirekten Einschr&#228;nkung &#39;&lt;Einschr&#228;nkung2&gt;&#39; in Konflikt, die von der Typparametereinschr&#228;nkung &#39;&lt;Typparameter1&gt;&#39; abgerufen wurde.
Ein generischer Typ wird aufgrund einer Kombination aus direkten und indirekten Einschränkungen mit im Konflikt stehenden Einschränkungen deklariert.  
  
 Dieser Fehler kann durch die folgende Anweisung generiert werden.  
  
 `Public Class testClass(Of t1 As {Structure, t2}, t2 As Class)`  
  
 Die direkte Einschränkung `Structure` und die indirekte Einschränkung `Class` verursachen einen Konflikt für Typparameter `t1`, weil die `Structure`\-Einschränkung erfordert, dass das entsprechende Typargument ein Werttyp ist, während `Class` erfordert, dass es ein Verweistyp ist.  
  
 **Fehler\-ID:** BC32110  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Typparametereinschränkungen, um einen Konflikt verursachende Einschränkungen zu vermeiden.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Struktur \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Class \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)