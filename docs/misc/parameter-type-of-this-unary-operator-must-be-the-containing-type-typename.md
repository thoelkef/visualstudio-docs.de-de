---
title: "Der Parametertyp dieses un&#228;ren Operators muss dem enthaltenden Typ &quot;&lt;Typname&gt;&quot; entsprechen. | Microsoft Docs"
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
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Parametertyp dieses un&#228;ren Operators muss dem enthaltenden Typ &quot;&lt;Typname&gt;&quot; entsprechen.
Eine Definition eines unären Operators gibt einen Parameter mit einem anderen Typ als dem der Klasse oder Struktur an, in der der Operator definiert ist.  
  
 Wenn Sie einen Operator in einer Klasse oder Struktur definieren, muss mindestens einer der Parameter mit dem Typ dieser Klasse bzw. Struktur übereinstimmen. Bei einem unären Operator muss der einzige Operand mit dem Typ der betreffenden Klasse oder Struktur übereinstimmen.  
  
 **Fehler\-ID:** BC33020  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Parametertyp in den Typ der Klasse oder Struktur, in der der Operator definiert ist.  
  
-   Wenn für den Parameter ein Datentyp akzeptiert und im Ergebnis der Operation ein anderer Datentyp zurückgegeben werden soll, definieren Sie stattdessen einen Konvertierungsoperator.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)