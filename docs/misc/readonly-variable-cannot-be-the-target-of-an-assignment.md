---
title: "ReadOnly-Variable kann nicht das Ziel einer Zuweisung sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30064"
  - "bc30064"
helpviewer_keywords: 
  - "BC30064"
ms.assetid: 17e0751d-4c22-40b2-bb07-cb5c845dbc30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReadOnly-Variable kann nicht das Ziel einer Zuweisung sein.
Eine `ReadOnly`\-Eigenschaft wurde in einem Kontext gefunden, in dem ihr einen Wert zugewiesen wird. Nur schreibbaren Variablen, Eigenschaften und Arrayelementen können während der Ausführung Werte zugewiesen werden.  
  
 **Fehler\-ID:** BC30064  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `ReadOnly`\-Schlüsselwort aus der `Dim`\-Anweisung, die die Variable deklariert, oder entfernen Sie die Anweisung, die ihr einen Wert zuweist.  
  
## Siehe auch  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)