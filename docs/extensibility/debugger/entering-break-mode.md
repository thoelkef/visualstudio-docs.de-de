---
title: "In den Unterbrechungsmodus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Unterbrechungsmodus"
  - "Debuggen [Debugging-SDK], in den Unterbrechungsmodus"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# In den Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden beschreibt den Prozess, der auftritt, wenn ein Haltepunkt erreicht wird, nachdem er auf eine Funktion aufgetreten ist, Zeile des Quellcodes ausgeführt wird, der den Cursor enthält oder einem Haltepunkt ausgeführt wird.  
  
## Unterbrechungsmodus\-Prozess  
  
1.  Das Debugmodul \(DE\) sendet [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)oder ein anderes aufhörende Ereignis, um die IDE dass in den Unterbrechungsmodus wechselt.  
  
2.  Das SDM Aufruflisteninformationen werden von der vom Thread ab, wie folgt:  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Danach](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) Quellcode, um die Informationen abzurufen  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) zum Abrufen des Dateinamens  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) , um den Anweisungstext Bereichs abrufen  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) zum Abrufen von Informationen über den Arbeitsspeicher  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)