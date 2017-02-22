---
title: "IDebugPort2::GetProcess | Microsoft Docs"
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
  - "IDebugPort2::GetPortSupplier"
helpviewer_keywords: 
  - "IDebugPort2::GetPortSupplier"
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den angegebenen Prozess, der auf einen Anschluss ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetProcess(   
   AD_PROCESS_ID    ProcessId,  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(   
   AD_PROCESS_ID      ProcessId,  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### Parameter  
 `ProcessId`  
 \[in\]  Eine [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die die Prozess\-ID angibt.  
  
 `ppProcess`  
 \[out\]  Gibt ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Objekt zurück, das den Prozess darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)