---
title: "Argument &lt;Argumentname&gt; muss im Bereich zwischen 0 und 99 liegen. | Microsoft Docs"
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
  - "vbrArgument_Range0to99_1"
ms.assetid: d9d9a15e-c5ee-4104-9504-b48a4a191415
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argument &lt;Argumentname&gt; muss im Bereich zwischen 0 und 99 liegen.
Ein Argument ist ungültig, weil es außerhalb des Bereichs 0 bis 99 liegt.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Argumente im Ausdruck. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erstellen, die mit 0 \(null\) initialisiert wird.  
  
2.  Überprüfen Sie vorherige Operationen für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)