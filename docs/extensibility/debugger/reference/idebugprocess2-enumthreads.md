---
title: "IDebugProcess2::EnumThreads | Microsoft Docs"
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
  - "IDebugProcess2::EnumThreads"
helpviewer_keywords: 
  - "IDebugProcess2::EnumThreads"
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste aller Threads ab, die im Prozess ausgeführt werden.  
  
## Syntax  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```c#  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)\-Objekt zurück, das eine Liste aller Threads in allen Programmen im Prozess enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode listet die Threads auf, die in jedem Programm aus und kombiniert sie dann in eine Ansicht der Threads verarbeitet werden.  Ein Thread kann in mehrere Programme ausgeführt. diese Methode listet diesen Thread nur einmal auf.  
  
 Diese Methode wird eine Liste der Threads des Prozesses ohne Duplikate vor.  Andernfalls um die Threads auflisten, die in ein bestimmtes Programm aus, verwenden Sie die [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)\-Methode.  
  
## Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)