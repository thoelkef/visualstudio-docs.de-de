---
title: Bindung spannen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739232"
---
# <a name="bind-breakpoints"></a>Binden von Haltepunkten
Wenn der Benutzer einen Haltepunkt festlegt, z. B. durch Drücken von **F9**, formuliert die IDE die Anforderung und fordert die Debugsitzung auf, den Haltepunkt zu erstellen.

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen
 Das Festlegen eines Haltepunkts ist ein zweistufiger Prozess, da der vom Haltepunkt betroffene Code oder die vom Haltepunkt betroffenen Daten möglicherweise noch nicht verfügbar sind. Zuerst muss der Haltepunkt beschrieben werden, und dann, wenn Code oder Daten verfügbar werden, muss er wie folgt an diesen Code oder diese Daten gebunden sein:

1. Der Haltepunkt wird von den entsprechenden Debugmodulen (DEs) angefordert, und dann wird der Haltepunkt an den Code oder die Daten gebunden, sobald er verfügbar ist.

2. Die Haltepunktanforderung wird an die Debugsitzung gesendet, die sie an alle relevanten DEs sendet. Jede DE, die den Haltepunkt behandelt, erstellt einen entsprechenden ausstehenden Haltepunkt.

3. Die Debugsitzung sammelt die ausstehenden Haltepunkte und sendet sie zurück an das Debugpaket (die Debugkomponente von Visual Studio).

4. Das Debugpaket fordert die Debugsitzung auf, den ausstehenden Haltepunkt an Code oder Daten zu binden. Die Debugsitzung sendet diese Anforderung an alle relevanten DEs.

5. Wenn die DE in der Lage ist, den Haltepunkt zu binden, sendet sie ein Haltepunktgebundenes Ereignis zurück an die Debugsitzung. Ist dies nicht der Fall, wird stattdessen ein Breakpoint-Fehlerereignis gesendet.

## <a name="pending-breakpoints"></a>Ausstehende Haltepunkte
 Ein ausstehender Haltepunkt kann an mehrere Codespeicherorte gebunden werden. Beispielsweise kann eine Zeile mit Quellcode für eine C++-Vorlage an jede Codesequenz gebunden werden, die aus der Vorlage generiert wird. Die Debugsitzung kann ein Haltepunktgebundenes Ereignis verwenden, um die Codekontexte aufzuzählen, die zum Zeitpunkt der Sendezeit an einen Haltepunkt gebunden sind. Weitere Codekontexte können später gebunden werden, sodass die DE möglicherweise mehrere Haltepunktgebundene Ereignisse für jede Bindungsanforderung sendet. Eine DE sollte jedoch nur ein Breakpoint-Fehlerereignis pro Bindungsanforderung senden.

## <a name="implementation"></a>Implementierung
 Programmgesteuert ruft das Debugpaket den Sitzungsdebug-Manager (SDM) auf und gibt ihm eine [IDebugBreakpointRequest2-Schnittstelle,](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) die eine [BP_REQUEST_INFO-Struktur](../../extensibility/debugger/reference/bp-request-info.md) umschließt, die den festzulegenden Haltepunkt beschreibt. Obwohl Haltepunkte von vielen Formen sein können, werden sie letztendlich in einen Code- oder Datenkontext aufgelöst.

 Das SDM übergibt diesen Aufruf an jede relevante DE, indem es seine [CreatePendingBreakpoint-Methode](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) aufruft. Wenn die DE den Haltepunkt verarbeitet, erstellt und gibt sie eine [IDebugPendingBreakpoint2-Schnittstelle](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) zurück. Das SDM sammelt diese Schnittstellen und übergibt sie als `IDebugPendingBreakpoint2` einzelne Schnittstelle an das Debugpaket zurück.

 Bisher wurden keine Ereignisse generiert.

 Das Debugpaket versucht dann, den ausstehenden Haltepunkt an Code oder Daten zu binden, indem [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)aufgerufen wird, das von der DE implementiert wird.

 Wenn der Haltepunkt gebunden ist, sendet die DE eine [IDebugBreakpointBoundEvent2-Ereignisschnittstelle](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) an das Debugpaket. Das Debugpaket verwendet diese Schnittstelle, um alle Codekontexte (oder den einzelnen Datenkontext) aufzuzählen, die an den Haltepunkt gebunden sind, indem [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)aufgerufen wird, wodurch eine oder mehrere [IDebugBoundBreakpoint2-Schnittstellen](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) zurückgegeben werden. Die [GetBreakpointResolution-Schnittstelle](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) gibt eine [IDebugBreakpointResolution2-Schnittstelle](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) zurück, und [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) gibt eine [BP_RESOLUTION_INFO-Union](../../extensibility/debugger/reference/bp-resolution-info.md) zurück, die den Code oder Datenkontext enthält.

 Wenn de den Haltepunkt nicht binden kann, sendet es eine einzelne [IDebugBreakpointErrorEvent2-Ereignisschnittstelle](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) an das Debugpaket. Das Debugpaket ruft den Fehlertyp (Fehler oder Warnung) und die Informationsmeldung ab, indem [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)aufgerufen wird, gefolgt von [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) und [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Dadurch wird eine [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur zurückgegeben, die den Fehlertyp und die Meldung enthält.

 Wenn eine DE einen Haltepunkt verarbeitet, ihn aber nicht `BPET_TYPE_ERROR`binden kann, gibt es einen Fehler vom Typ zurück. Das Debugpaket antwortet, indem ein Fehlerdialogfeld angezeigt wird, und die IDE platziert eine Ausrufezeichen-Glyphe innerhalb der Haltepunkt-Glyphe links neben der Quellcodezeile.

 Wenn ein DE einen Haltepunkt verarbeitet, ihn nicht binden kann, aber ein anderer DE ihn binden kann, gibt es eine Warnung zurück. Die IDE antwortet, indem sie eine Frage-Glyphe innerhalb der Haltepunkt-Glyphe links von der Quellcodezeile platziert.

## <a name="see-also"></a>Weitere Informationen
- [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md)
