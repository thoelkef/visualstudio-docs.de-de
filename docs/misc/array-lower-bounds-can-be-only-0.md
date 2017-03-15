---
title: "Untere Arraybegrenzung kann nur &#39;0&#39; sein. | Microsoft Docs"
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
  - "bc32059"
  - "vbc32059"
helpviewer_keywords: 
  - "BC32059"
ms.assetid: 273b69df-910e-45d2-acac-632005d24c5a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Untere Arraybegrenzung kann nur &#39;0&#39; sein.
Eine Deklarationsanweisung oder `New`\-Klausel gibt ein Array mit einer unteren Grenze ungleich 0 an.  
  
 Beim Erstellen oder Initialisieren einer Arrayvariablen können Sie optional die obere Grenze der einzelnen Dimensionen angeben. In diesem Fall wird die Länge dieser Dimension zur oberen Grenze, die um den Wert 1 erhöht wird, da die untere Grenze immer 0 \(null\) ist. Optional können Sie auch die untere Grenze angeben, doch Sie müssen hier 0 angeben. Der Vorteil dieser Vorgehensweise besteht darin, dass der Code einfacher zu lesen ist.  
  
 **Fehler\-ID:** BC32059  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Angabe für die untere Grenze in 0, oder entfernen Sie sie vollständig.  
  
## Siehe auch  
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [NOTINBUILD Gewusst wie: Angeben einer unteren Grenze von 0 \(null\) für ein Array](http://msdn.microsoft.com/de-de/20ffd49a-64f7-4634-8ed0-46ba1049d935)