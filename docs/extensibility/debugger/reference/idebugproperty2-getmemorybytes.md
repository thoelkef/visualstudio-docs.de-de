---
title: "IDebugProperty2::GetMemoryBytes | Microsoft Docs"
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
  - "IDebugProperty2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugProperty2::GetMemoryBytes"
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Bytes an Arbeitsspeicher ab, die den Wert einer Eigenschaft zusammensetzt.  
  
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
 \[out\]  Gibt ein [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)\-Objekt zurück, das verwendet werden kann, um auf den Speicher abgerufen, der den Wert der Eigenschaft enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  Gibt `S_GETMEMORYBYTES_NO_MEMORY_BYTES` zurück, wenn keine abzurufenden Bytes Speicherplatz vorhanden ist.  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)