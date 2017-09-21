---
title: "IDebugPortEvents2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2::Event"
helpviewer_keywords: 
  - "IDebugPortEvents2::Event"
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode sendet Ereignisse, die die Erstellung und Zerstörung von Prozessen und von Programmen auf einen Anschluss angeben.  
  
## Syntax  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```c#  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### Parameter  
 `pMachine`  
 \[in\]  Ein [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)\-Objekt, das den Server darstellt \(Debug vorhanden, ist eins für jede Instanz von [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\), bei der das Ereignis aufgetreten ist.  
  
 `pPort`  
 \[in\]  Ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Objekt, das den Anschluss darstellt, in dem das Ereignis aufgetreten ist.  
  
 `pProcess`  
 \[in\]  Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Objekt, das den Prozess darstellt, in dem das Ereignis aufgetreten ist.  
  
 `pProgram`  
 \[in\]  Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das das Programm darstellt, in dem das Ereignis aufgetreten ist.  
  
 `pEvent`  
 \[in\]  Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Objekt, das das Ereignis angibt.  Die möglichen Ereignisse sind:  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 \[in\]  Die GUID des Ereignisses.  Da das Ereignis [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) umgewandelt wird, bevor diese Methode aufgerufen wird, wird dieser Bezeichner es einfacher, zu bestimmen, welches Ereignis ausgelöst wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)