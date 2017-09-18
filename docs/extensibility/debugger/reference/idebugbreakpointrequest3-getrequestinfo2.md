---
title: "IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft die Informationen ab, die anforderungs Haltepunkt dieser Haltepunkt Anforderungen beschrieben wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```c#  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### Parameter  
 `dwFields`  
 \[in\]  Eine Kombination von Flags aus der [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)\-Enumeration, die bestimmen, welche Felder aus `pBPRequestInfo` gefüllt werden sollen.  
  
 `bBPRequestInfo`  
 \[out\]  Die ausgefüllt werden [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Es gibt weitere Informationen in dieser Anforderung, als von der [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)\-Methode zurückgegeben wird.  
  
## Siehe auch  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)