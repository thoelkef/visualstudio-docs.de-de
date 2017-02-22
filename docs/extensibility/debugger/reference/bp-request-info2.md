---
title: "BP_REQUEST_INFO2 | Microsoft Docs"
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
  - "BP_REQUEST_INFO2"
helpviewer_keywords: 
  - "BP_REQUEST_INFO2-Struktur"
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält die Informationen, um einen Haltepunkt, einschließlich Anbieter GUID, Einschränkungen und Ablaufverfolgungspunkt zu implementieren müssen.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```c#  
public struct BP_REQUEST_INFO2 {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
};  
```  
  
## Mitglieder  
 `dwFields`  
 Eine Kombination von Flags aus der [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)\-Enumeration, die angibt, welche Felder geändert werden.  
  
 `guidLanguage`  
 Die Sprache GUID.  
  
 `bpLocation`  
 Die [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur, die den Typ der Haltepunktposition angibt.  
  
 `pProgram`  
 Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das die Anwendung angibt, in der der Haltepunkt auftritt.  
  
 `bstrProgramName`  
 Der Name der Anwendung, in der der Haltepunkt auftritt.  
  
 `pThread`  
 Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt, in dem der Haltepunkt auftritt.  
  
 `bstrThreadName`  
 Der Name des Threads, in dem der Haltepunkt auftritt.  
  
 `bpCondition`  
 Die [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur, die die Bedingungen beschrieben, unter denen der Haltepunkt ausgelöst wird.  
  
 `bpPassCount`  
 Die [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur, die die Anzahl der Übergeben von Informationen über des Haltepunkts enthält.  
  
 `dwFlags`  
 Eine Kombination von Flags aus der [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)\-Enumeration, die die Flags für den angeforderten Haltepunkt erreicht ist.  
  
 `guidVendor`  
 GUID des Anbieters.  Kann ein NULL\-Wert.  
  
 `bstrConstraint`  
 Name der Haltepunkt KEY\-Einschränkung.  Kann ein NULL\-Wert.  
  
 `bstrTracepoint`  
 Name des Punkts Ablaufverfolgungsebene.  Kann ein NULL\-Wert.  
  
## Hinweise  
 Diese Struktur wird von der [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)