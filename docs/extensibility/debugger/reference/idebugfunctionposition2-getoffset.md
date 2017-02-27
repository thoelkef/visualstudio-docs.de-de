---
title: "IDebugFunctionPosition2::GetOffset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2::GetOffset"
helpviewer_keywords: 
  - "IDebugFunctionPosition2::GetOffset"
ms.assetid: 60943782-aec7-4be2-b222-1984ed53a543
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugFunctionPosition2::GetOffset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Position der Funktion im Quelldokument ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetOffset(   
   TEXT_POSITION* pPosition  
);  
```  
  
```c#  
int GetOffset(  
   TEXT_POSITION[] pPosition  
);  
```  
  
#### Parameter  
 `pPosition`  
 \[in, out\]  Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die die Position der Funktion in einem Dokument gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)