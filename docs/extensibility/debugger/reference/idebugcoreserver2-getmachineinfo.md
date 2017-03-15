---
title: "IDebugCoreServer2::GetMachineInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetInfo"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetInfo"
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::GetMachineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Beschreibung des Computers ab, auf dem der zentralen Server ausgeführt wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetInfo(   
   MACHINE_INFO_FIELDS Fields,  
   MACHINE_INFO*       pMachineInfo  
);  
```  
  
```c#  
int GetInfo(   
   enum_ MACHINE_INFO_FIELDS  Fields,  
   MACHINE_INFO[]             pMachineInfo  
);  
```  
  
#### Parameter  
 `Fields`  
 \[in\]  Eine Kombination von Flags aus der [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)\-Enumeration, die angeben, welche Felder aus `pMachineInfo` ergänzt werden sollen.  
  
 `pMachineInfo`  
 \[in, out\]  Eine [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) Struktur, die mit einer Beschreibung des Computers aufgefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)