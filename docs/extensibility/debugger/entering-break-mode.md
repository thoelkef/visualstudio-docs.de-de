---
title: In den Unterbrechungsmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f9b41a111ecc6118c9bae0ff518d8421a9f2320
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231937"
---
# <a name="enter-break-mode"></a>Geben Sie im Unterbrechungsmodus
Die folgenden Informationen beschreiben den Prozess, der tritt auf, wenn ein Breakpoint erreicht wird, nach dem Einzelschritt in eine Funktion, in die Zeile des Quellcodes, die den Cursor enthält, oder führen zu einem Breakpoint.  
  
## <a name="break-mode-process"></a>Modus Prozess anhalten  
  
1.  Die Debug-Engine (DE) sendet [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), oder andere Stopping-Ereignis, das dazu führen, dass die IDE im Unterbrechungsmodus befinden.  
  
2.  Das SDM Ruft die Aufruflisteninformationen aus dem Thread, wie folgt ab:  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) um die Quellcodeinformationen zu erhalten.  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) zum Abrufen des Dateinamens  
  
    -   [Idebugdocumentcontext2::](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) können Sie die Anweisungsbereich abrufen  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) zum Abrufen von Informationen im Arbeitsspeicher  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)