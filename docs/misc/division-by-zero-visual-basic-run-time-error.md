---
title: "Division durch null (Visual Basic-Laufzeitfehler) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID11"
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Division durch null (Visual Basic-Laufzeitfehler)
Ein Ausdruck, der als Divisor verwendet wird, weist den Wert null auf.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Variablen im Ausdruck. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erstellen, die mit 0 \(null\) initialisiert wird.  
  
2.  Überprüfen Sie vorherige Operationen für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Parameter Passing Mechanism Changes in Visual Basic](http://msdn.microsoft.com/de-de/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)