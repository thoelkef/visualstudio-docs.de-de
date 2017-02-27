---
title: "IDebugProgramHost2::GetHostId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2::GetHostId"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostId"
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramHost2::GetHostId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Prozess\-ID des Prozesses hostings dieses Programm ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```c#  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### Parameter  
 `pdwId`  
 \[in, out\]  Eine [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die den Prozess\-ID\-Informationen gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)