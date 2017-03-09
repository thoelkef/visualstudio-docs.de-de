---
title: "Das Argument &quot;&lt;Argumentname&gt;&quot; muss gr&#246;&#223;er als oder gleich 0 (null) sein. | Microsoft Docs"
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
  - "vbrFinancial_ArgGEZero1"
ms.assetid: 7b901c2a-3447-4afc-91f8-8fa5f6f961d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Argument &quot;&lt;Argumentname&gt;&quot; muss gr&#246;&#223;er als oder gleich 0 (null) sein.
Ein Argument ist ungültig, da es kleiner als 0 \(null\) ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Argumente. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erzeugen, die mit 0 \(null\) initialisiert wird.  
  
2.  Überprüfen Sie vorherige Operationen für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Parameter Passing Mechanism Changes in Visual Basic](http://msdn.microsoft.com/de-de/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)