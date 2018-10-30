---
title: IDebugPortEvents2::Event | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9254a17f0c88efa167019a1d05aa9524f9327ab1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856822"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode sendet die Ereignisse, die die Erstellung und Zerstörung von Prozessen und Programme auf einem Port angeben.  
  
## <a name="syntax"></a>Syntax  
  
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
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pMachine`  
 [in] Ein [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Objekt, das der debugserver darstellt (es gibt ein für jede Instanz des [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]) in der das Ereignis aufgetreten ist.  
  
 `pPort`  
 [in] Ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Objekt, das den Port darstellt, in dem das Ereignis aufgetreten ist.  
  
 `pProcess`  
 [in] Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den Prozess darstellt, in dem das Ereignis aufgetreten ist.  
  
 `pProgram`  
 [in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm darstellt, in dem das Ereignis aufgetreten ist.  
  
 `pEvent`  
 [in] Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Objekt, das das Ereignis identifiziert. Die möglichen Ereignisse sind wie folgt aus:  
  
- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
  `riidEvent`  
  [in] Die GUID des Ereignisses. Da das Ereignis umgewandelt wird [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) vor dem Aufrufen dieser Methode diese Bezeichner macht es erheblich einfacher ermitteln, welches Ereignis gesendet wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)

