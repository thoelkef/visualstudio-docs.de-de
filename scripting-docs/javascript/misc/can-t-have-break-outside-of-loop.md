---
title: "&quot;break&quot; ist au&#223;erhalb der Schleife unzul&#228;ssig | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# &quot;break&quot; ist au&#223;erhalb der Schleife unzul&#228;ssig
Sie haben versucht, das **break**\-Schlüsselwort außerhalb einer Schleife zu verwenden.  Das **break**\-Schlüsselwort wird verwendet, um eine Schleife oder eine `switch`\-Anweisung zu beenden.  Es muss im Text einer Schleife oder in der `switch`\-Anweisung eingebettet sein.  Ein **label** kann jedoch dem Unterbrechungsschlüsselwort folgen.  
  
```  
break labelname;  
```  
  
 Sie benötigen nur das beschriftete Formular des **break**\-Schlüsselworts, wenn Sie geschachtelte Schleifen oder `switch`\-Anweisungen verwenden und eine Schleife unterbrechen müssen, die nicht die innerste ist.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass das **break**\-Schlüsselwort innerhalb einer einschließenden Schleife oder einer switch\-Anweisung angezeigt wird.  
  
## Siehe auch  
 [break\-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Steuerung des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)