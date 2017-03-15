---
title: "Argument &lt;Argumentname&gt; muss im Bereich zwischen 1 und 255 liegen. | Microsoft Docs"
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
  - "vbrArgument_Range1toFF1"
ms.assetid: a447f9a6-1c90-4c71-abff-81170331e4c5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argument &lt;Argumentname&gt; muss im Bereich zwischen 1 und 255 liegen.
Ein Argument ist ungültig, weil es außerhalb des Bereichs 0 bis 255 liegt.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Argumente im Ausdruck. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erstellen, die mit 0 \(null\) initialisiert wird.  
  
2.  Überprüfen Sie vorherige Operationen für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)