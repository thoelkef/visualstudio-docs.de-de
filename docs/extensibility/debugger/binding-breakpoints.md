---
title: Binden von Haltepunkten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34914f382ded8dc7fbea4db49517c17024a8e3a9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720652"
---
# <a name="bind-breakpoints"></a>Binden von Haltepunkten
Wenn der Benutzer einen Haltepunkt, z. B. durch Drücken von **F9**, die IDE die Anforderung formuliert und werden aufgefordert, die Debugsitzung, um den Haltepunkt zu erstellen.

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen
 Festlegen eines Haltepunkts ist ein zweistufiger Prozess, da der Code oder Daten, die vom Haltepunkt betroffenen noch möglicherweise nicht verfügbar. Zunächst muss der Haltepunkt beschrieben, und klicken Sie dann, wie Code oder Daten verfügbar ist, es muss gebunden sein Code oder Daten, wie folgt:

1.  Der Haltepunkt wird angefordert, aus dem relevanten Debug-Engines (DEs), und klicken Sie dann wird der Haltepunkt Code oder an Daten gebunden, sobald diese verfügbar werden.

2.  Die Haltepunkt-Anforderung wird an die Debug-Sitzung gesendet, diese an alle relevanten DEs sendet. Alle, die auswählt, behandeln den Haltepunkt DE erstellt eine entsprechende ausstehender Haltepunkt.

3.  Die Debugsitzung ausstehenden Haltepunkte sammelt und sendet sie an das debugpaket (der Komponente Debuggen von Visual Studio).

4.  Das debugpaket fordert die Debugsitzung, um den ausstehenden Haltepunkt an Code oder Daten zu binden. Die Debugsitzung sendet diese Anforderung an alle relevanten DEs.

5.  Wenn die DE können den Haltepunkt gebunden ist, sendet sie an, dass ein Haltepunkt-Ereignis an die Debug-Sitzung gebunden. Wenn dies nicht der Fall ist, sendet er stattdessen ein Haltepunkt-Error-Ereignis.

## <a name="pending-breakpoints"></a>Ausstehenden Haltepunkte
 Ein ausstehender Haltepunkt kann an mehreren Standorten von Code binden. Beispielsweise kann eine Zeile des Quellcodes für eine C++-Vorlage an jede Codesequenz, die von der Vorlage generiert binden. Eine gebundene Haltepunktereignis können die Debugsitzung aufzählen die Codekontexte an einen Haltepunkt gebunden ist, zu dem Zeitpunkt, der das Ereignis gesendet wurde. Weitere Codekontexte können später gebunden werden, damit die DE senden kann, dass mehrere Haltepunkt Ereignisse für jede bindungsanforderung gebunden. Eine bereitgestellten Kompatibilitätsrichtlinie sollte jedoch nur eine Haltepunkt-Error-Ereignis pro bindungsanforderung senden.

## <a name="implementation"></a>Implementierung
 Programmgesteuert, das debugpaket Sitzung Debug-Manager (SDM) aufgerufen, und weist ihm eine [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) -Schnittstelle, die dient als Wrapper für eine [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) -Struktur, die beschreibt, die der Haltepunkt festgelegt werden. Obwohl Haltepunkte viele Formen aufweisen können, werden sie letztlich in einen Kontext Code- oder Datenmenge aufgelöst.

 Das SDM übergibt diesen Aufruf auf jeden relevanten DE durch einen Aufruf der [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Methode. Die DE gewählt, die den Haltepunkt zu behandeln, erstellt und gibt eine [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstelle. Die SDM erfasst diese Schnittstellen und übergibt sie an das debugpaket als einzelnes `IDebugPendingBreakpoint2` Schnittstelle.

 Bisher wurden keine Ereignisse generiert.

 Das debugpaket anschließend versucht, den ausstehenden Haltepunkt auf Code oder Daten durch den Aufruf zu binden [binden](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), die durch die DE implementiert wird.

 Wenn der Haltepunkt gebunden ist, sendet der DE eine [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) Senkenereignis-Schnittstelle, um das debugpaket. Die Debug-Paket verwendet, die diese Schnittstelle zum Aufzählen von allen Code-Kontexten (oder der Datenkontext für die einzelnen) bis zum Haltepunkt gebunden sein, durch den Aufruf [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), womit eine oder mehrere [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Schnittstellen. Die [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) -Schnittstelle gibt eine [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) -Schnittstelle und [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) gibt eine [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Union, die den Code- oder Datenmenge-Kontext.

 Wenn die DE kann nicht den Haltepunkt gebunden ist, sendet er eine einzelne [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) Senkenereignis-Schnittstelle, um das debugpaket. Das debugpaket Ruft den Fehlertyp (Fehler oder Warnung) und eine informative Meldung, die durch den Aufruf [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), gefolgt von [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) und [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Dies gibt eine [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur, die dem Fehlertyp und der Meldung enthält.

 Wenn eine bereitgestellten Kompatibilitätsrichtlinie einen Haltepunkt behandelt, aber es nicht werden gebunden kann, wird einen Fehler vom Typ `BPET_TYPE_ERROR`. Das debugpaket reagiert, indem ein Fehlerdialogfeld angezeigt, und die IDE fügt ein Ausrufezeichen-Symbol in das breakpointsymbol links von der Quellcodezeile.

 Wenn eine bereitgestellten Kompatibilitätsrichtlinie behandelt einen Haltepunkt, kann nicht gebunden werden, sondern eine andere DE binden kann, dann wird eine Warnung zurückgegeben. Die IDE reagiert, indem Sie eine Frage-Symbol in das breakpointsymbol links von der Quellcodezeile zu platzieren.

## <a name="see-also"></a>Siehe auch
- [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)