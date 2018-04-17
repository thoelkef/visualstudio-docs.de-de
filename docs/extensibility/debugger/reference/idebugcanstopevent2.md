---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48f049648fcbd93d7ad7411a4dfeba8bbdb4431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Diese Schnittstelle wird verwendet, zu dem Sitzung Debug-Manager (SDM) Fragen an, ob an der aktuellen Codeposition beendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle zur Unterstützung der Source Code schrittweise durchlaufen. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss implementiert werden, auf das gleiche Objekt wie diese Schnittstelle (verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle).  
  
 Die Implementierung dieser Schnittstelle muss das SDM-Aufruf der kommunizieren [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) zum Debugging-Modul. Z. B. Dies erreichen Sie mit einer Nachricht an das Debugmodul Meldungsbehandlung-Thread gesendet oder das Objekt implementiert diese Schnittstelle enthalten einen Verweis auf die Debugging-Modul und Rückruf in die Debugging-Modul mit dem Flag übergebenen konnte `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Methode Code jedes Mal, wenn die DE aufgefordert, Ausführung und die DE zu fortfahren durchlaufen wird kann die DE gesendet. Dieses Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM angegeben werden, wenn es an das derzeit debuggte Programm angefügt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugCanStopEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ruft den Grund für dieses Ereignis ab.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Gibt an, ob zu debuggenden Programms an der Position dieses Ereignisses (und senden ein Ereignis, das den Grund für Beendigung beschreibt) beenden oder Fortsetzen der Ausführung werden soll.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ruft den Dokumentenkontext, der den Speicherort der dieses Ereignis beschreibt.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ruft den Codekontext, der den Speicherort der dieses Ereignis beschreibt.|  
  
## <a name="remarks"></a>Hinweise  
 Die DE sendet diese Schnittstelle, die Benutzer Schritte in einer Funktion und die DE findet keine Debuginformationen vorhanden oder Debuginformationen vorhanden ist, aber die DE weiß nicht, wenn der Quellcode für den betreffenden Speicherort angezeigt werden kann.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)