---
title: IEnumDebugCustomAttributes::Skip | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 372a32d83f0cebf69fd5e7795e083a272bbeb588
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679826"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
Überspringt eine angegebene Anzahl von benutzerdefinierten Attributen in einer Enumerationsfolge.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Skip ( 
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

#### <a name="parameters"></a>Parameter
 `celt`

 [in] Die Anzahl der zu überspringenden Elemente.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn `celt` größer als die Anzahl der verbleibenden Elemente ist; andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn `celt` gibt einen Wert größer als die Anzahl der verbleibenden Elemente am Ende die Enumeration festgelegt ist und `S_FALSE` zurückgegeben wird.

## <a name="see-also"></a>Siehe auch
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)