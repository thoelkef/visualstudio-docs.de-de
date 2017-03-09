---
title: "Ein IsNot-Operand vom Typ &lt;Typparametername&gt; kann nur mit „Nothing“ verglichen werden, da &lt;Typparametername&gt; ein Typparameter ohne Klasseneinschr&#228;nkung ist. | Microsoft Docs"
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
  - "vbc32097"
  - "bc32097"
helpviewer_keywords: 
  - "BC32097"
ms.assetid: 50283a4b-70e3-4e59-9b9b-65e7cacf5ce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein IsNot-Operand vom Typ &lt;Typparametername&gt; kann nur mit „Nothing“ verglichen werden, da &lt;Typparametername&gt; ein Typparameter ohne Klasseneinschr&#228;nkung ist.
Ein Typparameter wird als Operand für den [IsNot Operator](/dotnet/visual-basic/language-reference/operators/isnot-operator) verwendet, wenn der Typparameter ohne das [Class\-Schlüsselwort \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) oder einen bestimmten Klassennamen in der Einschränkungsliste definiert wird.  
  
 `IsNot` vergleicht zwei Verweistypen, um zu bestimmen, ob sie auf unterschiedliche Objektinstanzen im Arbeitsspeicher verweisen. Ein Operand, der kein Verweistyp ist, wird nicht akzeptiert, es sei denn, der andere Operand ist [Nothing](/dotnet/visual-basic/language-reference/nothing).  
  
 **Fehler\-ID:** BC32097  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie festlegen können, dass das für diesen Typparameter angegebene Typargument immer ein Verweistyp sein muss, fügen Sie entweder das `Class`\-Schlüsselwort oder einen bestimmten Klassennamen zur Einschränkungsliste für den Typparameter hinzu.  
  
-   Wenn Sie nicht festlegen können, dass das für diesen Typparameter angegebene Typargument immer ein Verweistyp sein muss, entfernen Sie es aus dem `IsNot`\-Ausdruck. Sie können es nicht mithilfe des `IsNot`\-Operators mit anderen Verweistypen vergleichen.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)