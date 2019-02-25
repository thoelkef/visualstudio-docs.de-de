---
title: Auf Haltepunkte bezogene Methoden | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd40ac13cf00db2903f9c9dca7cf154572e2b81
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711175"
---
# <a name="breakpoint-related-methods"></a>Auf Haltepunkte bezogene Methoden
Ein Debugmodul (DE) muss die Einstellung von Haltepunkten unterstützen. Debuggen in Visual Studio unterstützt die folgenden Typen von Haltepunkten:

-   Gebunden

     Über die Benutzeroberfläche angefordert und an einem angegebenen Speicherort, erfolgreich gebunden

-   Ausstehend

     Über die Benutzeroberfläche, aber noch nicht mit tatsächlichen gebunden Anweisungen angefordert

## <a name="discussion"></a>Diskussion
 Ein ausstehender Haltepunkt tritt beispielsweise auf, wenn es sich bei die Anweisungen noch nicht geladen werden. Wenn der Code, ausstehenden Haltepunkte, versuchen Sie es, Code an der angegebenen Position zu binden, um die Break-Anweisungen in den Code einfügen geladen wird. Ereignisse werden für die Sitzung Debug-Manager (SDM) gesendet, um erfolgreiche Bindung anzugeben oder zu benachrichtigen, dass die Bindung aufgetreten sind.

 Ein ausstehender Haltepunkt verwaltet auch eine eigene interne Liste der entsprechenden gebundener Haltepunkte. Ein ausstehender Haltepunkt kann dazu führen, dass das Einfügen von vielen Haltepunkte im Code. Visual Studio debugging-Benutzeroberfläche zeigt eine Strukturansicht der ausstehenden Haltepunkte und die entsprechenden Haltepunkte gebunden.

 Erstellen und Verwenden eines ausstehenden Haltepunkte erfordern die Implementierung der [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Methode sowie die folgenden Methoden der [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstellen.

|Methode|Beschreibung|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob ein angegebener ausstehender Haltepunkt an einem codespeicherort binden können.|
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bindet ein angegebenes ausstehender Haltepunkt an einem oder mehreren Code-Speicherorten.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Status eines ausstehenden Haltepunkts ab.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft die Haltepunkt-Anforderung, die zum Erstellen eines ausstehenden Haltepunkts ab.|
|[Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Zustand eines ausstehenden Haltepunkts.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Breakpoints, die von einem ausstehenden Haltepunkt gebunden.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler Haltepunkte, die durch ein ausstehender Haltepunkt verursacht.|
|[Löschen](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht ein ausstehender Haltepunkt und alle Breakpoints, die von ihm gebunden.|

 Zum Auflisten der gebundener Haltepunkte und Fehler Haltepunkte müssen Sie alle Methoden des implementieren [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) und [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Ausstehenden Haltepunkte, die an einen Code binden erfordern Speicherort Implementierung der folgenden [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt, der einen Haltepunkt enthält.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand, der einen gebundenen Haltepunkt.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die haltepunktauflösung, die einen Haltepunkt zu beschreiben.|
|[Enable](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert einen Haltepunkt.|
|[Löschen](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht einen gebundenen Haltepunkt.|

 Auflösung und Informationen erfordern die Implementierung der folgenden Anforderung [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Haltepunkts durch eine Lösung dargestellt.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen der Haltepunkt-Lösung, die einen Haltepunkt zu beschreiben.|

 Lösungen für Fehler, die auftreten können, während der Bindung erfordert die Implementierung der folgenden [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt, der einen Haltepunkt auf Fehler enthält.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft ab, das Haltepunkt-Fehlerbehebung, das einen Haltepunkt auf Fehler beschreibt.|

 Lösungen für Fehler, die auftreten können, während der Bindung erfordert außerdem die folgenden Methoden der [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Methode|Beschreibung|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ eines Haltepunkts.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen der Auflösung eines Haltepunkts.|

 Anzeigen des Quellcodes an einem Haltepunkt erfordert, dass Sie die Methode implementiert [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und/oder die Methoden der [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Siehe auch
- [Ausführung und Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)