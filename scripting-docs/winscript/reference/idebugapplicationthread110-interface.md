---
title: IDebugApplicationThread110-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 44df7168c241c9a750354e1a603d6c5ba96dabd2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440539"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110-Schnittstelle
Stellt weitere Funktionen für die [IDebugApplicationThread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md) Schnittstelle.  
  
> [!IMPORTANT]
> Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugApplicationThread110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Führt einen asynchronen Aufruf im Hauptthread verarbeitet.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Die Anzahl der, wie viele Threadanforderungen von Mechanismen für das PDM Threadwechsel gerade verarbeitet werden. In der Regel ist 0 oder 1, aber es möglich, dass diese Option, um die höher sein, wenn ein Thread-Aufruf Verarbeitung gestartet wurde, aber einen synchronen Aufruf aus dem Thread löst oder hält andernfalls den Thread (z. B. durch das Auslösen eines IDebugApplicationEvents-Ereignisses, das für den Debugger ausgegeben wird Thread)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) für diesen Thread aufgerufen wurde und noch nicht abgeschlossen.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Dieser Thread befindet sich in einem Zustand, der Aufrufe, die über das PDM Threadwechsel Mechanismen (z. B. SynchronousCallInThread) verarbeiten kann.|