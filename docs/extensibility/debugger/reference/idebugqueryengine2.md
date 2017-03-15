---
title: "IDebugQueryEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "IDebugQueryEngine2-Schnittstelle"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht die Sitzung, die Multithreaded Manager \(SDM\) eine Schnittstelle abrufen, die das Debugmodul \(DE\) darstellt.  
  
## Syntax  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle für die meisten Objekte \(z. B. [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)interfaces, DE [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\) implementieren, und der Zugriff auf die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)\-Schnittstelle DEs selbst zu ermöglichen.  
  
## Hinweise für Aufrufer  
 DE [QueryInterface](/visual-cpp/atl/queryinterface) ein typischer Aufruf interface zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugQueryEngine2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ruft eine benutzerdefinierte Debuginformationen Schnittstelle des Moduls \(DE\) ab.|  
  
## Hinweise  
 Diese Schnittstelle wird normalerweise im Objekt implementiert, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle implementiert, um Kausalität ORDERED zu unterstützen, das von Funktionen wird. das heißt wenn der Debugger aus einer Funktion heraus erfolgt, wird möglicherweise die folgende Funktion nicht zum Ausführen auf dem Stapel die vorherige Funktion jedoch eine Funktion in einem anderen Thread vollständig.  Für eine Definition der Kausalität „,“ finden Sie unter [Glossar für Visual Studio\-Debugger](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)