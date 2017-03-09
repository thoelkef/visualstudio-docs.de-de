---
title: "Ein anderes Ereignisprotokoll hat bereits eine Quelle mit diesem Namen registriert. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein anderes Ereignisprotokoll hat bereits eine Quelle mit diesem Namen registriert.
Es wurde versucht, einen Eintrag in ein Ereignisprotokoll schreiben, bei dem die angegebene Quelle für ein anderes Ereignisprotokoll registriert ist.  
  
 Sie müssen die <xref:System.Diagnostics.EventLog.Source%2A>\-Eigenschaft Ihrer <xref:System.Diagnostics.EventLog>\-Komponenteninstanz festlegen, bevor die Komponente einen Eintrag in ein Protokoll schreibt. In diesem Fall überprüft das System, ob die angegebene Quelle mit dem Ereignisprotokoll registriert ist, in das die Komponente schreibt. Bei Bedarf wird dann <xref:System.Diagnostics.EventLog.CreateEventSource%2A> aufgerufen.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Zuordnung der Quelle zum ersten Protokoll mithilfe der <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>\- oder <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>\-Methode.  
  
2.  Registrieren Sie die Quelle für das neue Protokoll.  
  
## Siehe auch  
 [My.Application.Log\-Objekt](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/de-de/bc66c900-4b8a-426a-b8e2-17031a20167e)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/de-de/948ff920-a739-4e66-a191-ee951512d42c)