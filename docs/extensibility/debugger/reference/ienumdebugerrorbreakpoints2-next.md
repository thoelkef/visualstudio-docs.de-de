---
title: "IEnumDebugErrorBreakpoints2::Next | Microsoft Docs"
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
  - "IEnumDebugErrorBreakpoints2::Next"
helpviewer_keywords: 
  - "IEnumDebugErrorBreakpoints2::Next"
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugErrorBreakpoints2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die nächste Gruppe von Elementen aus der Enumeration zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG                    celt,  
   IDebugErrorBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                     celt,  
   IDebugErrorBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der abzurufenden Elemente.  Gibt die maximale Größe des `rgelt` Arrays an.  
  
 `rgelt`  
 \[in, out\]  Array von Elementen, [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) ausgefüllt werden soll.  
  
 `pceltFetched`  
 \[out\]  Gibt die Anzahl der Elemente zurück, die sich tatsächlich in `rgelt`zurückgegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn kleiner als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)