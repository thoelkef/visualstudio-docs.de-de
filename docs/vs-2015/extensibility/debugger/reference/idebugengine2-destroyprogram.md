---
title: IDebugEngine2::D estroyprogram | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9faacd80b036282a088b006a15eb9500e8606c5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196025"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Informiert eine Debug-Engine (de) darüber, dass das angegebene Programm atypisch beendet wurde und dass die de alle Verweise auf das Programm bereinigen und ein Programm zerstörungsereignis senden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProgram`  
 in Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, das atypisch beendet wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Nachdem diese Methode aufgerufen wurde, sendet der de-Vorgang ein [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) -Ereignis zurück an den Sitzungs-Debug-Manager (SDM).  
  
 Diese Methode ist nicht implementiert (gibt zurück `E_NOTIMPL` ), wenn die de in demselben Prozess wie das debuggerprogramm ausgeführt wird. Diese Methode wird nur implementiert, wenn die de in demselben Prozess wie die SDM ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
