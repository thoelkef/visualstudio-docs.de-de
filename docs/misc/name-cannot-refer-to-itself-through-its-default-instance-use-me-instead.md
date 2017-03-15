---
title: "&quot;&lt;Name&gt;&quot; kann nicht durch die Standardinstanz auf sich selbst verweisen. Verwenden Sie stattdessen &quot;Me&quot;. | Microsoft Docs"
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
  - "vbc31139"
  - "bc31139"
helpviewer_keywords: 
  - "BC31139"
ms.assetid: 459e5d5a-d526-4cd0-934e-96e4e1eb51bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Name&gt;&quot; kann nicht durch die Standardinstanz auf sich selbst verweisen. Verwenden Sie stattdessen &quot;Me&quot;.
Aus einem Formular wurde versucht , auf dieses Formular als Standardinstanz zu verweisen. Dadurch ruft sich möglicherweise das Formular rekursiv selbst auf.  
  
 In den meisten Fällen sollten Sie `Me` und nicht die Standardinstanz verwenden, wenn Sie auf die aktuelle Instanz des Formulars verweisen.  
  
 **Fehler\-ID:** BC31139  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie `Me`, um auf das Objekt zu verweisen.  
  
## Siehe auch  
 [Debugger – Grundlagen](../debugger/debugger-basics.md)