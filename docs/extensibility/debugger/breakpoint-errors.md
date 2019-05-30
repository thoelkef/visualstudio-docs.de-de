---
title: Haltepunktfehler | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31eabde4ae19ae7342188a5d2a16374b9c94afc0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332559"
---
# <a name="breakpoint-errors"></a>Haltepunktfehler
Die folgenden beschreibt den Prozess aus, wenn ein Haltepunkt zum Binden an Code versucht jedoch ein Fehler auftritt.

## <a name="troubleshoot-a-breakpoint-error"></a>Problembehandlung bei der ein haltepunktfehler

1. Die Debug-Engine (DE) sendet ein [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) für die Sitzung Debug-Manager (SDM).

2. Die SDM-Aufrufe [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) um den Haltepunkt Fehler zu erhalten.

3. Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) abzurufenden den ausstehenden Haltepunkt, von dem der Haltepunkt Fehler verursacht wurde.

4. Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) abzurufenden den Grund, warum der Haltepunkt Fehler beim Binden Fehler.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)