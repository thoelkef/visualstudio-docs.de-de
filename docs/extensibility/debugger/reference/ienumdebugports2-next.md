---
title: IEnumDebugPorts2::Next | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5fb4d5574976b99185c4affd934d4a86fdcab72
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691279"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
Gibt den nächsten Satz von Elementen aus der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugPort2** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugPort2[] rgelt,
   ref uint      pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 `celt`

 [in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe der `rgelt` Array.

 `rgelt`

 [in, out] Array von [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Elementen gefüllt werden soll.

 `pceltFetched`

 [out] Gibt die Anzahl der im tatsächlich zurückgegebenen Elemente `rgelt`.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden können; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)