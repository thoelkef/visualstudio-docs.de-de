---
title: "TryCast-Operanden m&#252;ssen Typparameter mit Klasseneinschr&#228;nkung sein, aber &quot;&lt;Typparametername&gt;&quot; hat keine Klasseneinschr&#228;nkung. | Microsoft Docs"
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
  - "BC30793"
  - "vbc30793"
helpviewer_keywords: 
  - "BC30793"
ms.assetid: a38a1da9-4413-4a69-a2ce-0b6d51c2c4ef
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# TryCast-Operanden m&#252;ssen Typparameter mit Klasseneinschr&#228;nkung sein, aber &quot;&lt;Typparametername&gt;&quot; hat keine Klasseneinschr&#228;nkung.
Der [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)\-Operator wird mit einem Operanden und Typparameter verwendet, der nicht unbedingt ein Verweistyp ist.  
  
 `TryCast` kann nur bei Verweistypen, z. B. Klassen oder Schnittstellen, verwendet werden. Wenn Sie einen Typparameter als Argument an `TryCast` übergeben, müssen Sie den Typparameter auf den Verweistyp einschränken. Dazu können Sie eines oder mehrere der folgenden Elemente in die Einschränkungsliste des Typparameters aufnehmen:  
  
-   Ein oder mehrere Schnittstellennamen \(alle müssen mit dem Typargument implementiert werden\)  
  
-   Maximal ein Klassenname \(das Typargument muss von ihm erben\)  
  
-   Die Einschränkung "[New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)" \(das Typargument muss einen parameterlosen Konstruktor aufweisen, auf den der erstellende Code zugreifen kann, und muss daher eine Klasse sein\)  
  
-   Die Einschränkung [Classe \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) \(das Typargument muss ein Verweistyp sein\)  
  
 **Fehler\-ID:** BC30793  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie diesen Typparameter an `TryCast` übergeben müssen, schränken Sie ihn mithilfe einer oder mehrerer Einschränkungen aus obiger Liste ein.  
  
-   Wenn Sie den Typparameter nicht soweit einschränken können, dass er nur den Verweistyp akzeptiert, können Sie ihn mit `TryCast` nicht verwenden. Vielleicht bietet sich stattdessen die [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function) an.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)