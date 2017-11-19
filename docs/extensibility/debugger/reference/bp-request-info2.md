---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_REQUEST_INFO2
helpviewer_keywords: BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 904210dc1547c587c62a44a8e788b3f07179a71b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="bprequestinfo2"></a>BP_REQUEST_INFO2
Enthält Informationen zum Implementieren eines Haltepunkts, einschließlich Anbieter-GUID, Einschränkung und Ablaufverfolgungspunkt erforderlich sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _BP_REQUEST_INFO2 {  
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
} BP_REQUEST_INFO2;  
```  
  
```csharp  
public struct BP_REQUEST_INFO2 {  
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
  
## <a name="members"></a>Member  
 `dwFields`  
 Eine Kombination aus Flags aus der [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) -Enumeration, der angibt, welche Felder ausgefüllt sind.  
  
 `guidLanguage`  
 Die Sprach-GUID.  
  
 `bpLocation`  
 Die [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) -Struktur, die den Typ des der Position des Haltepunkts angibt.  
  
 `pProgram`  
 Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das die Anwendung darstellt, in dem sich der Breakpoint auftritt.  
  
 `bstrProgramName`  
 Der Name der Anwendung, in der sich der Breakpoint auftritt.  
  
 `pThread`  
 Die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem sich der Breakpoint auftritt.  
  
 `bstrThreadName`  
 Der Name des Threads, in dem sich der Breakpoint auftritt.  
  
 `bpCondition`  
 Die [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) -Struktur, die die Bedingungen beschrieben werden, unter dem der Haltepunkt ausgelöst wird.  
  
 `bpPassCount`  
 Die [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur, die die Anzahl übergeben von Informationen des Haltepunkts enthält.  
  
 `dwFlags`  
 Eine Kombination aus Flags aus der [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) -Enumeration, der die Flags für die angeforderte Breakpoint angibt.  
  
 `guidVendor`  
 Die GUID des Herstellers. Ein null-Wert kann sein.  
  
 `bstrConstraint`  
 Name der Einschränkung Haltepunkt. Ein null-Wert kann sein.  
  
 `bstrTracepoint`  
 Name der Trace-Punkt. Ein null-Wert kann sein.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, durch die [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)