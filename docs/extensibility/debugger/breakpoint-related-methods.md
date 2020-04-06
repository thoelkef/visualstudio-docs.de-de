---
title: Breakpoint-bezogene Methoden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739208"
---
# <a name="breakpoint-related-methods"></a>Breakpoint-bezogene Methoden
Ein Debugmodul (DE) muss die Einstellung von Haltepunkten unterstützen. Das Visual Studio-Debuggen unterstützt die folgenden Haltepunktetypen:

- Bound

     Über die Benutzeroberfläche angefordert und erfolgreich an einen angegebenen Codespeicherort gebunden

- Ausstehend

     Über die Benutzeroberfläche angefordert, aber noch nicht an die tatsächlichen Anweisungen gebunden

## <a name="discussion"></a>Diskussion
 Beispielsweise tritt ein ausstehender Haltepunkt auf, wenn die Anweisungen noch nicht geladen sind. Wenn der Code geladen wird, versuchen ausstehende Haltepunkte, code an der vorgeschriebenen Stelle zu binden, d. h. Breakanweisungen in den Code einzufügen. Ereignisse werden an den Sitzungsdebug-Manager (SDM) gesendet, um eine erfolgreiche Bindung anzuzeigen oder um zu benachrichtigen, dass Bindungsfehler aufgetreten sind.

 Ein ausstehender Haltepunkt verwaltet auch seine eigene interne Liste der entsprechenden gebundenen Haltepunkte. Ein ausstehender Haltepunkt kann das Einfügen vieler Haltepunkte in den Code verursachen. Die Visual Studio-Debugbe-Benutzeroberfläche zeigt eine Strukturansicht ausstehender Haltepunkte und der zugehörigen gebundenen Haltepunkte an.

 Das Erstellen und Verwenden ausstehender Haltepunkte erfordert die Implementierung der [IDebugEngine2::CreatePendingBreakpoint-Methode](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) sowie der folgenden Methoden von [IDebugPendingBreakpoint2-Schnittstellen.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob ein angegebener ausstehender Haltepunkt an einen Codespeicherort gebunden werden kann.|
|[Binden](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bindet einen angegebenen ausstehenden Haltepunkt an einen oder mehrere Codespeicherorte.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Status eines ausstehenden Haltepunkts ab.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft die Haltepunktanforderung ab, die zum Erstellen eines ausstehenden Haltepunkts verwendet wird.|
|[Aktivieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Status eines ausstehenden Haltepunkts um.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Zählt alle Haltepunkte auf, die von einem ausstehenden Haltepunkt gebunden sind.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Zählt alle Fehlerhaltepunkte auf, die sich aus einem ausstehenden Haltepunkt ergeben.|
|[Richtlinie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht einen ausstehenden Haltepunkt und alle haltepunkte, die davon gebunden sind.|

 Um die gebundenen Haltepunkte und Fehlerhaltepunkte aufzuzählen, müssen Sie alle Methoden von [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) und [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)implementieren.

 Ausstehende Haltepunkte, die an einen Codespeicherort gebunden werden, erfordern die Implementierung der folgenden [IDebugBoundBreakpoint2-Methoden.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt ab, der einen Haltepunkt enthält.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Status eines gebundenen Haltepunkts ab.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die Haltepunktauflösung ab, die einen Haltepunkt beschreibt.|
|[Aktivieren](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert einen Haltepunkt.|
|[Richtlinie](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht einen gebundenen Haltepunkt.|

 Lösungs- und Anforderungsinformationen erfordern die Implementierung der folgenden [IDebugBreakpointResolution2-Methoden.](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Haltepunkts ab, der durch eine Auflösung dargestellt wird.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen zur Haltepunktauflösung ab, die einen Haltepunkt beschreiben.|

 Die Fehlerbehebung, die während der Bindung auftreten kann, erfordert die Implementierung der folgenden [IDebugErrorBreakpoint2-Methoden.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt ab, der einen Fehlerhaltepunkt enthält.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft die Breakpoint-Fehlerauflösung ab, die einen Fehlerhaltepunkt beschreibt.|

 Die Behebung von Fehlern, die während der Bindung auftreten können, erfordert auch die folgenden Methoden von [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ eines Haltepunkts ab.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ruft die Auflösungsinformationen eines Haltepunkts ab.|

 Wenn Sie den Quellcode an einem Haltepunkt anzeigen, müssen Sie die Methoden von [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und/oder die Methoden von [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungskontrolle und Zustandsbewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
