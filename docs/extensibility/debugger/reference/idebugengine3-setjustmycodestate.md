---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fda672cc9d6861520b9da3a894b94d51f4100683
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Diese Methode weist die Debugging-Modul zu den JustMyCode-Status-Informationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fUpdate`  
 [in] Ungleich Null (`TRUE`) um aktuelle Informationen zu aktualisieren, NULL (`FALSE`) alle Informationen (ignorieren alle zuvor festgelegten) zurücksetzen.  
  
 `dwModules`  
 [in] Anzahl der Informationsstrukturen in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Array von [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Strukturen zu verwenden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 JustMyCode ist das Konzept des Debuggen von Code, der ein Benutzer angehört, und wird ignoriert, alle temporären Code z. B. Systemcode – selbst wenn der Quellcode für diesen Systemcode verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)