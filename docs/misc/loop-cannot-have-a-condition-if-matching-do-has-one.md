---
title: "&quot;Loop&quot; kann keine Bedingung haben, wenn das entsprechende &quot;Do&quot; eine Bedingung hat. | Microsoft Docs"
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
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Loop&quot; kann keine Bedingung haben, wenn das entsprechende &quot;Do&quot; eine Bedingung hat.
Eine `Loop`\-Anweisung enthält eine `While`\- oder `Until`\-Klausel, und die entsprechende `Do`\-Anweisung enthält ebenfalls eine solche Klausel. Nur eine der `Do`\- und `Loop`\-Anweisungen können in einer Schleife eine Bedingung angeben.  
  
 **Fehler\-ID:** BC30238  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `While`\- oder `Until`\-Klausel aus der `Do`\-Anweisung oder aus der `Loop`\-Anweisung.  
  
## Siehe auch  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)