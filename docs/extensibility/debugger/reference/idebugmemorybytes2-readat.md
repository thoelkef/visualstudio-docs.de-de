---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
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
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::ReadAt-Methode"
  - "ReadAt-Methode"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Liest eine Folge von Bytes, beginnend an einem bestimmten Speicherort.  
  
## Syntax  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### Parameter  
 `pStartContext`  
 \[in\]  Das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekt, das angibt, wo die Bytes gelesen werden soll.  
  
 `dwCount`  
 \[in\]  Die Anzahl der zu lesenden Bytes.  Gibt die Länge des `rgbMemory` Arrays an.  
  
 `rgbMemory`  
 \[in, out\]  Das Array, dem die gelesenen Bytes genau genommen gefüllt wurde.  
  
 `pdwRead`  
 \[out\]  Gibt die Anzahl von zusammenhängenden Bytes gelesen, die tatsächlich zurückgegeben werden.  
  
 `pdwUnreadable`  
 \[in, out\]  Gibt die Anzahl von nicht lesbar Bytes zurück.  Kann ein NULL\-Wert, wenn der Client die Anzahl der Bytes uninteressiert nicht lesbar ist.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn 100 Bytes angefordert werden, und die ersten 50 lesbar sind, sind die nächsten 20 nicht lesbar, und die übrigen 30 sind diese Methode beendet lesbar:  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 In diesem Fall da `*pdwRead + *pdwUnreadable < dwCount`, der Aufrufer einen zusätzlichen Aufruf lesen können, müssen die verbleibenden 30 Bytes der ursprünglichen 100, die angefordert werden, und das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekt, das in den `pStartContext`\-Parameter übergebene durch 70 \(null\) gesetzt werden.  
  
## Siehe auch  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)