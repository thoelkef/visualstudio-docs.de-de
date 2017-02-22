---
title: "IDebugThread2::Resume | Microsoft Docs"
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
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Ausführung eines Threads fort.  
  
## Syntax  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### Parameter  
 `pdwSuspendCount`  
 \[out\]  Gibt den Unterbrechungszähler nach dem Wiederaufnahmevorgang zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jeder Aufruf dieser Methode dekrementiert den Unterbrechungszähler, bis er 0 \(null\) erreicht, wenn tatsächlich, wird die Ausführung fortgesetzt.  Der Unterbrechungszähler wird im **Threads** Debuggen die Option Fenster angezeigt.  
  
 Für jeden Aufruf dieser Methode muss es einen früheren Aufruf der Methode [Suspend \(Anhalten\)](../../../extensibility/debugger/reference/idebugthread2-suspend.md) erteilen.  Der Unterbrechungszähler bestimmt, wieoft die bisher `IDebugThread2::Suspend`\-Methode aufgerufen wurde.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend \(Anhalten\)](../../../extensibility/debugger/reference/idebugthread2-suspend.md)