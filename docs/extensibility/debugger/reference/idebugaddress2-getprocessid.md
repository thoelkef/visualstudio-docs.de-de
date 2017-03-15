---
title: "IDebugAddress2::GetProcessID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress2::GetProcessID"
helpviewer_keywords: 
  - "IDebugAddress2::GetProcessID-Methode"
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die ID des Prozesses ab, der das Objekt besitzt, die von dieser [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)\-Schnittstelle dargestellt wird.  
  
## Syntax  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```c#  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### Parameter  
 `pProcID`  
 \[out\]  Die Prozessnummer  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)