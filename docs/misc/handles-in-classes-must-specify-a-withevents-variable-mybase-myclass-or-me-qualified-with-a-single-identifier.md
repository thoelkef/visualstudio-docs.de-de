---
title: "&#39;Handles&#39; muss in Klassen eine WithEvents-Variable angeben. &#39;MyBase&#39;, &#39;MyClass&#39; oder &#39;Me&#39; wurde durch einen einzelnen Bezeichner qualifiziert. | Microsoft Docs"
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
  - "bc31412"
  - "vbc31412"
helpviewer_keywords: 
  - "BC31412"
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; muss in Klassen eine WithEvents-Variable angeben. &#39;MyBase&#39;, &#39;MyClass&#39; oder &#39;Me&#39; wurde durch einen einzelnen Bezeichner qualifiziert.
Um einen Ereignishandler anzugeben, müssen `Handles`\-Anweisungen entweder eine mit dem Schlüsselwort `WithEvents` deklarierte Objektvariable oder einen mit dem Schlüsselwort `MyBase` qualifizierten Member angeben.  
  
 **Fehler\-ID:** BC31412  
  
### So beheben Sie diesen Fehler  
  
1.  Verwenden Sie den `WithEvents`\-Modifizierer, um die Variablen zu deklarieren, die mit der `Handles`\-Anweisung verwendet werden können.  
  
2.  Geben Sie den Namen eines Ereignisses für die aktuelle Klasse in der Basisklasse an.  
  
## Siehe auch  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)