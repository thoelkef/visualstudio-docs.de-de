---
title: "Die Schnittstelle &quot;&lt;Schnittstellenname&gt;&quot; wird nicht von dieser Klasse implementiert. | Microsoft Docs"
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
  - "bc31035"
  - "vbc31035"
helpviewer_keywords: 
  - "BC31035"
ms.assetid: 99ddabb5-20e0-4cf6-a8d4-1ca91f3c7511
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Schnittstelle &quot;&lt;Schnittstellenname&gt;&quot; wird nicht von dieser Klasse implementiert.
Ein Member dieser Klasse oder Struktur versucht, einen Member einer Schnittstelle zu implementieren, die von der Klasse oder Struktur nicht implementiert wird.  
  
 **Fehler\-ID:** BC31035  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie am Anfang der Klasse oder Struktur eine `Implements`\-Anweisung hinzu, damit die passende Schnittstelle implementiert wird.  
  
-   Entfernen Sie das `Implements`\-Schlüsselwort aus dem Member, der diesen Fehler verursacht.  
  
## Siehe auch  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)