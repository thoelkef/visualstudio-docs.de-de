---
title: "IDebugThread2::EnumFrameInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::EnumFrameInfo"
helpviewer_keywords: 
  - "IDebugThread2::EnumFrameInfo"
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste der Stapelrahmen für diesen Thread ab.  
  
## Syntax  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```c#  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### Parameter  
 `dwFieldSpec`  
 \[in\]  Eine Kombination von Flags aus der [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)\-Enumeration, die angibt, welche Felder der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen ergänzt werden sollen.  Geben Sie das `FIF_FUNCNAME_FORMAT`\-Flag auf, um den Funktionsnamen zu einer einzigen Zeichenfolge zu formatieren.  
  
 `nRadix`  
 \[in\]  Basis verwendet, wenn numerische Informationen im Enumerator formatiert werden.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)\-Objekt zurück, das eine Liste von [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen enthält, die den Stapelrahmen beschreiben.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Rahmen des Threads werden in der Reihenfolge aufgelistet, wenn für den aktuellen Frame, die zuerst aufgelistet werden, und die ältesten Rahmen zuletzt aufgelistet sind.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)