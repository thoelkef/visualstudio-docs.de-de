---
title: "IDebugExceptionEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "IDebugExceptionEvent2-Schnittstelle"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Das Debugmodul \(DE\) sendet diese Schnittstelle zum Debuggen von Manager der Sitzung \(SDM\), wenn das Programm in eine Ausnahme ausgelöst wird, das gerade ausgeführt wird.  
  
## Syntax  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um zu melden, dass eine Ausnahme aufgetreten ist im Programm, das gedebuggt wird.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, um eine Ausnahme zu melden.  Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion bereitgestellt, die vom SDM angegeben wurde, als sie angefügt haben dem Programm, das gedebuggt wurde.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugExceptionEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ruft ausführliche Informationen über die Ausnahme ab, die das Ereignis ausgelöst hat.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ruft eine lesbare Beschreibung für die ausgelöste Ausnahme ab, die das Ereignis ausgelöst hat.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Bestimmt, ob das Debugmodul \(DE\) die Übergabe dieser Ausnahme in das Programm, das gedebuggt wird unterstützt, wenn die Ausführung fortgesetzt wird.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Gibt an, ob die Ausnahme an das Programm übergeben werden soll, das gedebuggt wird, wenn die Ausführung fortsetzt bzw. wenn die Ausnahme verworfen wird.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Hinweise  
 Bevor das Ereignis, die DE\-Überprüfungen übertragen wird, um zu ermitteln, ob dies ein Ausnahmeereignis der ersten Chance und der zweiten Chance Ausnahme durch einen vorherigen Aufruf von [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)festgelegt wurde.  Wenn sie festgelegt wurde, dass eine Ausnahme der ersten Chance, wird das Ereignis an den `IDebugExceptionEvent2` SDM gesendet.  Wenn dies nicht der Fall ist, gibt DE der Anwendung eine Möglichkeit, die Ausnahme zu behandeln.  Wenn kein Ausnahmehandler bereitgestellt wird und wenn die Ausnahme als Ausnahme der zweiten Chance festgelegt wurde, wird das Ereignis an den `IDebugExceptionEvent2` SDM gesendet.  Andernfalls führt DE Programmausführung fortgesetzt, und das Betriebssystem oder die Common Language Runtime behandelt die Ausnahme.  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)