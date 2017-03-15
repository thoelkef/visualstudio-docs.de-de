---
title: "Der Typ &#39;&lt;Typname&gt;&#39; muss den Operator &#39;&lt;Operator&gt;&#39; definieren, der in einer For-Anweisung verwendet werden soll. | Microsoft Docs"
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
  - "vbc33038"
  - "BC33038"
helpviewer_keywords: 
  - "BC33038"
ms.assetid: b1c9d87f-80f9-4c8c-8908-f8400b9fe4c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &#39;&lt;Typname&gt;&#39; muss den Operator &#39;&lt;Operator&gt;&#39; definieren, der in einer For-Anweisung verwendet werden soll.
Eine `For`\-Schleife gibt eine Indikatorvariable eines Typs an, der einen erforderlichen Operator nicht unterstützt.  
  
 Die Indikatorvariable in einer `For`\-Schleife kann einen beliebigen Datentyp aufweisen, der alle folgenden Operatoren unterstützt:  
  
-   Größer oder gleich \(`>=`\)  
  
-   Kleiner oder gleich \(`<=`\)  
  
-   Addition \(`+`\)  
  
-   Subtraktion \(`-`\)  
  
 Wenn Sie für die Indikatorvariable einen numerischen Datentyp verwenden, werden alle vorherigen Operatoren unterstützt. Wenn Sie eine benutzerdefinierte Klasse oder Struktur verwenden, müssen Sie alle vorherigen Operatoren für diese Klasse oder Struktur definieren.  
  
 Beachten Sie auch, dass die Datentypen der Ausdrücke `start`, `end` und `step` in der `For`\-Anweisung in den Datentyp der Indikatorvariablen erweitert werden. Wenn die Indikatorvariable eine benutzerdefinierte Klasse oder Struktur ist und der `start`\-, `end`\- oder `step`\-Ausdruck einen anderen Typ aufweist, müssen Sie den `CType`\-Konvertierungsoperator definieren, um die erforderliche Konvertierung auszuführen.  
  
 **Fehler\-ID:** BC33038  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Datentyp der Indikatorvariablen richtig geschrieben ist.  
  
2.  Wenn Sie für die Indikatorvariable eine benutzerdefinierte Klasse oder Struktur verwenden, definieren Sie alle erforderlichen Operatoren für diese Klasse oder Struktur.  
  
3.  In Abhängigkeit von den Datentypen der `start`\-, `end`\- und `step`\-Ausdrücke müssen Sie möglicherweise eine oder mehrere `CType`\-Konvertierungsoperatoren definieren, um sie in den Datentyp der Indikatorvariablen zu konvertieren.  
  
## Siehe auch  
 [For...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function)