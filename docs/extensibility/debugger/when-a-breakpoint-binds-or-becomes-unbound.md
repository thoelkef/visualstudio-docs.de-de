---
title: Wenn ein Haltepunkt bindet oder ungebunden wird | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3253841778fe5a07e00b644423495b8ceee1a335
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712335"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Wenn ein Haltepunkt bindet oder ungebunden wird
Wenn ein Haltepunkt zum Zeitpunkt eines Aufrufs an die [IDebugPendingBreakpoint2::CanBind-Methode](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) nicht gebunden werden kann, unterscheiden sich die Bindungszeit und die Erstellungszeit des Haltepunkts.

## <a name="methods-called"></a>Methoden, die als
 Der Sitzungsdebug-Manager (SDM) ruft die folgenden Methoden auf:

1. [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Die DE gibt einen [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)zurück.

2. [IDebugPendingBreakpoint2::Aktivieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2::Virtualisieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. Die [IDebugPendingBreakpoint2::Bind-Methode](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) und gibt S_OK zurück. Die DE sendet ein [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) oder [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) und [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints-Methoden](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) zum Überprüfen und Abrufen der gebundenen Haltepunkte.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
