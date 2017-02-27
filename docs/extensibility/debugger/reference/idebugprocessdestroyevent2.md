---
title: "IDebugProcessDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProcessDestroyEvent2"
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProcessDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird, wenn ein Prozess beendet wird, endet atypisch ist oder nicht mit gesendet.  
  
## Syntax  
  
```  
IDebugProcessDestroyEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) oder das benutzerdefinierte Anschlusslieferanten diese Schnittstelle implementieren, um zu melden, dass ein Prozess beendet wurde.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE oder einer benutzerdefinierten Port lieferant erstellt und sendet das Ereignisobjekt, um die Beendigung eines Prozesses.  DE sendet dieses Ereignis, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wird, wenn sie dem Programm verknüpft ist, das gedebuggt wird.  Der benutzerdefinierte Port lieferant sendet dieses Ereignis unter Verwendung der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)\-Schnittstelle.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)