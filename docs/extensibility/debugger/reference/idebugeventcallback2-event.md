---
title: "IDebugEventCallback2::Event | Microsoft Docs"
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
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sendet eine Benachrichtigung von Ereignissen Debuggen.  
  
## Syntax  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```c#  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### Parameter  
 `pEngine`  
 \[in\]  Ein [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)\-Objekt, das das Debugmodul \(DE\) darstellt, das dieses Ereignis sendet.  DE ist erforderlich, um diesen Parameter zu ergänzen.  
  
 `pProcess`  
 \[in\]  Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Objekt, das den Prozess darstellt, in dem das Ereignis aufgetreten ist.  Dieser Parameter wird vom Debugbuild Manager der Sitzung \(SDM\) eingetragen.  DE übergibt immer einen NULL\-Wert für diesen Parameter.  
  
 `pProgram`  
 \[in\]  Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das das Programm darstellt, in dem dieses Ereignis eintritt.  Für die meisten Ereignisse ist dieser Parameter kein NULL\-Wert.  
  
 `pThread`  
 \[in\]  Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt, in dem dieses Ereignis eintritt.  Für das Beenden von Ereignissen, kann dieser Parameter kein NULL\-Wert sein, wenn der Stapelrahmen für diesen Parameter abgerufen wird.  
  
 `pEvent`  
 \[in\]  Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Objekt, das das Debugereignis darstellt.  
  
 `riidEvent`  
 \[in\]  GUID, der identifiziert, das die Ereignisschnittstelle, die vom `pEvent`\-Parameter abgerufen werden sollen.  
  
 `dwAttrib`  
 \[in\]  Eine Kombination von Flags aus der [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)\-Enumeration.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn diese Methode aufgerufen wird `dwAttrib` der Parameter müssen übereinstimmen, wird der Wert zurückgegeben von der aufgerufenen Methode als [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) das Ereignisobjekt in den `pEvent`\-Parameter übergeben.  
  
 Alle von Ereignissen werden asynchron gesendet, unabhängig davon, ob ein Ereignis selbst oder nicht asynchron ist.  Wenn DE diese Methode aufruft, gibt der Rückgabewert nicht an, ob das Ereignis verarbeitet wurde, sondern nur, ob das Ereignis empfangen wurde.  Auch bei den meisten Fällen ist das Ereignis nicht verarbeitet worden, wenn diese Methode erfolgreich beendet wird.  
  
## Siehe auch  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)