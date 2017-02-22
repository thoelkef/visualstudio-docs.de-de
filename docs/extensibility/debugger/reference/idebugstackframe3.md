---
title: "IDebugStackFrame3 | Microsoft Docs"
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
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "IDebugStackFrame3-Schnittstelle"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle erweitert, um [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) abgefangene Ausnahmen zu behandeln.  
  
## Syntax  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\-Schnittstelle implementiert, um abgefangene Ausnahmen zu unterstützen.  
  
## Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/visual-cpp/atl/queryinterface) auf einer `IDebugStackFrame2`\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden, die von [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)geerbt werden, macht die folgenden Methoden `IDebugStackFrame3` .  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Behandelt eine Ausnahme für den aktuellen Stapelrahmen vor jeder regulären Ausnahmebehandlung.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Gibt einen Code Elementkontext zurück, wenn eine Stapel Entladen von durchgeführt wurden.|  
  
## Hinweise  
 Eine abgefangene Ausnahme besagt, dass ein Debugger eine Ausnahme verarbeiten kann, bevor alle normalen Ausnahmebehandlung routinen von der Laufzeit aufgerufen werden.  Eine Ausnahme abzufangen im Prinzip besagt, dass die Laufzeit erfolgt, vortäuschen Sie, dass es sich um einen Ausnahmehandler vorhanden ist, auch wenn es nicht vorhanden ist.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) wird bei allen normalen Ausnahme von Rückruf aufgerufen \(die einzige Ausnahme liegt vor, wenn Sie \(verwaltetem und nicht verwaltetem Code im gemischten Modus Code\) debuggen. In diesem Fall wird die Ausnahme nicht während des Rückrufs der letzte Möglichkeit abgefangen werden kann\).  Wenn DE nicht implementiert, gibt `IDebugStackFrame3`oder DE einen Fehler aus IDebugStackFrame3: zurück:`InterceptCurrentException` \(z. B. `E_NOTIMPL`\), wird der Debugger behandelt die Ausnahme ordnungsgemäß.  
  
 Indem er eine Ausnahme abgefangen wird, kann der Debugger den Benutzern ermöglichen, Änderungen am Zustand des Programms ändern, die dann an der Stelle fortgesetzt und ausgeführt werden, in dem die Ausnahme ausgelöst wurde.  
  
> [!NOTE]
>  Abgefangene Ausnahmen werden nur in verwaltetem Code ermöglicht. h. in einem Programm, das unter der Common Language Runtime \(CLR\) ausgeführt wird.  
  
 Ein Debuggen Modul gibt an, dass sie Ausnahmen Unterbrechungen unterstützt, indem metricExceptions „at“ auf den Wert 1 festgelegt, indem die `SetMetric`\-Funktion verwendet.  Weitere Informationen finden Sie unter [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)