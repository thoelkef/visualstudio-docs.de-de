---
title: Eingabe des Pausenmodus | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738878"
---
# <a name="enter-break-mode"></a>Eingabe in den Pausenmodus
Die folgenden Informationen beschreiben den Prozess, der auftritt, wenn ein Haltepunkt auftritt, nachdem er in eine Funktion eingetreten ist, zu der Quellcodezeile ausgeführt wird, in der sich der Cursor befindet, oder wenn er zu einem Haltepunkt ausgeführt wird.

## <a name="break-mode-process"></a>Break-Modus-Prozess

1. Das Debugmodul (DE) sendet [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)oder ein anderes Stoppereignis, das dazu führt, dass die IDE in den Unterbrechungsmodus wechselt.

2. Das SDM ruft die Anruflisteninformationen wie folgt aus dem Thread ab:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) zum Abrufen der Quellcodeinformationen

    - [IDebugDocumentContext2::GetName,](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) um den Dateinamen abzubekommen

    - [IDebugDocumentContext2::GetStatementRange,](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) um den Anweisungsbereich abzubekommen

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) zum Abrufen von Speicherinformationen

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
