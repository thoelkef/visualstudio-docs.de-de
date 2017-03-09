---
title: "Ein indirekter Verweis auf Assembly &lt;Assemblyname&gt;, Version &lt;Nummer einer sp&#228;teren Version&gt; enth&#228;lt &lt;Typname&gt;. | Microsoft Docs"
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
  - "vbc32207"
  - "bc32207"
helpviewer_keywords: 
  - "BC32207"
ms.assetid: a3de74b5-bedd-4e36-b379-485e4b3903f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein indirekter Verweis auf Assembly &lt;Assemblyname&gt;, Version &lt;Nummer einer sp&#228;teren Version&gt; enth&#228;lt &lt;Typname&gt;.
Ein indirekter Verweis auf Assembly \<Assemblyname\>, Version \<Nummer einer späteren Version\> enthält \<Typname\>. Dieses Projekt verweist auf eine frühere Version von \<Assemblyname\> Version \<Nummer einer früheren Version\>. Um \<Typname\> zu verwenden, müssen Sie den Verweis auf \<Assemblyname\> durch Version \<Nummer einer späteren Version\> oder höher ersetzen.  
  
 Ein Ausdruck verweist indirekt auf ein anderes Projekt, das einen Verweis auf eine frühere Version der gleichen Assembly enthält.  
  
 Sie sollten normalerweise nur die neueste Version einer Assembly verwenden.  
  
 **Fehler\-ID:** BC32207  
  
### So beheben Sie diesen Fehler  
  
1.  Verwenden Sie den genanten Typnamen, um zu bestimmen, welches Projekt noch auf dieselbe Assembly verweist.  
  
2.  Bestimmen Sie die Version der Assembly, auf die das andere Projekt verweist, und ändern Sie Ihr Projekt so, dass es auf die gleiche Version verweist.  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)