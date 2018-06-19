---
title: Haltepunkt-bezogenen Methoden | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce44a7d3d3578d5157bcefcf14172d92ece677d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107289"
---
# <a name="breakpoint-related-methods"></a>Haltepunkt-bezogenen Methoden
Die Einstellung von Haltepunkten muss ein Debugging-Modul (DE) unterstützt werden. Debuggen von Visual Studio unterstützt die folgenden Typen von Haltepunkten:  
  
-   gebunden  
  
     Über die Benutzeroberfläche angefordert und erfolgreich gebunden an einen Speicherort für die angegebene Codepage  
  
-   Ausstehend  
  
     Über die Benutzeroberfläche, aber noch nicht mit tatsächlichen gebundenen Anweisungen angefordert  
  
## <a name="discussion"></a>Diskussion  
 Ein ausstehender Haltepunkt tritt beispielsweise auf, wenn es sich bei die Anweisungen noch nicht geladen werden. Wenn der Code, ausstehenden Haltepunkte, versuchen Sie es an Code am Speicherort vorgeschriebenen, d. h. binden, um die Break-Anweisungen in den Code einfügen geladen wird. Ereignisse werden auf der Sitzungs-Manager (SDM) gesendet, um erfolgreiche Bindung anzugeben oder zu benachrichtigen, dass die Bindung Fehler aufgetreten sind.  
  
 Ein ausstehender Haltepunkt verwaltet auch eine eigene interne Liste der entsprechenden gebundenen Haltepunkte. Ein ausstehender Haltepunkt kann dazu führen, dass das Einfügen von vielen Haltepunkte im Code. Der Visual Studio-debugging UI zeigt eine Strukturansicht der ausstehenden Haltepunkte und die entsprechenden Haltepunkte gebunden.  
  
 Erstellen und Verwenden eines ausstehenden Haltepunkte erfordern die Implementierung der [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Methode als auch die folgenden Methoden der [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstellen.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob ein angegebener ausstehender Haltepunkt an einem Speicherort Code binden können.|  
|[Binden](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Binden ein angegebenes ausstehender Haltepunkt auf eine oder mehrere Codepositionen.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Zustand eines ausstehenden Haltepunkts ab.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft das Haltepunkt-Anforderung verwendet, um ein ausstehender Haltepunkt zu erstellen.|  
|[Aktivieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Zustand eines ausstehenden Haltepunkts an.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Breakpoints, die über ein ausstehender Haltepunkt gebunden.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler Breakpoints, die ein ausstehender Haltepunkt ergeben.|  
|[Löschen](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht ein ausstehender Haltepunkt und alle Breakpoints, die von ihm gebunden.|  
  
 Um die gebundenen Haltepunkte und Fehler Haltepunkte auflisten möchten, müssen Sie die Methoden der implementieren [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) und [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Ausstehender Haltepunkte, die an einen Code binden erfordern Speicherort Implementierung der folgenden [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkts, der einen Haltepunkt enthält.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand eines Haltepunkts gebundenen ab.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die Breakpoint-Lösung, die beschreibt, einen Haltepunkt an.|  
|[Aktivieren](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert einen Haltepunkt.|  
|[Löschen](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht einen gebundenen Haltepunkt an.|  
  
 Auflösung und Anforderung, die Informationen benötigen, die Implementierung der folgenden [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Haltepunkts eine Auflösung dargestellt.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft die breakpointinformationen für die Auflösung, die einen Breakpoint beschreibt.|  
  
 Auflösung von Fehlern, die während der Bindung auftreten erfordert die Implementierung der folgenden [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkts, der einen Haltepunkt auf Fehler enthält.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft die Auflösung der Breakpoint-Fehler, die einen Haltepunkt auf Fehler beschreibt.|  
  
 Auflösung von Fehlern, die während der Bindung auftreten erfordert außerdem die folgenden Methoden der [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ eines Haltepunkts.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ruft die problemlösungsinformationen eines Haltepunkts.|  
  
 Anzeigen des Quellcodes an einem Haltepunkt erfordert, dass Sie die Methoden implementieren [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und/oder die Methoden der [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)