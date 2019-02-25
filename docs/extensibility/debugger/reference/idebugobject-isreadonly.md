---
title: IDebugObject::IsReadOnly | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bef21a491a175e7f1a7f93cd7c8d9d70a5ec6279
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682621"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Bestimmt, ob dieses Objekt schreibgeschützt ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

#### <a name="parameters"></a>Parameter
 `pfIsReadOnly`

 [out] Ungleich NULL zurück (`TRUE`) Wenn dieses Objekt schreibgeschützt ist; andernfalls ist, gibt NULL zurück (`FALSE`).

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein schreibgeschütztes Objekt kann nicht haben, dessen Wert sich ändert, nachdem es erstellt wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)