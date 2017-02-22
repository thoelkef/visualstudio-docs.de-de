---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

VERALTET.  NOT TUN USE.  
  
## Syntax  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### Parameter  
 `pMDMProgram`  
 \[in\]  Die Schnittstelle [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Programm anzufügenden darstellt.  
  
 `pCallback`  
 \[in\]  Die zum Debuggen von Ereignissen verwendet werden soll [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Schnittstelle zum SDM zu senden.  
  
 `dwReason`  
 \[in\]  Ein Wert aus der [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)\-Enumeration, der den Grund für das Anfügen angibt.  
  
## Rückgabewert  
 Eine Implementierung sollte immer `E_NOTIMPL`zurückgeben.  
  
## Hinweise  
  
> [!WARNING]
>  Ab [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]wird diese Methode nicht mehr verwendet und sollte immer `E_NOTIMPL`zurückgeben.  Weitere Informationen finden Sie, dass die [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)\-Schnittstelle für einen alternativen Ansatz, wenn der Knoten Programm angeben, muss es nicht angefügt werden kann, oder wenn der Knoten Programm einfach das Programm `GUID`festlegt. Andernfalls implementieren Sie die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode.  
  
## Vor Visual Studio 2005  
 Diese Methode muss implementiert werden, nur dann, wenn DE im Adressbereich des Programms, das gedebuggt wird.  Andernfalls gibt diese Methode `S_FALSE`zurückgeben.  
  
 Wenn diese Methode aufgerufen wird, muss das DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)\-Ereignisobjekt, wenn es nicht bereits für diese Instanz der [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)\-Schnittstelle übermittelt wurde, sowie die [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) und [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)\-Ereignisobjekte senden.  Das [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)\-Ereignisobjekt wird dann gesendet, wenn der `dwReason`\-Parameter `ATTACH_REASON_LAUNCH`ist.  
  
 DE [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) muss die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Methode für das Objekt aufrufen, das vom [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)\-Ereignisobjekt angegeben ist, und muss die GUID des Programms dem Speichern in die Instanzdaten für das Objekt, auf das von `IDebugProgram2` DE implementiert wird.  
  
## Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)