---
title: "Das Argument &#39;&lt;Argumentname&gt;&#39; ist &#39;Nothing&#39;. | Microsoft Docs"
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
  - "vbrArgument_InvalidNullValue1"
ms.assetid: abbde904-c191-4911-8822-c9dd2f81d616
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Argument &#39;&lt;Argumentname&gt;&#39; ist &#39;Nothing&#39;.
Ein Ausdruck enthält ein NULL\-Argument.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Argumente im Ausdruck. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erstellen, die mit Null initialisiert wird.  
  
2.  Überprüfen Sie vorherige Vorgänge für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Parameter Passing Mechanism for Visual Basic 6.0 Users](http://msdn.microsoft.com/de-de/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)