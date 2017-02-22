---
title: "IDebugMemoryBytes2::WriteAt | Microsoft Docs"
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
  - "IDebugMemoryBytes2::WriteAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::WriteAt-Methode"
  - "WriteAt-Methode"
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Schreibt die angegebene Anzahl von Bytes des Arbeitsspeichers, wobei an der angegebenen Adresse.  
  
## Syntax  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```c#  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### Parameter  
 `pStartContext`  
 \[in\]  Das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekt, das angibt, wo die Bytes geschrieben werden soll.  
  
 `dwCount`  
 \[in\]  Die Anzahl der zu schreibenden Bytes.  
  
 `rgbMemory`  
 \[in\]  Die zu schreibende Byte.  Dieses Array wird angenommen, dass mindestens `dwCount` Bytes an Größe zu sein.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` , wenn nicht alle geschriebenen Bytes werden konnten oder einen Fehlercode zurück \(in der Regel `E_FAIL`\).  
  
## Hinweise  
 Wenn die Startadresse nicht innerhalb des Fensters Arbeitsspeicher ist, das durch dieses Objekt dargestellt wird [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) findet keine Schreibvorgänge auf, und ein Fehlercode von `E_FAIL` wird, selbst wenn die Menge zurückgegeben, um Überschneidungen in den Speicherbereich geschrieben werden soll.  
  
## Siehe auch  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)