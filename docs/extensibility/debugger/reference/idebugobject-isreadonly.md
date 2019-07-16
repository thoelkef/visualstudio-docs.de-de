---
title: IDebugObject::IsReadOnly | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21c8a21f3cc85247f1cef4131768984f99fff764
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349955"
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

## <a name="parameters"></a>Parameter
`pfIsReadOnly`\
[out] Ungleich NULL zurück (`TRUE`) Wenn dieses Objekt schreibgeschützt ist; andernfalls ist, gibt NULL zurück (`FALSE`).

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein schreibgeschütztes Objekt kann nicht haben, dessen Wert sich ändert, nachdem es erstellt wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)