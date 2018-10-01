---
title: In den Unterbrechungsmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25adcc12e6d474899165c1a486fd550f34dd99a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512702"
---
# <a name="entering-break-mode"></a>Eintreten in den Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [eingeben im Unterbrechungsmodus](https://docs.microsoft.com/visualstudio/extensibility/debugger/entering-break-mode).  
  
Im folgenden wird beschrieben, den Prozess, der tritt auf, wenn ein Breakpoint erreicht wird, nach dem Einzelschritt in eine Funktion, in die Zeile des Quellcodes, die den Cursor enthält, oder führen zu einem Breakpoint.  
  
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
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)

