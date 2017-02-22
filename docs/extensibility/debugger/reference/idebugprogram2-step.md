---
title: "IDebugProgram2::Step | Microsoft Docs"
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
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Führt einen Schritt aus.  
  
> [!NOTE]
>  Diese Methode ist veraltet.  Verwenden Sie stattdessen die [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)\-Methode.  
  
## Syntax  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### Parameter  
 `pThread`  
 \[in\]  Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt, der aufgetreten ist.  
  
 `sk`  
 \[in\]  Ein Wert aus der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)\-Enumeration, der den Typ des Schrittes angibt.  
  
 `step`  
 \[in\]  Ein Wert aus der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)\-Enumeration, der die Einheit des Schritts angegeben wird \(beispielsweise durch Anweisung oder \- Anweisung\).  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Falls alle Threadsynchronisierung Kommunikation zwischen Threads oder sollten sich andere Threads im Programm ausgeführt werden, wenn ein bestimmter Thread erfolgt.  
  
> [!WARNING]
>  Senden Sie ein aufhörendes Ereignis oder ein unmittelbares \(synchrone\) Ereignis nicht beim Behandeln dieses Aufrufs zu [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Andernfalls hängt vom Debugger kann.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)