---
title: "IDebugDefaultPort2::GetServer | Microsoft Docs"
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
  - "IDebugDefaultPort2::GetServer"
helpviewer_keywords: 
  - "IDebugDefaultPort2::GetServer"
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDefaultPort2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft eine Schnittstelle zum Server, die diesen Port aktiviert ist.  
  
## Syntax  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```c#  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### Parameter  
 `ppServer`  
 \[out\]  Gibt ein Objekt zurück, das die [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)\-Schnittstelle implementiert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) wird von Visual Studio implementiert und den Server darstellt, dass der Port an befindet.  
  
## Siehe auch  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)