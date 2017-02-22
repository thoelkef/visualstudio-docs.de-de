---
title: "IDebugReference2::GetMemoryBytes | Microsoft Docs"
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
  - "IDebugReference2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugReference2::GetMemoryBytes"
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Arbeitsspeicher physisch Bytes ab, die den Wert eines Verweises enthalten.  Für zukünftige Verwendung reserviert.  
  
## Syntax  
  
```cpp#  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### Parameter  
 `ppMemoryBytes`  
 \[out\]  Gibt ein [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)\-Objekt zurück, das verwendet werden kann, um auf den Speicher abgerufen, der den Wert des Verweises enthält.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)