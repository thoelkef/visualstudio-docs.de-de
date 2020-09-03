---
title: Wechseln in den Umbruch Modus | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738878"
---
# <a name="enter-break-mode"></a>In den Umbruch Modus wechseln
Die folgenden Informationen beschreiben den Prozess, der auftritt, wenn nach dem Durchlaufen einer Funktion ein Haltepunkt erreicht wird, der in der Zeile des Quellcodes ausgeführt wird, in der sich der Cursor befindet, oder bis zu einem Breakpoint ausgeführt wird.

## <a name="break-mode-process"></a>Prozess für den Abbruch Modus

1. Die Debug-Engine (de) sendet [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)oder ein beliebiges anderes anhalteereignis, um zu bewirken, dass die IDE in den Umbruch Modus wechselt.

2. Der SDM Ruft die aufrufstackinformationen aus dem Thread wie folgt ab:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2:: getdocumentcontext zum Abrufen](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) der Quell Code Informationen

    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) , um den Dateinamen zu erhalten

    - [IDebugDocumentContext2:: getstatuementrange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) zum erhalten des Anweisungs Bereichs

    - [IDebugStackFrame2:: getcodecontext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) zum erhalten von Speicherinformationen

## <a name="see-also"></a>Siehe auch
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
