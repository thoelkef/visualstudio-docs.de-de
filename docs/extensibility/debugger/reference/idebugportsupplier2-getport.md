---
title: "IDebugPortSupplier2::GetPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::GetPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::GetPort"
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::GetPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen Port aus einem Anschlusslieferanten ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```c#  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### Parameter  
 `guidPort`  
 \[in\]  GUID \(Globally Unique Identifier\) des Anschlusses.  
  
 `ppPort`  
 \[out\]  Gibt ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Objekt zurück, das den Anschluss darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_PORTSUPPLIER_NO_PORT` zurück, wenn kein Anschluss mit dem angegebenen Bezeichner vorhanden ist.  
  
## Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)