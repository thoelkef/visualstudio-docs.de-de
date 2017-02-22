---
title: "IDebugStackFrame2::GetInfo | Microsoft Docs"
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
  - "IDebugStackFrame2::GetInfo"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetInfo"
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Beschreibung des Stapelrahmens ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetInfo (   
   FRAMEINFO_FLAGS dwFieldSpec,  
   UINT            nRadix,  
   FRAMEINFO*      pFrameInfo  
);  
```  
  
```c#  
int GetInfo (   
   enum_FRAMEINFO_FLAGS dwFieldSpec,  
   uint                 nRadix,  
   FRAMEINFO[]          pFrameInfo  
);  
```  
  
#### Parameter  
 `dwFieldSpec`  
 \[in\]  Eine Kombination von Flags aus der [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)\-Enumeration, die angibt, welche Felder des `pFrameInfo`\-Parameters gefüllt werden sollen.  
  
 `nRadix`  
 \[in\]  Die Basis verwendet werden soll, wenn alle numerischen Daten formatiert werden.  
  
 `pFrameInfo`  
 \[out\]  Eine [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur, die mit der Beschreibung des Stapelrahmens gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)