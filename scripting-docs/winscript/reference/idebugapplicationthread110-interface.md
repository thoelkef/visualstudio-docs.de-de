---
title: "IDebugApplicationThread110-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110-Schnittstelle"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThread110-Schnittstelle
Enthält zusätzliche Funktionen für die [IDebugApplicationThread\-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)\-Schnittstelle bereit.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Methoden  
 Die `IDebugApplicationThread110`\-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Führt einen asynchronen Aufruf im Hauptausführungsthread auf.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Eine Anzahl, wie viele aufruft, Anforderungen von den Thread\-Umschaltungsmechanismen des PDMS verarbeiten nur.  Normalerweise 0 oder 1, aber es ist möglich, um dieses höher sein, wenn ein Threadaufruf Verarbeitung beginnt, jedoch Trigger ein synchrones auszurufen des Threads oder enthält andernfalls den Thread an \(beispielsweise, durch das Starten eines IDebugApplicationEvents\-Ereignisses, das auf dem Debuggerthread ausgegeben wird\)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) wurde um diesem Thread aufgerufen wurde und noch nicht abgeschlossen.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Dieser Thread befindet sich in einem Zustand, der die Aufrufe verarbeiten kann, die mithilfe der Thread\-Umschaltungsmechanismen des PDMS gemacht werden \(z SynchronousCallInThread\).|