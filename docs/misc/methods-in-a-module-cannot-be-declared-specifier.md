---
title: "Methoden in einem Modul k&#246;nnen nicht als &#39;&lt;Spezifizierer&gt;&#39; deklariert werden. | Microsoft Docs"
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
  - "bc30433"
  - "vbc30433"
helpviewer_keywords: 
  - "BC30433"
ms.assetid: e9fa204c-a40f-439e-95bb-048a89a19159
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methoden in einem Modul k&#246;nnen nicht als &#39;&lt;Spezifizierer&gt;&#39; deklariert werden.
Sie haben einen Spezifizierer verwendet, der für eine Methode innerhalb einer `Module`\-Anweisung ungültig ist. Module können nie instanziiert werden, unterstützen keine Vererbung und können keine Schnittstellen implementieren.  
  
 **Fehler\-ID:** BC30433  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Spezifizierer.  
  
## Siehe auch  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)