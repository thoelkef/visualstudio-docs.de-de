---
title: BP_REQUEST_INFO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41a134c70c94c6c7fa826cf952c2444b7128fbb6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513122"
---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [BP_REQUEST_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-request-info).  
  
Enthält die Informationen erforderlich, um einen Haltepunkt zu implementieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
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
} BP_REQUEST_INFO;  
```  
  
```csharp  
public struct BP_REQUEST_INFO {  
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
  
## <a name="members"></a>Member  
 `dwFields`  
 Eine Kombination von Flags aus der [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Enumeration, der angibt, welche Felder ausgefüllt sind.  
  
 `guidLanguage`  
 Die Sprachen-GUID.  
  
 `bpLocation`  
 Die [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) -Struktur, die den Typ der Haltepunktposition angibt.  
  
 `pProgram`  
 Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das die Anwendung darstellt, in dem sich der Breakpoint auftritt.  
  
 `bstrProgramName`  
 Der Name der Anwendung in der der Breakpoint auftritt.  
  
 `pThread`  
 Die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem sich der Breakpoint auftritt.  
  
 `bstrThreadName`  
 Der Name des Threads in der der Breakpoint auftritt.  
  
 `bpCondition`  
 Die [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) -Struktur, die beschreibt die Bedingungen, unter dem der Haltepunkt ausgelöst wird.  
  
 `bpPassCount`  
 Die [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) -Struktur, die die Pass-Count-Informationen des Haltepunkts enthält.  
  
 `dwFlags`  
 Eine Kombination von Flags aus der [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Enumeration, die die Flags für den angeforderten Haltepunkt angibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, durch die [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) Methode.  
  
 Um die Debug-Engine-Anbieter-GUID zu erhalten, die Haltepunkt-Einschränkung oder der Ablaufverfolgungspunkt, finden Sie unter den [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

