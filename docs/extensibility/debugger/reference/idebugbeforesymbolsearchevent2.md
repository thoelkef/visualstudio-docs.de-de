---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBeforeSymbolSearchEvent2-Schnittstelle"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Das Debugmodul \(DE\) sendet diese Schnittstelle zum Debuggen von Manager der Sitzung \(SDM\), um die Auslastung Symbol während der für eine Statusleiste festzulegen.  
  
## Syntax  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, wenn es sich bei der für eine der Statusleiste Laden des Symbols festgelegt werden muss.  Diese Schnittstelle wird nur von Debugsymbolinformationen auf Module implementiert, die mit Skripts arbeiten oder ist Teil interpreter.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM die **QueryInterface** verwendet, um die **IDebugEvent2**\-Schnittstelle zuzugreifen\).  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, wenn es sich bei der für eine der Statusleiste Laden des Symbols festgelegt werden muss.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugBeforeSymbolSearchEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Ruft den Namen des Moduls ab, das gerade gedebuggt wird.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll