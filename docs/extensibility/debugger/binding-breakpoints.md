---
title: Bindung von Haltepunkten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efda5969e7022f8c44d7060a29ee31fbc5968d96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="binding-breakpoints"></a>Bindung von Haltepunkten
Wenn der Benutzer einen Breakpoint festzulegen, z. B. durch Drücken F9, die IDE formuliert die Anforderung und fordert die Debugsitzung, um den Haltepunkt zu erstellen.  
  
## <a name="setting-a-breakpoint"></a>Festlegen eines Haltepunkts  
 Festlegen eines Haltepunkts ist ein zweistufiger Prozess, da der Code- oder Datenmenge, die den Breakpoint betroffen noch möglicherweise nicht verfügbar. Zuerst muss der Haltepunkt beschrieben werden, und klicken Sie dann wie Code- oder Datenmenge verfügbar ist, es muss gebunden werden zu diesem Code oder Daten, wie folgt:  
  
1.  Der Haltepunkt wird aus der entsprechenden Debugmodule (DEs) angefordert, und dann wird der Haltepunkt an den Code oder Daten gebunden, sobald sie verfügbar.  
  
2.  Der Breakpoint-Anforderung wird an die Debugsitzung gesendet, die an alle relevanten DEs gesendet. Alle DE ab, die auswählt, behandeln den Haltepunkt erstellt ein entsprechendes ausstehender Haltepunkt.  
  
3.  Die Debugsitzung ausstehenden Haltepunkte sammelt und sendet sie zurück an das debugpaket (die Komponente Debuggen von Visual Studio).  
  
4.  Das debugpaket fordert die Debugsitzung, um die ausstehenden Haltepunkts an Code- oder Datenmenge zu binden. Die Debugsitzung sendet diese Anforderung an alle relevanten DEs.  
  
5.  Wenn die DE den Haltepunkt gebunden werden kann, sendet er, ein Haltepunkt an der Debugsitzung Ereignis gebunden. Wenn dies nicht der Fall ist, sendet er stattdessen ein Haltepunkt Error-Ereignis.  
  
## <a name="pending-breakpoints"></a>Ausstehenden Haltepunkte  
 Ein ausstehender Haltepunkt kann an mehrere Codepositionen binden. Beispielsweise kann eine Zeile des Quellcodes für eine C++-Vorlage an jeder Codesequenz, die die Vorlage generiert binden. Eine gebundene Haltepunktereignis können die Debugsitzung aufzählen Kontexte Code zu einem Breakpoint gebunden werden, zu dem Zeitpunkt, der das Ereignis gesendet wurde. Weiterer Code Kontexte können später gebunden werden, damit die DE senden kann, dass mehrere Haltepunkt für jede bindungsanforderung Ereignisse gebunden. Ein DE sollten jedoch nur ein Haltepunkt Error-Ereignis pro Anforderung zur Bindung senden.  
  
## <a name="implementation"></a>Implementierung  
 Programmgesteuert, das debugpaket der Sitzung Debug-Manager (SDM) aufgerufen, und übergibt ein [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Schnittstelle, die dient als Wrapper für eine [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) -Struktur, die beschreibt, die der Haltepunkt festgelegt werden. Obwohl viele Formen annehmen, Haltepunkte letztlich in einem Kontext Code- oder Datenmenge aufgelöst sein können.  
  
 Die SDM übergibt diesen Aufruf auf jeden relevanten DE durch Aufrufen seiner [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Methode. Wenn DE entscheidet, behandeln den Haltepunkt, erstellt und gibt eine [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstelle. Die SDM erfasst diese Schnittstellen und übergibt sie an das debugpaket als ein einzelnes `IDebugPendingBreakpoint2` Schnittstelle.  
  
 Bisher wurden keine Ereignisse generiert.  
  
 Das debugpaket versucht anschließend, binden die ausstehenden Haltepunkts an Code- oder Datenmenge durch Aufrufen [binden](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), die durch die DE implementiert wird.  
  
 Wenn der Haltepunkt gebunden ist, sendet der DE ein [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) Ereignisschnittstelle um das debugpaket. Der Debug-Paket verwendet, die diese Schnittstelle zum Aufzählen von allen Code-Kontexten (oder die einzelnen Datenkontext) bis zum Haltepunkt gebunden sein, durch den Aufruf [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), womit eine oder mehrere [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Schnittstellen. Die [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) -Schnittstelle gibt eine [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) -Schnittstelle, und [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) gibt eine [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Union, die den Kontext Code- oder Datenmenge enthält.  
  
 Wenn DE der Breakpoint kann nicht gebunden ist, sendet er eine einzelne [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) Ereignisschnittstelle um das debugpaket. Das debugpaket Ruft den Fehlertyp (Fehler oder Warnung) und eine informative Meldung, die durch den Aufruf [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), gefolgt von [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) und [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Dies gibt eine [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) -Struktur, die den Fehlertyp und die Meldung enthält.  
  
 Wenn ein DE einen Haltepunkt behandelt, aber es nicht werden gebunden kann, gibt es einen Fehler vom Typ `BPET_TYPE_ERROR`. Das debugpaket reagiert, indem ein Fehlerdialogfeld angezeigt, und die IDE fügt eine Ausrufezeichen Glyphe in das breakpointsymbol links von der Quellcodezeile.  
  
 Wenn eine bereitgestellten Kompatibilitätsrichtlinie behandelt einen Haltepunkt, kann nicht gebunden werden, aber eine andere DE binden kann, wird eine Warnung zurückgegeben. Die IDE reagiert, indem ein Symbol Frage in das breakpointsymbol links von der Quellcodezeile zu platzieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)