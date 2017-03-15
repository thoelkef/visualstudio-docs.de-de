---
title: "IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie"
helpviewer_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie"
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird aufgerufen, wenn die Verarbeitung einer abgefangenen Ausnahme abgeschlossen wurde.  
  
## Syntax  
  
```cpp#  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```c#  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### Parameter  
 `pqwCookie`  
 \[out\]  Eindeutiger Wert, der der Ausnahme, dass zugeordnet ist, abgefangen wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Nachdem die Behandlung einer abgefangene Ausnahme [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)\-Methode abgeschlossen hat, sendet er das [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)\-Ereignis.  Der Handler kann die `GetInterceptCookie`\-Methode verwenden, um den eindeutigen Wert abzurufen, der der Ausnahme zugeordnet wird \(der gleiche Wert der `InterceptCurrentException`Methode übergeben\).  
  
## Siehe auch  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)