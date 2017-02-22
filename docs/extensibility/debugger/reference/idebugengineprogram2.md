---
title: "IDebugEngineProgram2 | Microsoft Docs"
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
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "IDebugEngineProgram2-Schnittstelle"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt Multithreaded Debugunterstützung.  
  
## Syntax  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Debuggen Modul implementiert diese Schnittstelle, um simultanes Debuggen mehrerer Threads zu unterstützen.  Diese Schnittstelle wird für dasselbe Objekt implementiert, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle implementiert.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus einer `IDebugProgram2`\-Schnittstelle zu erhalten.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugEngineProgram2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet die für alle Threads in diesem Programm ausgeführt werden sollen.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Beobachtet zur Ausführung \(oder Beenden, der bei der Ausführung überwacht\), um für den angegebenen Thread zu fungieren.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Ermöglicht \(oder nicht zulässig sind\), Ausdrucksauswertung, die auf dem angegebenen Thread ausgeführt, selbst wenn das Programm beendet wird.|  
  
## Hinweise  
 Visual Studio ruft diese Schnittstelle als Reaktion auf ein Ereignis [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) und Überwachungen für die „Thread\-Schritt“ und „Überwachungen für Ausdrucksauswertung ein Thread“ Zustände des Programms festzulegen.  [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird aufgerufen, sobald das Programm beendet werden soll. Diese Methode gibt das Programm eine Möglichkeit, alle Threads zu beenden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)