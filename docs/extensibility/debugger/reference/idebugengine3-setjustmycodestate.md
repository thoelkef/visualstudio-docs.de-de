---
title: IDebugEngine3::SetJustMyCodeState | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: 9dafc7a98b511c9d7b8367e96621faee9e2cbc22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914422"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Diese Methode teilt die Debug-Engine zu den JustMyCode-Status-Informationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
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
 [in] Ungleich Null (`TRUE`) um aktuelle Informationen zu aktualisieren, NULL (`FALSE`) alle Informationen, die (wird ignoriert, alle zuvor festgelegten) zurücksetzen.  
  
 `dwModules`  
 [in] Anzahl der Informationsstrukturen in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Array von [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Strukturen verwenden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 JustMyCode ist das Konzept der nur den Code Debuggen, der zu einem Benutzer gehört, und wird ignoriert, alle temporären Code wie z. B. Systemcode – selbst wenn der Quellcode für diesen Systemcode verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)