---
title: "&quot;&lt;Modifizierer&gt;&quot; ist in einer Delegatdeklaration ung&#252;ltig | Microsoft Docs"
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
  - "bc30385"
  - "vbc30385"
helpviewer_keywords: 
  - "BC30385"
ms.assetid: cacbcdc7-dca9-4a22-b3bf-7e264308c031
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Modifizierer&gt;&quot; ist in einer Delegatdeklaration ung&#252;ltig
Sie haben versucht, einen Modifizierer \(wie z. B. `Shared`\) in einer Delegatdeklaration zu verwenden. Delegaten sind Objekte, mit denen die Methoden anderer Objekte aufgerufen werden. Dazu wird ein Konstruktor definiert, dem die Angabe einer Objektmethode übergeben wird. Ein Modifizierer darf nicht für eine Delegatdeklaration angegeben werden.  
  
 **Fehler\-ID:** BC30385  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den Modifizierer.  
  
## Siehe auch  
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [How to: Invoke a Delegate Method](../Topic/How%20to:%20Invoke%20a%20Delegate%20Method%20\(Visual%20Basic\).md)