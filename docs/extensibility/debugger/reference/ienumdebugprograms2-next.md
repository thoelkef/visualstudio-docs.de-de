---
title: "IEnumDebugPrograms2::Next | Microsoft Docs"
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
  - "IEnumDebugPrograms2::Next"
helpviewer_keywords: 
  - "IEnumDebugPrograms2::Next"
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die nächste Gruppe von Elementen aus der Enumeration zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG            celt,  
   IDebugProgram2** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint             celt,  
   IDebugProgram2[] rgelt,  
   ref uint         pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der abzurufenden Elemente.  Gibt die maximale Größe des `rgelt` Arrays an.  
  
 `rgelt`  
 \[in, out\]  Array von Elementen, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ausgefüllt werden soll.  
  
 `pceltFetched`  
 \[out\]  Gibt die Anzahl der Elemente zurück, die sich tatsächlich in `rgelt`zurückgegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn kleiner als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)