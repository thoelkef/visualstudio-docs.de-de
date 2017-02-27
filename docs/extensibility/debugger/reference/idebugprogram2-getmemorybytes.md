---
title: "IDebugProgram2::GetMemoryBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Bytes an Arbeitsspeicher ab, die vom Programm belegt sind.  
  
## Syntax  
  
```cpp#  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### Parameter  
 `ppMemoryBytes`  
 \[out\]  Gibt ein Objekt zurück, das die [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) Bytes Speicherplatz des Programms darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Bytes des Arbeitsspeichers, wie durch das Objekt dargestellt wird [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) für das Bild des Programms im Arbeitsspeicher und nicht in einem Speicher, die belegt wurde, während das Programm ausgeführt wurde.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)