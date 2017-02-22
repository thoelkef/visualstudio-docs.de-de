---
title: "IDebugEngine3::SetAllExceptions | Microsoft Docs"
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
  - "IDebugEngine3::SetAllExceptions"
helpviewer_keywords: 
  - "IDebugEngine3::SetAllExceptions"
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::SetAllExceptions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode legt den Zustand aller ausstehenden Ausnahmen fest.  
  
## Syntax  
  
```cpp  
HRESULT SetAllExceptions(  
   EXCEPTION_STATE dwState  
);  
```  
  
```c#  
int SetAllExceptions(  
   enum_EXCEPTION_STATE dwState  
);  
```  
  
#### Parameter  
 `dwState`  
 \[in\]  Einer der [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)\-Werte.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Siehe auch  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)