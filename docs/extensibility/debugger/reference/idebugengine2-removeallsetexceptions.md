---
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e28eb35d1d6172f693cc2be0e17aa3cd25050373
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986292"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Entfernt die Liste der Ausnahmen, die die IDE für eine bestimmte Laufzeit-Architektur oder Sprache festgelegt hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidType`  
 [in] Die GUID für die Sprache oder die GUID für die Debug-Engine, die spezifisch für eine Laufzeit-Architektur ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Ausnahmen von dieser Methode entfernt wurden festgelegt, durch frühere Aufrufe der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) Methode.  
  
 Rufen Sie zum Entfernen einer bestimmten Ausnahme die [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)