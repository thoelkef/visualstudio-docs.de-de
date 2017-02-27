---
title: "IDebugProcess3::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Veranlasst den Prozess der Anweisung oder die Anweisung einer des Schritts.  
  
> [!NOTE]
>  Diese Methode sollte statt [Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md)verwendet werden.  
  
## Syntax  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### Parameter  
 `pThread`  
 \[in\]  Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt wird hergestellt.  
  
 `sk`  
 \[in\]  Einer der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)\-Werte.  
  
 `step`  
 \[in\]  Einer der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)\-Werte.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Falls alle Threadsynchronisierung Kommunikation zwischen Threads oder sollten sich andere Threads im Prozess ausgeführt werden, wenn ein bestimmter Thread erfolgt.  
  
 **Warnung** senden aufhörendes ein Ereignis oder ein unmittelbares \(synchrone\) Ereignis nicht beim Behandeln dieses Aufrufs zu [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Andernfalls hängt vom Debugger kann.  
  
## Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)