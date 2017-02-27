---
title: "Dialogfeld &quot;Debuggen wird abgebrochen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.stopnow"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen wird beendet (Dialogfeld)"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Dialogfeld &quot;Debuggen wird abgebrochen&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dialogfeld wird angezeigt, wenn vom Debugger versucht wird, eine Debugsitzung zu beenden, der Beendigungsvorgang jedoch einige Zeit dauert.  Das Beenden einer Debugsitzung erfolgt normalerweise sehr schnell, sodass dieses Dialogfeld nicht angezeigt wird.  Manchmal dauert es jedoch eine Weile, bis alle derzeit debuggten Prozesse getrennt sind.  Wenn das Beenden der Sitzung mehrere Sekunden dauert \(bzw. ein Fehler beim Trennen auftritt\), wird dieses Dialogfeld angezeigt.  Bei wiederholtem Auftreten kann dies auf ein internes Problem hindeuten. Nehmen Sie ggf. Kontakt zum Produktsupport auf.  
  
 Sie können entweder warten, bis alle Prozesse getrennt sind und dieses Dialogfeld ausgeblendet wird, oder Sie erzwingen über die Schaltfläche **Jetzt beenden** die sofortige Beendigung.  
  
 **Jetzt beenden**  
 Klicken Sie auf diese Schaltfläche, um die Debugsitzung sofort zu beenden.  Durch **Jetzt beenden** werden die debuggten Prozesse beendet, aber nicht getrennt.  Wenn Sie Systemprozesse debuggen und die Prozesse mit **Jetzt beenden** stoppen, kann es zu unerwarteten und unerwünschten Folgen kommen.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/de-de/f2c756c2-8079-474b-94c2-01c19a141a01)