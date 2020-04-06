---
title: Schlagen eines Haltepunkts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738570"
---
# <a name="hit-a-breakpoint"></a>Treffen eines Haltepunkts
Im folgenden Abschnitt wird der Prozess beschrieben, wenn das Debugmodul (DE) beim Ausführen oder Schrittweisen einen Haltepunkt erreicht:

## <a name="troubleshoot-a-hit-breakpoint"></a>Fehlerbehebung bei einem Trefferpunkt

1. Die DE sendet eine [IDebugBreakpointEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugbreakpointevent2.md) als **EVENT_SYNC_STOP**.

2. Der Sitzungsdebug-Manager (SDM) ruft [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) auf, um den punkteinen Punkt abzubekommen, der getroffen wurde.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
