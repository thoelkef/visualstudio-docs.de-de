---
title: IDebugApplicationThread110-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726350"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110-Schnittstelle
Bietet mehr Funktionen für die [IDebugApplicationThread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md) Schnittstelle.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugApplicationThread110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Stellt einen asynchronen Aufruf im Hauptthread an.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Die Anzahl der, wie viele Threadanforderungen von der PDM Thread wechseln Mechanismen gerade verarbeitet werden. In der Regel's 0 oder 1, aber sie möglich, dass diese Option, um die höher sein, wenn ein Thread Aufruf Verarbeitung gestartet wurde, jedoch wird, einen synchronen Aufruf nicht genügend Threads ausgelöst oder andernfalls hält den Thread (z. B. durch das Auslösen eines IDebugApplicationEvents-Ereignisses, das auf der Debugger ausgegeben wird Thread)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) in diesem Thread aufgerufen wurde und noch nicht abgeschlossen.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Dieser Thread befindet sich in einem Zustand, der Aufrufe, die mithilfe der PDM Threads wechseln Mechanismen (z. B. SynchronousCallInThread) verarbeiten kann.|