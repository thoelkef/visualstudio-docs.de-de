---
title: "Die indirekte Einschr&#228;nkung &quot;&lt;Einschr&#228;nkung1&gt;&quot; der Typparametereinschr&#228;nkung &quot;&lt;Typparameter1&gt;&quot; steht in Konflikt mit der indirekten Einschr&#228;nkung &quot;&lt;Einschr&#228;nkung2&gt;&quot; der Typparametereinschr&#228;nkung &quot;&lt;Typparameter2&gt;&quot;. | Microsoft Docs"
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
  - "bc32109"
  - "vbc32109"
helpviewer_keywords: 
  - "BC32109"
ms.assetid: 37abd3b4-25dc-4959-8617-ce93a02bbf47
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die indirekte Einschr&#228;nkung &quot;&lt;Einschr&#228;nkung1&gt;&quot; der Typparametereinschr&#228;nkung &quot;&lt;Typparameter1&gt;&quot; steht in Konflikt mit der indirekten Einschr&#228;nkung &quot;&lt;Einschr&#228;nkung2&gt;&quot; der Typparametereinschr&#228;nkung &quot;&lt;Typparameter2&gt;&quot;.
Ein generischer Typ wurde mit Einschränkungen deklariert, die aufgrund einer Kombination aus indirekten Einschränkungen einen Konflikt verursachen.  
  
 Dieser Fehler kann durch die folgende Anweisung generiert werden.  
  
```  
Public Class testClass(Of t1 As {t2, t3}, t2 As Structure, t3 As Class)  
```  
  
 Die indirekten Einschränkungen `Structure` und `Class` verursachen einen Konflikt für Typparameter `t1`, weil die `Structure`\-Einschränkung erfordert, dass das entsprechende Typargument ein Werttyp ist, während `Class` erfordert, dass es ein Verweistyp ist.  
  
 **Fehler\-ID:** BC32109  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Typparametereinschränkungen, um einen Konflikt verursachende Einschränkungen zu vermeiden.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Struktur \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Klasse \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)