---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird programmbezogene Schnittstellen über Prozessgrenzen hinweg.  
  
## Syntax  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert, um Marshalling von Schnittstellen über Prozessgrenzen hinweg zu unterstützen.  
  
## Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/visual-cpp/atl/queryinterface) auf einer `IDebugProgramNode2`\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  Wenn diese Schnittstelle nicht abgerufen werden kann, unterstützt keine Marshalling von Schnittstellen. DE  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgende Weise:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg ab.|  
  
## Hinweise  
 Diese Schnittstelle wird implementiert, wenn in einem separaten Prozessbereich DE vom Programm, das gedebuggt wird: DE beispielsweise in Visual Studio\-Prozessraum anstelle des Prozessraums des Programms, das gedebuggt wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)