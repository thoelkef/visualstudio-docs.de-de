---
title: Haltepunktfehler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739216"
---
# <a name="breakpoint-errors"></a>Breakpoint-Fehler
Im Folgenden wird der Prozess beschrieben, wenn ein Haltepunkt versucht, eine Bindung an Code zu binden, aber fehlschlägt.

## <a name="troubleshoot-a-breakpoint-error"></a>Beheben eines Haltepunktfehlers

1. Das Debugmodul (DE) sendet einen [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) an den Session Debug Manager (SDM).

2. Das SDM ruft [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2** `ppErrorBP`) auf, um den Fehlerhaltepunkt abzubekommen.

3. Das SDM ruft [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) auf, um den ausstehenden Haltepunkt abzubekommen, von dem der Fehlerhaltepunkt stammt.

4. Das SDM ruft [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) auf, um den Grund zu ermitteln, warum der Fehlerhaltepunkt nicht gebunden werden konnte.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
