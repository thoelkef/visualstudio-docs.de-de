---
title: "IDebugSymbolProviderDirect::GetAppIDFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetAppIDFromAddress"
  - "GetAppIDFromAddress"
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetAppIDFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den bereitgestellten Bezeichner der Anwendungsdomäne Debug\- Adresse ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetAppIDFromAddress(  
   IDebugAddress* pAddress,  
   DWORD*         pAppID  
);  
```  
  
```c#  
int GetAppIDFromAddress(  
   IDebugAddress pAddress,  
   out uint      pAppID  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in\]  Debuggen Adresse, die von der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle dargestellt wird.  
  
 `pAppID`  
 \[out\]  Bezeichner der Anwendungsdomäne.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)