---
title: IDebugObject::IsNullReference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fb6b5c0692ec43feec0cf4de48d9ce730b0032e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323516"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Testet, ob dieses Objekt ein null-Verweis ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parameter
`pfIsNull`\
[out] Ungleich NULL zurück (`TRUE`) Wenn dieses Objekt ein null-Verweis; andernfalls wird NULL (`FALSE`).

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein null-Verweis bedeutet, dass ein leeres Objekt oder ein Objekt, das nicht zugewiesen wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)