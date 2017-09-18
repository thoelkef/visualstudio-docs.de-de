---
title: "IDebugCoreServer2::GetPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetPort"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetPort"
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::GetPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen bestimmten Anschluss ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```c#  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### Parameter  
 `guidPort`  
 \[in\]  GUID des abzurufenden Anschlusses.  
  
 `ppPort`  
 \[out\]  Gibt ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Objekt zurück, das den gewünschten Anschlusses darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_PORTSUPPLIER_NO_PORT` zurück, wenn kein Anschluss mit dem angegebenen Bezeichner enthält.  
  
## Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)