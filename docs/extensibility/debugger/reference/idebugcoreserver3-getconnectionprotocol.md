---
title: "IDebugCoreServer3::GetConnectionProtocol | Microsoft Docs"
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
  - "IDebugCoreServer3::GetConnectionProtocol"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetConnectionProtocol"
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::GetConnectionProtocol
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt einen Wert zurück, der das Protokoll angibt, das verwendet wird, um zwischen dem Server und dem Debuggen von Paket zu kommunizieren.  
  
## Syntax  
  
```cpp#  
HRESULT GetConnectionProtocol(  
   CONNECTION_PROTOCOL* pProtocol  
);  
```  
  
```c#  
int GetConnectionProtocol(  
   CONNECTION_PROTOCOL[] pProtocol  
);  
```  
  
#### Parameter  
 `pProtocol`  
 \[out\]  Gibt einen Wert aus der [CONNECTION\_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)\-Enumeration zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [CONNECTION\_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)