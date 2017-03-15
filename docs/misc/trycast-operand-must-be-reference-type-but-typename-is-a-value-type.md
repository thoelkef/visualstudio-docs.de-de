---
title: "TryCast erfordert einen Verweistyp als Operanden, &quot;&lt;Typname&gt;&quot; ist jedoch ein Werttyp. | Microsoft Docs"
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
  - "BC30792"
  - "vbc30792"
helpviewer_keywords: 
  - "BC30792"
ms.assetid: 3325fce5-dbc0-4d1d-9530-31f4720bfe6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# TryCast erfordert einen Verweistyp als Operanden, &quot;&lt;Typname&gt;&quot; ist jedoch ein Werttyp.
Der `TryCast`\-Operator wird mit einem Werttyp für mindestens eines der Argumente verwendet.  
  
 `TryCast` überprüft, ob eine Vererbungs\- oder Implementierungsbeziehung zwischen den beiden Argumenten vorliegt. Daher sind nur Verweistypen für die Argumente zulässig. Weitere Informationen finden Sie unter [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types).  
  
 **Fehler\-ID:** BC30792  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie `DirectCast` oder `CType`, um die Konvertierung auszuführen. In beiden Fällen sind Werttypen zulässig.  
  
## Siehe auch  
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)