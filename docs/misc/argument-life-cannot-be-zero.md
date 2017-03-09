---
title: "Das Argument &#39;Life&#39; kann nicht 0 (null) sein. | Microsoft Docs"
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
  - "vbrFinancial_LifeNEZero"
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Argument &#39;Life&#39; kann nicht 0 (null) sein.
Ein Argument für `Life`, das vom Typ `Double` sein muss und die Länge der Nutzungsdauer der Ressource angibt, ist ungültig.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Schreibweise der Argumente im Ausdruck. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erstellen, die mit Null initialisiert wird.  
  
-   Überprüfen Sie vorherige Vorgänge für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [NICHT IM BUILD: DDB\-Funktion](http://msdn.microsoft.com/de-de/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [NICHT IM BUILD: SYD\-Funktion](http://msdn.microsoft.com/de-de/23c25672-f5dd-49ac-9893-4faa82634181)   
 [NICHT IM BUILD: SLN\-Funktion](http://msdn.microsoft.com/de-de/8e06130a-056e-4266-a8a9-1592b86f58d2)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)