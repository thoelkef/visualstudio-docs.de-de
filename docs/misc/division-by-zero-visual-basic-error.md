---
title: "Division durch 0 (null) (Visual Basic-Fehler) | Microsoft Docs"
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
  - "vbrID11"
ms.assetid: 7dc22e29-8baa-4d82-a1a6-2de64ba9b25d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Division durch 0 (null) (Visual Basic-Fehler)
Der Wert eines Ausdrucks, der als Divisor verwendet wird, ist 0 \(null\).  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Variablen im Ausdruck. Eine falsch geschriebene Variable kann implizit eine numerische Variable erzeugen, die mit 0 \(null\) initialisiert wird.  
  
2.  Überprüfen Sie vorherige Operationen für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [Error Types](/dotnet/visual-basic/programming-guide/language-features/error-types)