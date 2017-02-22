---
title: "IDebugThread2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2"
helpviewer_keywords: 
  - "IDebugThread2-Schnittstelle"
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Thread, der in einem Programm dar.  
  
## Syntax  
  
```  
IDebugThread2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um einen Ausführungsthread in einem einzelnen Programm darzustellen.  
  
## Hinweise für Aufrufer  
 Rufen Sie [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) an, die zum Abrufen dieser Schnittstelle, die den derzeit aktive Thread darstellt.  
  
 Diese Schnittstelle wird auch verwendet, wenn eine Anforderung Haltepunkt erstellt werden \(siehe [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)\).  
  
 Diese Schnittstelle wird auch zurückgegeben, wenn ein Grenzen\- oder Fehler behoben breakpoint \(siehe [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) und [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)\).  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugThread2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Ruft eine Liste der Stapelrahmen für diesen Thread ab.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ruft den Namen des Threads ab.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Legt den Namen des Threads fest.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ruft das Programm ab, in dem ein Thread ausgeführt wird.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Bestimmt, ob die folgende Anweisung in den angegebenen Stapelrahmen und den Code Elementkontext festgelegt werden kann.|  
|[Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Legt die folgende Anweisung in den angegebenen Stapelrahmen und den Code Elementkontext festgelegt.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ruft den Bezeichner für den Thread des Systems ab.|  
|[Suspend \(Anhalten\)](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Hält einen Thread an.|  
|[Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Setzt einen Thread fortgesetzt.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ruft Eigenschaften ab, die einem Thread beschreiben.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ruft den logischen Thread ab, die dieser physischen Thread zugeordnet ist.|  
  
## Hinweise  
 Da ein einzelner physischer Threads in mehreren Programmen ausgeführt werden kann, kann mehr als ein `IDebugThread2` von mehr als einem Programm den gleichen physischen Thread darstellt.  
  
 Wenn ein Haltepunkt oder eine Ausnahme auftritt, wird ein Ereignis gesendet, indem [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)aufruft.  Eines der Argumente an diese Methode ist eine `IDebugThread2`\-Schnittstelle, die den aktuellen Thread darstellt.  [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) dient zum Abrufen der [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\-Schnittstelle für den aktuellen Stapelrahmen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)