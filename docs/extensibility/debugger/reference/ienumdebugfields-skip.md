---
title: IEnumDebugFields::Skip | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Skip
helpviewer_keywords:
- IEnumDebugFields::Skip method
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a56dc0e07750a30644ccae54803172123c7753fd
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66208030"
---
# <a name="ienumdebugfieldsskip"></a>IEnumDebugFields::Skip
Diese Methode überspringt die angegebene Anzahl von Elementen ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der zu überspringenden Elemente.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn `celt` größer als die Anzahl der verbleibenden Elemente ist; andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn `celt` gibt einen Wert größer als die Anzahl der verbleibenden Elemente am Ende die Enumeration festgelegt ist und `S_FALSE` zurückgegeben wird.

## <a name="see-also"></a>Siehe auch
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)