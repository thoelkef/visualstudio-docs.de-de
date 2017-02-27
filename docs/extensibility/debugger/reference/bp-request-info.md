---
title: "BP_REQUEST_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_REQUEST_INFO"
helpviewer_keywords: 
  - "BP_REQUEST_INFO-Struktur"
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält die Informationen, um einen Haltepunkt zu implementieren müssen.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
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
} BP_REQUEST_INFO;  
```  
  
```c#  
public struct BP_REQUEST_INFO {  
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
  
## Hinweise  
 Diese Struktur wird von der [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)\-Methode zurückgegeben.  
  
 Wenn Sie erhalten muss der Debugmodul GUID, die Haltepunkt oder Ablaufverfolgungspunkt Einschränkung finden Sie in den [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)