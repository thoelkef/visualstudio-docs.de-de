---
title: IDebugEngine2::DestroyProgram | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 066a8a3cf9fb4f9c39d36cfa4ea386e06cbba831
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Ein Debugging-Modul (DE), die angegebene Programm ungewöhnlich beendet wurde und die DE sollten bereinigen Sie alle Verweise auf das Programm, informiert, und Senden eines Programms zerstört Ereignis.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProgram`  
 [in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das die Anwendung darstellt, die ungewöhnlich beendet wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Nachdem diese Methode aufgerufen wird, sendet der DE anschließend ein [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) Ereignis zurück an die Sitzung Debug-Manager (SDM).  
  
 Diese Methode ist nicht implementiert (gibt `E_NOTIMPL`) Wenn die DE in demselben Prozess wie das derzeit debuggte Programm ausgeführt wird. Nur wenn DE im selben Prozess wie die SDM ausgeführt wird, wird diese Methode implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)