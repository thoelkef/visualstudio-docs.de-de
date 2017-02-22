---
title: "BP_ERROR_RESOLUTION_INFO | Microsoft Docs"
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
  - "BP_ERROR_RESOLUTION_INFO"
helpviewer_keywords: 
  - "BP_ERROR_RESOLUTION_INFO-Struktur"
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt die Behebung eines Fehlers von Haltepunkten, einschließlich Speicherort Programm und Threads.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```c#  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## Mitglieder  
 `dwFields`  
 Eine Kombination von Werten aus [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)\-Enumeration angeben, welche Felder der Struktur ergänzt werden.  
  
 `bpResLocation`  
 Die [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Union, die den Haltepunkt auflösungs für angibt.  
  
 `pProgram`  
 Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das die Anwendung angibt, in der der Haltepunkt Fehler aufgetreten ist.  
  
 `pThread`  
 Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt, in dem die Anwendung, die den Haltepunkt Fehler generiert hat, ausgeführt wird.  
  
 `bstrMessage`  
 Eine Zeichenfolge, die eine Warn\- oder Fehlermeldung, die sich aus dieser Fehler anschließend enthält.  
  
 `dwType`  
 Ein Wert aus der [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)\-Enumeration, die den Haltepunkt Fehlertyp angibt.  
  
## Hinweise  
 Diese Struktur wird von der [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)