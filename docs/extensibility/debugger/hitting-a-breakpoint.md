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
ms.openlocfilehash: 1286af8222703028d5a8a1bd2dbb0d990ca7e30c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889904"
---
# <a name="hit-a-breakpoint"></a>Treffen eines Haltepunkts
Der folgende Abschnitt beschreibt den Prozess aus, wenn die Debug-Engine (DE) einen Haltepunkt erreicht, bei der Ausführung oder das schrittweise ausführen:

## <a name="troubleshoot-a-hit-breakpoint"></a>Problembehandlung bei einem Treffer Haltepunkt

1. Der DE sendet eine [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) Schnittstelle als eine **EVENT_SYNC_STOP**.

2. Ruft die Sitzungs-Debug-Manager (SDM) [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) um den Haltepunkt zu erhalten, das ermittelt wurde.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)