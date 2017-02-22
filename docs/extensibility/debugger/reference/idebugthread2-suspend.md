---
title: "IDebugThread2::Suspend | Microsoft Docs"
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
  - "IDebugThread2::Suspend"
helpviewer_keywords: 
  - "IDebugThread2::Suspend"
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::Suspend
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Hält einen Thread an.  
  
## Syntax  
  
```cpp#  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### Parameter  
 `pdwSuspendCount`  
 \[out\]  Gibt den Unterbrechungszähler nach dem Unterbrechen Vorgang zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jeder Aufruf dieser Methode erhöht den Unterbrechungszähler über 0.  Der Unterbrechungszähler wird im **Threads** Debuggen die Option Fenster angezeigt.  
  
 Für jeden Aufruf dieser Methode muss es sich um einen späteren Aufruf der [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)\-Methode geben.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)