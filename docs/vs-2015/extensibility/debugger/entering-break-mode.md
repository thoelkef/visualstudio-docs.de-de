---
title: Wechseln in den Umbruch Modus | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182250"
---
# <a name="entering-break-mode"></a>Eintreten in den Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird der Prozess beschrieben, der auftritt, wenn ein Breakpoint nach dem Ausführen einer Funktion ausgeführt wird, die bis zur Zeile des Quellcodes ausgeführt wird, in der sich der Cursor befindet, oder bis zu einem Breakpoint ausgeführt wird.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
