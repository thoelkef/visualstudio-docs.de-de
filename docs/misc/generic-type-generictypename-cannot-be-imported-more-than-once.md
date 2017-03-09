---
title: "Der generische Typ &lt;Name des generischen Typs&gt; kann nur einmal importiert werden. | Microsoft Docs"
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
  - "BC32086"
  - "vbc32086"
helpviewer_keywords: 
  - "BC32086"
ms.assetid: d93bae4b-3224-4a6e-a072-8ce231084519
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der generische Typ &lt;Name des generischen Typs&gt; kann nur einmal importiert werden.
Eine [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) gibt einen generischen Typ an, der bereits mit einer anderen Typparametrisierung importiert wurde.  
  
 Sie können mehrere konstruierte Typen aus einem generischen Typ deklarieren, weil Sie den generischen Typ durch das Deklarieren eines konstruierten Typs nicht neu definieren. Wenn Sie einen generischen Typ jedoch mehrmals importieren, entspricht dies mehreren Definitionen.  
  
 **Fehler\-ID:** BC32086  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn die Quelldatei, die die `Imports`\-Anweisung enthält, auch eine weitere `Imports`\-Anweisung enthält, die den gleichen generischen Typ angibt, entfernen Sie eine der beiden Anweisungen.  
  
2.  Wenn Sie den gleichen generischen Typ mit anderen Typparametrisierungen importieren müssen, verwenden Sie mehrere Quelldateien.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)