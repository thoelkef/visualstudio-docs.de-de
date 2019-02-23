---
title: Erreichen eines Haltepunkts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29e0fb7a5fe9cfa107bdbc4ced90cbea2967b77a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707314"
---
# <a name="hit-a-breakpoint"></a>Treffen eines Haltepunkts
Der folgende Abschnitt beschreibt den Prozess aus, wenn die Debug-Engine (DE) einen Haltepunkt erreicht, bei der Ausführung oder das schrittweise ausführen:

## <a name="troubleshoot-a-hit-breakpoint"></a>Problembehandlung bei einem Treffer Haltepunkt

1.  Der DE sendet eine [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) Schnittstelle als eine **EVENT_SYNC_STOP**.

2.  Ruft die Sitzungs-Debug-Manager (SDM) [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) um den Haltepunkt zu erhalten, das ermittelt wurde.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)