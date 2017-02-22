---
title: "IEnumDebugCustomAttributes::Next | Microsoft Docs"
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
  - "IEnumCustomAttributes::Next"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Next"
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCustomAttributes::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von benutzerdefinierten Attributen in der Enumerationsfolge ab.  
  
## Syntax  
  
```cpp#  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der abzurufenden Elemente.  Gibt die maximale Größe des `rgelt` Arrays an.  
  
 `rgelt`  
 \[out\]  Ein Array von Objekten, [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) ausgefüllt werden soll.  
  
 `pceltFetched`  
 \[out\]  Gibt die Anzahl der Elemente zurück, die sich tatsächlich in `rgelt`zurückgegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn kleiner als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)