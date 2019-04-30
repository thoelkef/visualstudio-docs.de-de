---
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 8f5eb2542fa16d86dd342ae0e2783ac03ca69ee4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920949"
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
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)