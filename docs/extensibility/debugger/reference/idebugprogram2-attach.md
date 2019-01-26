---
title: IDebugProgram2::Attach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00a5f71a5283640f79079f4117471d0e5e3d42f6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025682"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Fügt an die Anwendung an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCallback`  
 [in] Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt, das für die Debug-ereignisbenachrichtigung verwendet werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt einige mögliche Fehlercodes.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Das angegebene Programm ist bereits an den Debugger angefügt.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Während dieses Vorgangs Anfügen ist ein Sicherheitsverstoß aufgetreten.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein Desktopprogramm kann nicht an den Debugger angefügt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode zum Anfügen an ein Programm wird von eine Debug-Engine (DE) nie aufgerufen. Wenn die DE im Adressraum des Programms ausgeführt wird. die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode wird aufgerufen. Wenn die DE-Ausführungen in der Sitzung Debug-Manager (SDM) Adressraum, den [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode wird aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)