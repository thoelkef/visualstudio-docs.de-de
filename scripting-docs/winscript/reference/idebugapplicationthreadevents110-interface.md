---
title: "IDebugApplicationThreadEvents110-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThreadEvents110-Schnittstelle"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThreadEvents110-Schnittstelle
Fügt mehr Threadereignisse hinzu.  Diese Ereignisse sind nur lokal.  Das heißt, können Sie diese nur im Prozess abonnieren, der, mithilfe des [die IConnectionPoint\-Schnittstelle](http://go.microsoft.com/fwlink/?LinkId=232738) Angemeldete gedebuggt wird und Methoden auf PDM\-Anwendung abzumelden verlegen Sie Objekte \(Objekte, die [IDebugApplicationThread\-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md) implementieren\).  Sie werden auf dem Thread auf, den sie stammen.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Methoden  
 Die `IDebugActivationThreadEvents110`\-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Ein Aufruf in den Thread mit der Threadumschaltung des PDMS wurde gestartet.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Der Thread wird von einem Haltepunkt fort und wird erneut aktiv sein.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Der Thread wird für einen Haltepunkt und kann Aufrufe behandeln, die den Thread benötigen, vollständig belegt werden.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Ein Aufruf in den Thread mit der Threadumschaltung des PDMS abgeschlossen wurde.|